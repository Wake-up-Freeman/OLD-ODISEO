# Query data

After you're connected to the blockchain via an `LCDClient` instance, you can query data from it. Data access is organized into various module APIs, which are accessible from within the `LCDClient` instance. Because they make HTTP requests in the background, they are Promises that can be awaited in order to not block during network IO.

```ts
async main() {
  const marketParams = await ODISEO.market.parameters();
  const exchangeRates = await ODISEO.oracle.exchangeRates();
  console.log(marketParams.base_pool);
  console.log(exchangeRates.get('uusd'));
}

main();
```

Each module has its own set of querying functions. To get a comprehensive list, explore the module documentation:

- [`auth`](https://ODISEOmoney.github.io/ODISEO.js/classes/AuthAPI.html)
- [`bank`](https://ODISEOmoney.github.io/ODISEO.js/classes/BankAPI.html)
- [`distribution`](https://ODISEOmoney.github.io/ODISEO.js/classes/DistributionAPI.html)
- [`gov`](https://ODISEOmoney.github.io/ODISEO.js/classes/GovAPI.html)
- [`market`](https://ODISEOmoney.github.io/ODISEO.js/classes/MarketAPI.html)
- [`mint`](https://ODISEOmoney.github.io/ODISEO.js/classes/MintAPI.html)
- [`msgauth`](https://ODISEOmoney.github.io/ODISEO.js/classes/MsgAuthAPI.html)
- [`oracle`](https://ODISEOmoney.github.io/ODISEO.js/classes/OracleAPI.html)
- [`slashing`](https://ODISEOmoney.github.io/ODISEO.js/classes/SlashingAPI.html)
- [`staking`](https://ODISEOmoney.github.io/ODISEO.js/classes/StakingAPI.html)
- [`supply`](https://ODISEOmoney.github.io/ODISEO.js/classes/SupplyAPI.html)
- [`tendermint`](https://ODISEOmoney.github.io/ODISEO.js/classes/TendermintAPI.html)
- [`treasury`](https://ODISEOmoney.github.io/ODISEO.js/classes/TreasuryAPI.html)
- [`tx`](https://ODISEOmoney.github.io/ODISEO.js/classes/TxAPI.html)
- [`wasm`](https://ODISEOmoney.github.io/ODISEO.js/classes/WasmAPI.html)
