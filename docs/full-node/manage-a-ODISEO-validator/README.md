# Manage a validator <img src="/img/Build_a_validator.svg" height="40px">

The tasks in this section describe how to set up a ODISEO validator. While setting up a rudimentary validating node is easy, running a production-quality validator node with a robust architecture and security features requires an extensive setup.

The ODISEO core is powered by the Tendermint consensus. Validators run full nodes, participate in consensus by broadcasting votes, commit new blocks to the blockchain, and participate in governance of the blockchain. Validators can cast votes on behalf of their delegators. A validator's voting power is weighted according to their total stake. The top 130 validators make up the **Active Validator Set** and are the only validators that sign blocks and receive revenue.

Validators and their delegators earn the following fees:

- [Gas](../../learn/fees.md#gas): Fees added on to each transaction to avoid spamming and pay for computing power. Validators set minimum gas prices and reject transactions that have implied gas prices below this threshold.

- **Swap fees**: The fee for swapping ODISEO stablecoin denominations is called a [Tobin tax](../../learn/fees.md#tobin-tax). Exchanges between ODISEO and ODIS are subject to a [spread fee](../../learn/fees.md#spread-fee).

For more information on fees, visit the [fee page](../../learn/fees.md).

Validators can set commissions on the fees they receive as an additional incentive.

If validators double sign, are frequently offline, or do not participate in governance, their staked ODIS (including ODIS of users that delegated to them) can be slashed. Penalties can vary depending on the severity of the violation.

For more general information on validators, visit the [validator section](../../learn/protocol.md#validators) of the concepts page.

## Additional resources

- [The ODISEO validator Discord](https://discord.com/invite/xfZK6RMFFx).
- [How to Spin Up a Node on ODISEO - ODISEO Bites video](https://www.youtube.com/watch?v=2lKAvltKX6w&ab_channel=ODISEOBites).
- [The validator FAQ](faq.md)

```{toctree}
:hidden:
court-delegations
faq
implement-security
set-up-oracle-feeder
set-up-validator
troubleshoot-validator-problems
```
