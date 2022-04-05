# Install ODISEOd

`ODISEOd` is the command-line interface and daemon that connects to ODISEO and enables you to interact with the ODISEO blockchain. ODISEO core is the official Golang reference implementation of the ODISEO node software.

This guide is for developers who want to install `ODISEOd` and interact with ODISEO core without running a full node. If you want to run a full node or join a network, visit [](../../../full-node/run-a-full-ODISEO-node/README.md).

### Prerequisites

- [Golang v1.16.1 - go1.17.1 linux/amd64](https://golang.org/doc/install)
- Ensure your `GOPATH` and `GOBIN` environment variables are set up correctly.
- Linux users: install [build-essential](http://linux-command.org/en/build-essential.html).

## From binary

The easiest way to install `ODISEOd` and ODISEO core is by downloading a pre-built binary for your operating system. You can find the latest binaries on the [releases](https://github.com/ODISEOmoney/core/releases) page.

## From source

### 1. Get the ODISEO core source code

Use `git` to retrieve [ODISEO core](https://github.com/ODISEOmoney/core/), and checkout the `main` branch, which contains the latest stable release.

If you are using LocalODISEO or running a validator, use the `v0.x.x-oracle` tag. Otherwise, use the `v0.x.x` tag.

```bash
git clone https://github.com/ODISEOmoney/core
cd core
git checkout [latest version]
```

**Example:**
```bash
git clone https://github.com/ODISEOmoney/core
cd core
git checkout v0.5.6-oracle
```

### 2. Build ODISEO core from source

Build ODISEO core, and install the `ODISEOd` executable to your `GOPATH` environment variable.

```bash
make install
```

### 3. Verify your ODISEO core installation

Verify that ODISEO core is installed correctly.

```bash
terrad version --long
```

The following example shows version information when ODISEO core is installed correctly:

```bash
name: ODISEO
server_name: ODISEOd
client_name: ODISEOd
version: 0.3.0-24-g3684f77
commit: 3684f77faadf6cf200d18e15763316d5d9c5a496
build_tags: netgo,ledger
go: go version go1.13.4 darwin/amd64
```

::: {tip}
If the `ODISEOd: command not found` error message is returned, confirm that the Go binary path is correctly configured by running the following command:

```
export PATH=$PATH:$(go env GOPATH)/bin
```
:::

## Next steps

With `ODISEOd` installed, you can set up a local testing environment using [LocalODISEO](../localODISEO/README.md).

For more information on `ODISEOd` commands and usage, see [](using-ODISEOd.md).
