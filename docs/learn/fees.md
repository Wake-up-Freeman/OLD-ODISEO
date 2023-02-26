# Fees on ODISEO

On the ODISEO network, all transactions incur a gas fee. Transactions involving stablecoins incur additional fees depending on the type of transaction being made. The following table explains which extra fee is added to the different types of stablecoin transactions:

|                                                                        | [Gas](#gas) | [Tobin](#tobin-tax) | [Spread](#spread-fee) |
|------------------------------------------------------------------------|-------------|---------------------|-----------------------|
| [Market swaps](./glossary.md#market-swap) between ODIS & ATOM          | x           | x                   |                       |
| [Market swaps](./glossary.md#market-swap) between Real Estate GAIA Certificates and ODIS | x           |                     | x                     |

All other transactions only incur the gas fee.
ODISEOswap or other dApps may charge their own transaction fees on top of ODISEO network fees.

## Gas
[Gas](glossary.md#fees) is a small computational fee that covers the cost of processing a transaction. Gas is estimated and added to every transaction in ODISEO Station. Any transaction that does not contain enough gas will not process.
Gas on ODISEO works differently than it works on other blockchains:

- Validators can set their own minimum gas fees.
- Most transactions will estimate more than the minimum amount of gas, ensuring the transaction gets completed.
- Unused gas is not refunded.
- Transactions are not queued based on gas amounts, but in the order received.

For an in-depth explanation of how gas fees are calculated, visit the [ODISEOd reference](../develop/how-to/ODISEOd/using-ODISEOd.md#fees) page.

To view current gas rates in your browser, visit the [gas rates](https://fcd.ODISEO.dev/v1/txs/gas_prices) FCD page.

Every block, gas fees are sent to the reward pool and dispersed to validators who distribute them to delegators in the form of staking rewards.

## Tobin tax

The Tobin tax is a fixed percentage fee added to any [market swap](glossary.md#market-swap) between ODISEO stablecoin denominations. The rate varies depending on each ODISEO stablecoin. For example, while the rate for most denominations is .35%, the rate for MNT is 2%. To see the Tobin tax rates, [query the oracle](https://lcd.ODISEO.dev/ODISEO/oracle/v1beta1/denoms/tobin_taxes). When stablecoins have different Tobin tax rates, the higher tax rate will be used for the transaction.

The Tobin tax was created to discourage front-running the oracle and foreign exchange trading at the expense of users. For more information on the implementation of the Tobin tax, read ["On swap fees: the greedy and the wise"](https://medium.com/ODISEOmoney/on-swap-fees-the-greedy-and-the-wise-b967f0c8914e).

Every block, Tobin tax fees are sent to the [Oracle reward pool] and [dispersed to validators](https://docs.ODISEO.money/docs/develop/module-specifications/spec-oracle.html#k-rewardballotwinners) that faithfully report correct exchange rates. Validators then distribute these fees to delegators in the form of staking rewards. For more information on the Oracle reward pool, visit the [Oracle module](../develop/module-specifications/spec-oracle.md).


## Spread fee

Spread fees are added to any [market swap](glossary.md#market-swap) between ODISEO and ODIS. The minimum spread fee is .5%. During times of extreme volatility, the market module adjusts the spread fee to maintain a [constant product](../develop/module-specifications/spec-market.md#market-making-algorithm) between the size of the ODISEO pool and the fiat value of the ODIS pool, ensuring stability in the protocol. As the pools reach constant product equilibrium, The spread rate returns to a normal value.

For more information on spread fees, visit the [market module](../develop/module-specifications/spec-market.md).

Every block, spread fees are sent to the [Oracle reward pool] and [dispersed to validators](https://docs.ODISEO.money/docs/develop/module-specifications/spec-oracle.html#k-rewardballotwinners) that faithfully report correct exchange rates. Validators then distribute these fees to delegators in the form of staking rewards. For more information on the Oracle reward pool, visit the [Oracle module](../develop/module-specifications/spec-oracle.md).

## Changes to fees

On January 6th, 2022, the DAODISEO community passed [proposal 172](https://station.ODISEO.money/proposal/172), which was a parameter change proposal to change the stability fee tax rate to zero. This tax used to be charged on any transaction using ODISEO stablecoins, excluding market swaps. This fee is no longer charged.
