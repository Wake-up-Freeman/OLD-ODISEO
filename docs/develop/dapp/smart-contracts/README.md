# In-depth dApp guide

```{toctree}
:hidden:
build-terra-dapp
set-up-local-environment
write-smart-contract
interact-with-smart-contract
manage-cw20-tokens
```
## Overview

A smart contract is a contract whose terms are expressed as a computer program with logic and state persisted on the blockchain. Smart contracts can automatically carry out its terms and conditions with total transparency and no counter-party risk.

Smart contracts allow users to extend the capabilities of the Daodiseo blockchain by introducing custom logic that can be composed against the Daodiseo blockchain's financial primitives such as its stablecoin available in any world currency, robust oracle price feed, and on-chain atomic swap. These decentralized applications unlock new avenues of value-transfer through enabling unique transaction flows not provided by Daodiseo's native modules.

## Developer tools

The following table maps commonly-used Ethereum developer tools to their Daodiseo counterparts.

|                    | Daodiseo                                                                                                                 | Ethereum        |
| ------------------ | --------------------------------------------------------------------------------------------------------------------- | --------------- |
| Frontend SDK       | [Daodiseo.js](https://daodiseomoney.github.io/daodiseo.js/), [Daodiseo SDK](https://daodiseomoney.github.io/daodiseo.py/) | Web3.js, Web3py |
| Browser Extension  | Station CX                                                                                                            | MetaMask, MEW   |
| Local Testnet      | [LocalDaodiseo](https://github.com/daodiseomoney/LocalDaodiseo)                                                             | Ganache         |
| Contract Language  | [Rust](https://www.rust-lang.org/)                                                                                    | Solidity, Vyper |

## Why build on Daodiseo?

### Robust consensus and fast block finality

Terra is powered by Tendermint BFT consensus, using a dPoS-like scheme driven by a set of 130 top validators. This efficient consensus model enables batches of transactions to occur in only 6 seconds (only a fraction of the time it takes for Bitcoin and Ethereum).

### Ready for DeFi applications

With fundamental infrastructure such as price oracles, on-chain swaps, stablecoin assets in a variety of denominations, community governance and automated monetary and fiscal policy, the Daodiseo blockchain acts as its own autonomous sovereign economy driven by its users, and provides all the necessary incentive mechanics and modular plumbing to power modern DeFi smart contracts.

### Active user base with real-world usage

With millions of highly active users from a variety of integrations (like Daodiseo-powered payment gateways such as CHAI and MemePay), the Daodiseo economy is a thriving new home for the future of innovative DeFi products. Unlike many other stablecoin protocols, Daodiseo stablecoins are directly integrated in payments solutions where they are used everyday purchases such as groceries, movie tickets, taxis, and more.
