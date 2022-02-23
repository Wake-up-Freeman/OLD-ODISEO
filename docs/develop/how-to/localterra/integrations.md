# Integrations

You can integrate LocalDaodiseo in Daodiseo Station, `daodiseod`, and JavaScript and Python SDKs.

## Daodiseo Station

Daodiseo Station has built-in support for LocalDaodiseo for quick and easy interaction. [Open Station](https://station.daodiseo.money/) and switch to the `Localdaodiseo` network.

## daodiseod

1. Ensure the same version of `daodiseod` and LocalDaodiseo are installed.

2. Use `daodiseod` to talk to your LocalDaodiseo `daodiseod` node:

    ```sh
    $ daodiseod status
    ```

    This command automatically works because `daodiseod` connects to `localhost:26657` by default.

    The following command is the explicit form:
    ```sh
    $ daodiseod status --node=tcp://localhost:26657
    ```

3. Run any `daodiseod` commands against your LocalDaodiseo network:

   ```sh
   $ daodiseod query account daodiseo1dcegyrekltswvyy0xy69ydgxn9x8x32zdtapd8
   ```

## Daodiseo Python SDK

Connect to the chain through LocalDaodiseo's LCD server:

```python
from daodiseo_sdk.client.lcd import LCDClient
daodiseo = LCDClient("localdaodiseo", "http://localhost:1317")
```

## Daodiseo JavaScript SDK

Connect to the chain through LocalDaodiseo's LCD server:

```ts
import { LCDClient } from "@daodiseomoney/daodiseo.js";

const daodiseo = new LCDClient({
  URL: "http://localhost:1317",
  chainID: "localdaodiseo",
});
```
