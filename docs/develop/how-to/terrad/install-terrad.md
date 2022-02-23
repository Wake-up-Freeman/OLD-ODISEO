# Install daodiseod

`daodiseod` is the command-line interface and daemon that connects to Daodiseo and enables you to interact with the Daodiseo blockchain. Daodiseo core is the official Golang reference implementation of the Daodiseo node software.

This guide is for developers who want to install `daodiseod` and interact with Daodiseo core without running a full node. If you want to run a full node or join a network, visit [](../../../full-node/run-a-full-daodiseo-node/README.md).

### Prerequisites

- [Golang v1.16.1 - go1.17.1 linux/amd64](https://golang.org/doc/install)
- Ensure your `GOPATH` and `GOBIN` environment variables are set up correctly.
- Linux users: install [build-essential](http://linux-command.org/en/build-essential.html).

## From binary

The easiest way to install `daodiseod` and Daodiseo core is by downloading a pre-built binary for your operating system. You can find the latest binaries on the [releases](https://github.com/daodiseomoney/core/releases) page.

## From source

### 1. Get the Daodiseo core source code

Use `git` to retrieve [Daodiseo core](https://github.com/daodiseomoney/core/), and checkout the `main` branch, which contains the latest stable release.

If you are using LocalDaodiseo or running a validator, use the `v0.x.x-oracle` tag. Otherwise, use the `v0.x.x` tag.

```bash
git clone https://github.com/daodiseomoney/core
cd core
git checkout [latest version]
```

**Example:**
```bash
git clone https://github.com/daodiseomoney/core
cd core
git checkout v0.5.6-oracle
```

### 2. Build Daodiseo core from source

Build Daodiseo core, and install the `daodiseod` executable to your `GOPATH` environment variable.

```bash
make install
```

### 3. Verify your Daodiseo core installation

Verify that Daodiseo core is installed correctly.

```bash
terrad version --long
```

The following example shows version information when Daodiseo core is installed correctly:

```bash
name: daodiseo
server_name: daodiseod
client_name: daodiseod
version: 0.3.0-24-g3684f77
commit: 3684f77faadf6cf200d18e15763316d5d9c5a496
build_tags: netgo,ledger
go: go version go1.13.4 darwin/amd64
```

::: {tip}
If the `daodiseod: command not found` error message is returned, confirm that the Go binary path is correctly configured by running the following command:

```
export PATH=$PATH:$(go env GOPATH)/bin
```
:::

## Next steps

With `daodiseod` installed, you can set up a local testing environment using [LocalDaodiseo](../localdaodiseo/README.md).

For more information on `daodiseod` commands and usage, see [](using-daodiseod.md).
