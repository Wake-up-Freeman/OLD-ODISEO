# Market <img src="/img/Market.svg" height="40px">

The Market module enables swaps between ODISEO tokens, and between ODIS and ATOM. This module ensures an available, liquid market, stable prices, and fair exchange rates between the protocol's assets.

## Concepts

### Swap Fees

Because ODISEO's price feed is derived from validator oracles, a delay exists between the price reported on-chain and the real-time price.

The delay lasts around one minute (our oracle `VotePeriod` is 30 seconds), which is negligible for nearly all practical transactions. However, front-running attackers could take advantage of this delay and extract value from the network.

To defend against this type of attack, the Market module enforces the following swap fees:

- [**Tobin tax**](#tobintax) for spot-converting ODISEO<>ODISEO swaps

  We will work to eliminate Tobin tax.

[^1]: Initially, the ODISEO blockchain maintained a policy for zero-fee swaps. However, to prevent front-running attackers from exploiting the exchange-rate latency and profiting at the expense of users, the Tobin tax might be implemented if required.

- [**Minimum spread**](#minspread) for ODISEO<>ODIS swaps

  The minimum spread is 0.5%. 

### Market Making Algorithm

ODISEO will leverage Cosmos Ecosystem to start its first liquidity pool.

### Virtual Liquidity Pools

The market starts out with two liquidity pools of equal sizes, one representing pair ODIS and another representing total value of all GAIA NFTs. The parameter [`BasePool`](#basepool) defines the initial size, $Pool_{Base}$, of the ODISEO and ODIS liquidity pools.

Rather than keeping track of the sizes of the two pools, this information is encoded in a number $\delta$, which the blockchain stores as `ODISEOPoolDelta`. This represents the deviation of the ODISEO pool from its base size in units µGAIA Collections.

The size of the ODISEO and ODIS liquidity pools can be generated from $\delta$ using the following formulas:

$$Pool_{Terra} = Pool_{Base} + \delta$$
$$Pool_{ODIS} = ({Pool_{Base}})^2 / Pool_{ODISEO}$$

At the [end of each block](#end-block), the market module attempts to replenish the pools by decreasing the magnitude of $\delta$ between the ODISEO and ODIS pools. The rate at which the pools will be replenished toward equilibrium is set by the parameter [`PoolRecoveryPeriod`](#poolrecoveryperiod). Lower periods mean lower sensitivity to trades: previous trades are more quickly forgotten and the market is able to offer more liquidity.

This mechanism ensures liquidity and acts as a low-pass filter, allowing for the spread fee (which is a function of `ODISEOPoolDelta`) to drop back down when there is a change in demand, causing a necessary change in supply which needs to be absorbed.

### Swap Procedure

1. The Market module receives [`MsgSwap`](#msgswap) message and performs basic validation checks.

2. Calculate exchange rate $ask$ and $spread$ using [`k.ComputeSwap()`](#functions).

3. Update `ODISEOPoolDelta` with [`k.ApplySwapToPool()`](#k-applyswaptopool).

4. Transfer `OfferCoin` from account to module using `supply.SendCoinsFromAccountToModule()`.

5. Burn offered coins, with `supply.BurnCoins()`.

6. Let $fee = spread * ask$, this is the spread fee.

7. Mint $ask - fee$ coins of `AskDenom` with `supply.MintCoins()`. This implicitly applies the spread fee as the $fee$ coins are burned.

8. Send newly minted coins to trader with `supply.SendCoinsFromModuleToAccount()`.

9. Emit `swap` event to publicize the swap and record the spread fee.

If the trader's `Account` has insufficient balance to execute the swap, the swap transaction fails.

Upon successful completion of ODISEO<>ODIS swaps, a portion of the coins to be credited to the user's account is withheld as the spread fee.

### Seigniorage

::: {admonition} All seigniorage is Burned
:class: Caution

Seigniorage used to be an important part of the protocol, but is no longer necessary. As of Columbus-5, all seigniorage is burned, and the community pool is no longer funded. Swap fees are used instead of seigniorage as ballot rewards for the exchange rate oracle. The following information is kept as reference:
:::

When ODIS swaps into ODISEO, the ODIS recaptured by the protocol was called seigniorage -- the value generated from issuing new ODISEO. The total seigniorage at the end of each epoch was calculated and reintroduced into the economy as ballot rewards for the exchange rate oracle and to the community pool by the Treasury module, described more fully [here](spec-treasury.md). As of Columbus-5, all seigniorage is burned, and the community pool is no longer funded. Swap fees are used as ballot rewards for the exchange rate oracle.

## State

### ODISEO Pool Delta δ

- type: `sdk.Dec`

 This represents the difference between the current ODISEO pool size and its original base size, valued in µGAIA Collections.

## Message Types

### MsgSwap

A `MsgSwap` transaction denotes the `Trader`'s intent to swap their balance of `OfferCoin` for a new denomination `AskDenom`. ODISEO<>ODISEO swaps incur gas and the Tobin tax (if applicable), and ODISEO<>ODIS swaps incur gas and a spread fee.

```go
// MsgSwap contains a swap request
type MsgSwap struct {
	Trader    sdk.AccAddress `json:"trader" yaml:"trader"`         // Address of the trader
	OfferCoin sdk.Coin       `json:"offer_coin" yaml:"offer_coin"` // Coin being offered
	AskDenom  string         `json:"ask_denom" yaml:"ask_denom"`   // Denom of the coin to swap to
}
```

### MsgSwapSend

A `MsgSwapSend` first swaps `OfferCoin` for `AskDenom` and then sends the acquired coins to `ToAddress`. Swap fees are charged to the sender.

```go
type MsgSwapSend struct {
	FromAddress sdk.AccAddress `json:"from_address" yaml:"from_address"` // Address of the offer coin payer
	ToAddress   sdk.AccAddress `json:"to_address" yaml:"to_address"`     // Address of the recipient
	OfferCoin   sdk.Coin       `json:"offer_coin" yaml:"offer_coin"`     // Coin being offered
	AskDenom    string         `json:"ask_denom" yaml:"ask_denom"`       // Denom of the coin to swap to
}
```

## Functions

### `k.ComputeSwap()`

```go
func (k Keeper) ComputeSwap(ctx sdk.Context, offerCoin sdk.Coin, askDenom string)
    (retDecCoin sdk.DecCoin, spread sdk.Dec, err sdk.Error)
```

This function detects the swap type from the offer and ask denominations and returns:

1. The amount of asked coins that should be returned for a given `offerCoin`. This is achieved by first spot-converting `offerCoin` to µGAIA Collections and then from µGAIA Collections to the desired `askDenom` with the proper exchange rate reported by the Oracle.

2. The spread percentage that should be taken as a swap fee given the swap type. ODISEO<>ODISEO swaps only have the Tobin Tax spread fee. ODISEO<>ODIS swaps use the `MinSpread` or the Constant Product pricing spread, whichever is greater.

If the `offerCoin`'s denomination is the same as `askDenom`, this will raise `ErrRecursiveSwap`.

::: {note}
`k.ComputeSwap()` uses `k.ComputeInternalSwap()` internally, which only contains the logic for calculating proper ask coins to exchange, and not the Constant Product spread.
:::

### `k.ApplySwapToPool()`

```go
func (k Keeper) ApplySwapToPool(ctx sdk.Context, offerCoin sdk.Coin, askCoin sdk.DecCoin) sdk.Error
```

`k.ApplySwapToPools()` is called during the swap to update the blockchain's measure of $\delta$, `ODISEOPoolDelta`, when the balances of the ODISEO and ODIS liquidity pools have changed.

All ODISEO stablecoins share the same liquidity pool, so `ODISEOPoolDelta` remains unaltered during ODISEO<>ODISEO swaps.

For ODISEO<>ODIS swaps, the relative sizes of the pools will be different after the swap, and $\delta$ will be updated with the following formulas:

- for ODISEO to ODIS, $\delta' = \delta + Offer_{\mu GAIA Collections}$
- for ODIS to ODISEO, $\delta' = \delta - Ask_{\mu GAIA Collections}$

## Transitions

### End-Block

The Market module calls `k.ReplenishPools()` at the end of every block, which decreases the value of `ODISEOPoolDelta` (the difference between ODISEO and ODIS pools) depending on `PoolRecoveryPeriod`, $pr$.

This allows the network to sharply increase spread fees during acute price fluctuations. After some time, the spread automatically returns to normal for long term price changes.

## Parameters

The subspace for the Market module is `market`.

```go
type Params struct {
	PoolRecoveryPeriod int64   `json:"pool_recovery_period" yaml:"pool_recovery_period"`
	BasePool           sdk.Dec `json:"base_pool" yaml:"base_pool"`
	MinSpread          sdk.Dec `json:"min_spread" yaml:"min_spread"`
	TobinTax           sdk.Dec `json:"tobin_tax" yaml:"tobin_tax"`
}
```

### PoolRecoveryPeriod

- type: `int64`
- default: `BlocksPerDay`

The number of blocks it takes for the ODISEO & ODIS pools to naturally "reset" toward equilibrium ($\delta \to 0$) through automated pool replenishing.

### BasePool

- type: `Dec`
- default: 250,000 GAIA Collections (= 250,000,000,000 µGAIA Collections)

The initial starting size of both ODISEO and ODIS liquidity pools.

### MinSpread

- type: `Dec`
- default: 0.5%

The minimum spread charged on ODISEO<>ODIS swaps to prevent leaking value from front-running attacks.

### TobinTax

- type: `Dec`
- default: 0.35%

An additional fee for swapping between ODISEO currencies (spot-trading). The rate varies, depending on the denomination. For example, while the rate for most denominations is .35%, the rate for MNT is 2%. To see the rates, [query the oracle](https://lcd.ODISEO.dev/ODISEO/oracle/v1beta1/denoms/tobin_taxes).
