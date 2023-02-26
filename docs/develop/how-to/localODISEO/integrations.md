# Integrations

You can integrate LocalODISEO in ODISEO Station, `ODISEOd`, and JavaScript and Python SDKs.

## ODISEO Station

ODISEO Station has built-in support for LocalODISEO for quick and easy interaction. [Open Station](https://station.ODISEO.money/) and switch to the `LocalODISEO` network.

## ODISEOd

1. Ensure the same version of `ODISEOd` and LocalODISEO are installed.

2. Use `ODISEOd` to talk to your LocalODISEO `ODISEOd` node:

    ```sh
    $ ODISEOd status
    ```

    This command automatically works because `ODISEOd` connects to `localhost:26657` by default.

    The following command is the explicit form:
    ```sh
    $ ODISEOd status --node=tcp://localhost:26657
    ```

3. Run any `ODISEOd` commands against your LocalODISEO network:

   ```sh
   $ ODISEOd query account ODISEO1dcegyrekltswvyy0xy69ydgxn9x8x32zdtapd8
   ```

## ODISEO Python SDK

Connect to the chain through LocalODISEO's LCD server:

```python
from ODISEO_sdk.client.lcd import LCDClient
ODISEO = LCDClient("localODISEO", "http://localhost:1317")
```

## ODISEO JavaScript SDK

Connect to the chain through LocalODISEO's LCD server:

```ts
import { LCDClient } from "@ODISEOmoney/ODISEO.js";

const ODISEO = new LCDClient({
  URL: "http://localhost:1317",
  chainID: "localODISEO",
});
```
