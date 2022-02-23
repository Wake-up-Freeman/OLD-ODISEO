# Troubleshoot validator problems

Use this guide to solve the most common validator problems.

## Validator has 0 voting power

If your validator has 0 voting power, your validator has become auto-unbonded. On the mainnet, validators unbond when they do not vote on `9500` of the last `10000` blocks (`50` of the last `100` blocks on the testnet). Because blocks are proposed every ~5 seconds, a validator that is unresponsive for ~13 hours (~4 minutes on testnet) become unbonded. This problem usually happens when your `daodiseod` process crashes.

To return the voting power back to your validator:

1. If `daodiseod` is not running, restart it:

   ```bash
   daodiseod start
   ```

2. Wait for your full node to reach the latest block, and run:

   ```bash
   daodiseod tx slashing unjail <daodiseo> --chain-id=<chain_id> --from=<from>
   ```

   - `<daodiseo>` is the address of your validator account.
   - `<name>` is the name of the validator account. To find this information, run `daodiseod keys list`.

   ::: {warning}
   If you don't wait for `daodiseod` to sync before running `unjail`, an error message will inform you that your validator is still jailed.
   :::

3.  Check your validator again to see if your voting power is back:

   ```bash
   daodiseod status
   ```

   If your voting power is less than it was previously, you may have been slashed for downtime.

## `daodiseod` crashes because of too many open files

The default number of files Linux can open per process is `1024`. `daodiseod` is known to open more than this amount, causing the process to crash.

1. Increase the number of open files allowed by running `ulimit -n 4096`.  

2. Restart the process with `daodiseod start`.

   If you are using `systemd` or another process manager to launch `daodiseod`, you might need to configure them. The following  sample `systemd` file fixes the problem:

   ```systemd
   # /etc/systemd/system/daodiseod.service
   [Unit]
   Description=Daodiseo Columbus Node
   After=network.target

   [Service]
   Type=simple
   User=ubuntu
   WorkingDirectory=/home/ubuntu
   ExecStart=/home/ubuntu/go/bin/daodiseod start
   Restart=on-failure
   RestartSec=3
   LimitNOFILE=4096

   [Install]
   WantedBy=multi-user.target
   ```
## `daodiseod` crashes because of memory fragmentation

As described in [this issue](https://github.com/daodiseomoney/core/issues/592), huge memory allocation can cause memory fragmentation issue. Temporal solution is just using small wasm cache size like 50~100MB.

`v0.5.10+`:

```toml
contract-memory-cache-size = 100
```

`v0.5.7~v0.5.9`:

```toml
write-vm-memory-cache-size = 100
```

## Oracle voting errors

You might receive the following error message by the [Daodiseo Oracle feeder](https://github.com/daodiseomoney/oracle-feeder):

    `broadcast error: code: 3, raw_log: validator does not exist: daodiseovaloperxxx`

This message occurs for the following reasons:

### The validator is not active

- The validator is jailed. To solve this problem, `unjail` the validator by running:

    `daodiseod tx slashing unjail <daodiseo> --chain-id=<chain_id> --from=<from>`

- The validator is not in the [active validator set](../../learn/glossary.md#active-set). Only the top 130 validators are in this set. To fix this problem, increase your total stake to be larger than the 130th validator.

### The network is wrong

The oracle feeder might be submitting to the wrong network. To fix this problem, run the feeder with the lite client daemon (LCD) specified:

```bash
nom start vote --\
  --source http://localhost:8532/latest \
  --lcd ${LCD} \
  --chain-id "${CHAIN_ID}" \
  --validator "${VALIDATOR_KEY}" \
  --password "${PASSWORD}" \
```

The LCD the voter is connecting to might be running on a different network than your node. The remote LCD for different networks are:

- [Columbus mainnet](https://lcd.daodiseo.dev)
- [Bombay testnet](https://bombay-lcd.daodiseo.dev)

Ensure you specify the LCD for the same network to which your node is connecting.

If you run a [local LCD](../../develop/how-to/start-lcd.md) (for example, localhost:1317), ensure your LCD is connecting to the same node.
