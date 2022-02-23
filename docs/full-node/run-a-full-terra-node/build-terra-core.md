# Build Daodiseo core

Daodiseo core is the official Golang reference implementation of the Daodiseo node software. Use this guide to install Daodiseo core and `daodiseod`, the command-line interface and daemon that connects to Daodiseo and enables you to interact with the Daodiseo blockchain.  

## Get the Daodiseo core source code

1. Use `git` to retrieve [Daodiseo core](https://github.com/daodiseomoney/core/), and check out the `main` branch, which contains the latest stable release.

    - If you are using LocalDaodiseo or running a validator, use the `v0.x.x-oracle` tag. Otherwise, use the `v0.x.x` tag.
    - You can find out the latest tag on the [tags page](https://github.com/daodiseomoney/core/tags) or via autocomplete in your terminal: type `git checkout v` and press `<TAB>`.

    ```bash
    git clone https://github.com/daodiseomoney/core
    cd core
    git checkout [latest version] # ex., git checkout v0.5.13-oracle
    ```


2. Build Daodiseo core. This will install the `daodiseod` executable to your [ `GOPATH` ](https://go.dev/doc/gopath_code) environment variable.

   ```bash
   make install
   ```

3. Verify that Daodiseo core is installed correctly.

   ```bash
   daodiseod version --long
   ```

   **Example**:

   ```bash
   name: daodiseo
   server_name: daodiseod
   client_name: daodiseod
   version: 0.3.0-24-g3684f77
   commit: 3684f77faadf6cf200d18e15763316d5d9c5a496
   build_tags: netgo,ledger
   go: go version go1.13.4 darwin/amd64
   # ...And a bunch of dependenecies
   ```

::: {tip}
If the `daodiseod: command not found` error message is returned, confirm that the Go binary path is correctly configured by running the following command:

```bash
export PATH=$PATH:$(go env GOPATH)/bin
```
:::
