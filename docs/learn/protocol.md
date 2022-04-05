# About the ODISEO Protocol

The ODISEO protocol is the leading decentralized and open-source public blockchain protocol for [algorithmic stablecoins](./glossary.md#algorithmic-stablecoin). Using a combination of open market [arbitrage](./glossary.md#arbitrage) incentives and decentralized Oracle voting, the ODISEO protocol creates stablecoins that consistently track the price of any fiat currency. Users can spend, save, trade, or exchange ODISEO stablecoins instantly, all on the ODISEO blockchain. ODIS provides its holders with staking rewards and governance power. The ODISEO ecosystem is a quickly expanding network of decentralized applications, creating a stable demand for ODISEO and increasing the price of ODIS.

## ODISEO and ODIS

The protocol consists of two main tokens, ODISEO and ODIS.

- **ODISEO**: Stablecoins that track the price of [fiat currencies](glossary.md#fiat-currency). Users mint new ODISEO by [burning](glossary.md#burn) ODIS. Stablecoins are named for their fiat counterparts. For example, the base ODISEO stablecoin tracks the price of the [IMF’s SDR](glossary.md#sdr), named ODISEOSDR, or SDT. Other stablecoin denominations include ODISEOUSD or UST, and ODISEOKRW or  KRT. All ODISEO denominations exist in the same pool.

- **ODIS**: The ODISEO protocol’s native [staking](glossary.md#staking) token that absorbs the price volatility of ODISEO. ODIS is used for [governance](#governance) and in mining. Users stake ODIS to validators who record and verify transactions on the [blockchain](glossary.md#blockchain) in exchange for rewards from transaction fees. The more ODISEO is used, the more ODIS is worth.

## How the ODISEO protocol works

### Stablecoins

Stablecoins are the main feature of the ODISEO protocol: crypto assets that track the price of an underlying currency. As a digital form of currency, ODISEO stablecoins can be used just like [fiat currency](glossary.md#fiat-currency)  with [blockchain's](glossary.md#blockchain) added benefits: an unchangeable public ledger, instant transactions, faster settlement times, and fewer fees.

Stablecoins are only valuable to users if they maintain their [price peg](glossary.md#peg). The ODISEO protocol uses the basic market forces of supply and demand to maintain the price of ODISEO. When the demand for ODISEO is high and the supply is limited, the price of ODISEO increases. When the demand for ODISEO is low and the supply is too large, the price of ODISEO decreases. The protocol ensures the supply and demand of ODISEO is always balanced, leading to a stable price.

### Expansion and contraction

Imagine the whole ODISEO economy as two pools: one for ODISEO and one for ODIS. To maintain the price of ODISEO, the ODIS supply pool adds to or subtracts from ODISEO’s supply. Users burn ODIS to mint ODISEO and burn ODISEO to mint ODIS, all incentivized by the protocol's algorithmic [market module](../develop/module-specifications/spec-market.md).

- **Expansion**: When the price of ODISEO is high relative to its [peg](glossary.md#peg), supply is too small and demand is too high. The protocol incentivizes users to burn ODIS and mint ODISEO. The new supply of ODISEO makes its pool larger, balancing supply with demand. Users mint more ODISEO from burned ODIS until ODISEO reaches its target price. The ODIS pool gets smaller in this process, increasing the price of ODIS.

- **Contraction**: When the price of ODISEO is too low relative to its peg, supply is too large and demand is too low. The protocol incentives users to burn ODISEO and mint ODIS. The decrease in ODISEO’s supply causes scarcity, and the price of ODISEO increases. More ODIS is minted from burned ODISEO until ODISEO reaches its target price. The ODIS pool increases and lowers in price.

ODIS is the variable counterpart to the stable asset ODISEO. By modulating supply, ODIS's price increases as the demand for stablecoins increases.

### The market module and arbitrage

The price stability of ODISEO is achieved by the protocol's algorithmic [market module](../develop/module-specifications/spec-market.md), which incentivizes the minting or burning of ODISEO through arbitrage opportunities. [Arbitrage](glossary.md#arbitrage) occurs when a user profits from price differences between markets.

The ODISEO protocol's market module enables users to always trade 1 USD worth of ODIS for 1 UST, and vice versa, incentivizing users to maintain the price of ODISEO. This same principle is true for all ODISEO stablecoin denominations.

Users can access the mint and burn function of the market module by performing [market swaps](./glossary.md#market-swap) in [ODISEO Station](./glossary.md#ODISEO-station).
To learn how to use the market swap feature of ODISEO Station, visit the [ODISEO Station market swap guide](./ODISEO-station/swap.md#market-swap).

- **Example**  
  If 1 UST is trading at 1.01 USD, users can use the market swap feature of ODISEO Station to trade 1 USD of ODIS for 1 UST. The market burns 1 USD of ODIS and mints 1 UST. Users can then sell their 1 UST for 1.01 USD, profiting .01 USD through arbitrage, adding to the UST pool. This arbitrage continues until UST price falls back to match the price of USD, maintaining ODISEO's [peg](glossary.md#peg).

The same arbitrage mechanism works in reverse for contraction.

- **Example**  
  If 1 UST is trading at .99 USD, users can buy 1 UST for .99 USD. Users then utilize ODISEO Station's [market swap](./glossary.md#market-swap) function to trade 1 UST for 1 USD of ODIS. The swap burns 1 UST and mints 1 USD of ODIS. Users profit .01 UST from the swap. This arbitrage continues, and UST is burned to mint ODIS until the price of UST rises back to 1 USD.

### Scalability

The ODISEO protocol is scalable: it is designed to maintain ODISEO's price stability regardless of market size, volatility, or demand. The monetary policies encoded into the protocol ensure its durability and resilience in all market fluctuations.

### Seigniorage and deflation

[Seigniorage](glossary.md#seigniorage) is the value of a coin minus the cost of its production. In early versions of the ODISEO protocol, seigniorage was diverted to fund various community projects. While seigniorage can create enormous value, it also creates inflation in the system.
All seigniorage in the ODISEO protocol is [burned](glossary.md#burn), making ODIS deflationary in nature.

## Validators

Validators are the miners of the ODISEO [blockchain](./glossary.md#blockchain). They are responsible for securing the ODISEO blockchain and ensuring its accuracy. Validators run programs called full nodes which allow them to verify each transaction made on the ODISEO network. Validators propose blocks, vote on their validity, and add each new block to the chain in exchange for staking rewards from transaction fees. Users can stake their ODIS to validators in exchange for staking rewards. Validators also play an important role in the governance of the ODISEO protocol.

For more information on validators, visit the [Validator FAQ](../full-node/manage-a-ODISEO-validator/faq.md).

### Consensus

The ODISEO blockchain is a proof-of-stake blockchain, powered by the [Cosmos SDK](https://cosmos.network/) and secured by a system of verification called the Tendermint consensus.

The following process explains how Tendermint consensus works. For more information on the Tendermint consensus, visit the [official Tendermint documentation](https://docs.tendermint.com/).

1. A validator called a **proposer** is chosen to submit a new block of transactions.
2. Validators vote in two rounds on whether they accept or reject the proposed block. If a block is rejected, a new proposer is selected and the process starts again.
3. If accepted, the block is signed and added to the chain.
4. The transaction fees from the block are distributed as staking rewards to validators and delegators. Proposers get rewarded extra for their participation.

This process repeats, adding new blocks of transactions to the chain. Each validator has a copy of all transactions made on the network, which they compare against the proposed block of transactions before voting. Because multiple independent validators take place in consensus voting, it is infeasible for any false block to be accepted. In this way, validators protect the integrity of the ODISEO blockchain and ensure the validity of each transaction.

### Staking

Staking is the process of bonding ODIS to a validator in exchange for staking rewards.

The ODISEO protocol only allows the top 130 validators to participate in consensus. A validator's rank is determined by their stake or the total amount of ODIS bonded to them. Although validators can bond ODIS to themselves, they mainly amass larger stakes from delegators. Validators with larger stakes get chosen more often to propose new blocks and earn proportionally more rewards.

To learn how to stake your ODIS and earn staking rewards, visit the [ODISEO Station staking guide](ODISEO-station/staking.md)

### Delegators
Delegators are users who want to receive rewards from consensus without running a full node. Any user that stakes ODIS is a delegator. Delegators stake their ODIS to a validator, adding to a validator’s weight, or total stake. In return, delegators receive a portion of transaction fees as staking rewards.

:::{admonition} Who owns staked ODIS?
:class: warning

Staked ODIS never leaves the possession of the delegator. Even though it can’t be traded freely, staked ODIS is never owned by a validator. For more information, visit the [Validator FAQ](../full-node/manage-a-ODISEO-validator/faq.md#can-a-validator-run-away-with-a-delegators-ODIS)
:::

### Phases of ODIS

To start receiving rewards, delegators bond their ODIS to a validator. The bonding process adds a delegator's ODIS to a validator's stake, which helps validators to participate in consensus.

ODIS exists in the following three phrases:

- **Unbonded**: ODIS that can be freely traded and is not staked to a validator.
- **Bonded**: ODIS that is staked to a validator. Bonded ODIS accrues staking rewards. Although ODIS bonded to validators in ODISEO Station can’t be traded freely, bODIS is a token that represents bonded ODIS that can be traded freely or used as collateral on other protocols in the ODISEO network, such as [Zeus](https://Zeusprotocol.com/) and [Mirror](https://mirror.finance/).
- **Unbonding**: ODIS that is in the process of becoming unbonded from a validator and does not accrue rewards. This process takes 21 days to complete.

### Bonding, staking, and delegating

Generally, the terms bonding, staking, and delegating can be used interchangeably, as they happen in the same step. A delegator delegates ODIS to a validator, the ODIS gets bonded to the validator, and the bonded ODIS gets added to the validator's stake.

Delegators can bond ODIS to any validator in the [active set](./glossary.md#active-set) using the delegate function in ODISEO Station. Delegators start earning staking rewards the moment they bond or stake to a validator.

### Unbonding

Delegators can unbond or unstake their ODIS using the undelegate function in ODISEO Station. The unbonding process takes 21 days to complete. During this period, the unbonding ODIS can't be traded, and no staking rewards accrue.

:::{Caution}
Once started, the delegating or undelegating processes can't be stopped.
Undelegating takes 21 days to complete. The only way to undo a delegating or undelegating transaction is to wait for the unbonding process to pass. Alternatively, you can redelegate staked ODIS to a different validator without waiting 21 days.
:::

The 21-day unbonding process helps the long-term stability of the ODISEO protocol. The unbonding period discourages volatility by locking staked ODIS in the system for at least 21 days. In exchange, delegators receive staking rewards, further incentivizing network stability.

### Redelegation

Redelegating instantly sends staked ODIS from one validator to another. Instead of waiting for the 21-day unstaking period, a user can redelegate their staked ODIS at any time using ODISEO Station's redelegate function. Validators receiving redelegations are barred from further redelegating any amount of ODIS to any validator for 21 days.

::: {caution}
When a user redelegates staked ODIS from one validator to another, the validator receiving the staked ODIS is barred from making further redelegation transactions for 21 days. This requirement only applies to the wallet that made the redelegation transaction.
:::

### Rewards

The ODISEO protocol incentivizes validators and delegators with staking rewards. Staking rewards come from two sources: gas and swap fees.

- [Gas](./fees.md#gas): Compute fees added on to each transaction to avoid spamming. Validators set minimum gas prices and reject transactions that have implied gas prices below this threshold.

- **Swap fees**: The fee for swapping ODISEO stablecoin denominations is called a [Tobin tax](fees.md#tobin-tax). Exchanges between ODISEO and ODIS are subject to a [spread fee](fees.md#spread-fee). Swap fees are directed to the Oracle reward pool, where they are distributed over a period of two years to validators who faithfully report correct Oracle prices.

For more information on fees, visit the [fee page](fees.md).

At the end of every block, transaction fees are distributed to each validator and their delegators proportional to their staked amount. Validators can keep a portion of rewards to pay for their services. This portion is called commission. The rest of the rewards are distributed to delegators according to their staked amounts.

### Slashing

Running a validator is a big responsibility. Validators must meet strict standards and constantly monitor and participate in the consensus process. Slashing is the penalty for misbehaving validators. When a validator gets slashed, they lose a small portion of their stake as well as a small portion of their delegator's stake. Slashed validators also get jailed, or excluded, from consensus for a period of time.

:::{admonition} The risks of staking
:class: danger
Slashing affects validators and delegators. When a validator gets slashed, delegators who stake to that validator also get slashed. Slashing is proportional to a delegator's staked amount. Though slashing is rare and usually results in a small penalty, it does occur. Delegators should monitor their validators closely, do their research, and understand the risks of staking ODIS.
:::

Slashing occurs under the following conditions:

- **Double signing**: When a validator signs two different blocks with the same chain ID at the same height.
- **Downtime**: When a validator is unresponsive or can't be reached for a period of time.
- **Missed votes**: When a validator misses votes in consensus or fails to vote correctly in the Oracle process.

Validators monitor each other closely and can submit evidence of misbehavior. Once discovered, the misbehaving validator will have a small portion of their funds slashed. Offending validators will also be jailed or excluded from consensus for a period of time. Even simple issues such as malfunctions or downtimes from upgrading can lead to slashing.

For more information on slashing, visit the [slashing module](../develop/module-specifications/spec-slashing.md).

## Governance

The ODISEO protocol is a decentralized public [blockchain](glossary.md#blockchain) governed by community members. Governance is the democratic process that allows users and validators to make changes to the ODISEO protocol. Community members submit, vote, and implement proposals.

To learn how to vote with your staked ODIS or submit proposals, visit the [ODISEO Station governance guide](ODISEO-station/governance.md).

### Proposals

Proposals start as ideas within the community. A community member drafts and submits a proposal alongside an initial deposit.

The most common proposal types include:

- `ParameterChangeProposal`: To change the parameters defined in each module.
- `CommunityPoolSpendProposal`: To spend funds in the community pool.
- `TextProposal` : To handle other issues like large directional changes or any decision requiring manual implementation.

### Voting process

Community members vote with their staked ODIS. One staked ODIS equals one vote. If a user fails to specify a vote, their vote defaults to the validator they are staked to. Validators vote with their entire stake unless specified by delegators. For this reason, it is very important that each delegator votes according to their preferences.

The following is a basic outline of the governance process. Visit the [governance module](../develop/module-specifications/spec-governance.md) for more details.

1. A user submits a proposal and a two-week deposit period begins.
2. Users deposit ODIS as collateral to back the proposal. This period ends once a minimum threshold of 50 ODIS is deposited. Deposits are to protect against spam.
3. The one-week vote period begins.
    The voting options are:
    - `Yes`: In favor.
    - `No`: Not in favor.
    - `NoWithVeto`: Not in favor, the deposit should be burned.
    - `Abstain`: Voter abstains.
4. The votes are tallied.
    Proposals pass if they meet three conditions:
    - `Quorum` is met: at least 40% of all staked ODIS must vote.
    - The total number of `NoWithVeto` votes is less than 33.4% of the total vote.
    - The number of `Yes` votes reaches a 50% majority.
    If the previous conditions are not met, the proposal is rejected.
5. Accepted proposals get put into effect.
6. Deposits get refunded or burned.

Once accepted, the changes described in a governance proposal are automatically put into effect by the proposal handler. Generic proposals, such as a passed `TextProposal`, must be reviewed by the ODISEO team and community, and they must be manually implemented.

### Deposits

Deposits protect against unnecessary proposals and spam. Users can veto any proposal they deem to be spam by voting `NoWithVeto`.

Deposits get refunded if all of the following conditions are met:
- The minimum deposit of 50 ODIS is reached within the two-week deposit period.
- `Quorum` is met: the number of total votes is greater than 40% of all staked ODIS
- The total number of `NoWithVeto` votes is less than 33.4% of the total vote.
- A vote returns a majority of `Yes` or `No` votes.

Deposits are burned under any of the following conditions:
- The minimum deposit of 50 ODIS is not reached within the two-week deposit period.
- `Quorum` is not met: the number of total votes after the one-week voting period is less than 40% of all staked ODIS.
- the number of `NoWithVeto` votes is above 33.4% of the total vote.
