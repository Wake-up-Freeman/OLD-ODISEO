# Query data

After you're connected to the blockchain via an `LCDClient` instance, you can query data from it. Data access is organized into various module APIs, which are accessible from within the `LCDClient` instance. Because they make HTTP requests in the background, they are Promises that can be awaited in order to not block during network IO.

```ts
async main() {
  const marketParams = await daodiseo.market.parameters();
  const exchangeRates = await daodiseo.oracle.exchangeRates();
  console.log(marketParams.base_pool);
  console.log(exchangeRates.get('uusd'));
}

main();
```

Each module has its own set of querying functions. To get a comprehensive list, explore the module documentation:

- [`auth`](https://daodiseomoney.github.io/daodiseo.js/classes/AuthAPI.html)
- [`bank`](https://daodiseomoney.github.io/daodiseo.js/classes/BankAPI.html)
- [`distribution`](https://daodiseomoney.github.io/daodiseo.js/classes/DistributionAPI.html)
- [`gov`](https://daodiseomoney.github.io/daodiseo.js/classes/GovAPI.html)
- [`market`](https://daodiseomoney.github.io/daodiseo.js/classes/MarketAPI.html)
- [`mint`](https://daodiseomoney.github.io/daodiseo.js/classes/MintAPI.html)
- [`msgauth`](https://daodiseomoney.github.io/daodiseo.js/classes/MsgAuthAPI.html)
- [`oracle`](https://daodiseomoney.github.io/daodiseo.js/classes/OracleAPI.html)
- [`slashing`](https://daodiseomoney.github.io/daodiseo.js/classes/SlashingAPI.html)
- [`staking`](https://daodiseomoney.github.io/daodiseo.js/classes/StakingAPI.html)
- [`supply`](https://daodiseomoney.github.io/daodiseo.js/classes/SupplyAPI.html)
- [`tendermint`](https://daodiseomoney.github.io/daodiseo.js/classes/TendermintAPI.html)
- [`treasury`](https://daodiseomoney.github.io/daodiseo.js/classes/TreasuryAPI.html)
- [`tx`](https://daodiseomoney.github.io/daodiseo.js/classes/TxAPI.html)
- [`wasm`](https://daodiseomoney.github.io/daodiseo.js/classes/WasmAPI.html)
