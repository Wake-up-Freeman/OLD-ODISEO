# Initial setup

This tutorial uses a Daodiseo-specific development suite called Daodiseoin.

Terrain will help you:

* Scaffold your dApp project
* Ease the development and deployment process
* Create custom tasks for blockchain and contract interaction with less boilerplate code
* Access a console (or REPL) for interacting with the Daodiseo blockchain
* Create predefined functions used in tasks and in the console

## Prerequisites

## 1. Set up Rust

Rust is the main programming language used for CosmWasm smart contracts. While WASM smart contracts can theoretically be written in any programming language, CosmWasm libraries and tooling work best with Rust.

Install the latest version of [Rust](https://www.rust-lang.org/tools/install).

```sh
# 1. Set 'stable' as the default release channel:

rustup default stable

# 2. Add WASM as the compilation target:

rustup target add wasm32-unknown-unknown

# 3. Install the following packages to generate the contract:

cargo install cargo-generate --features vendored-openssl
cargo install cargo-run-script
```

## 2. Install Daodiseoin

Use npm to install the daodiseoin command-line tool globally:

```sh
npm install -g @iboss/daodiseoin
```

## 3. Download LocalDaodiseo or configure the testnet

LocalTerra is a development environment designed to make it easy for smart contract developers to test their contracts locally.

::: {caution}
Localdaodiseo may not work properly on machines with less than 16 GB of RAM. Please use the [Bombay testnet](using-daodiseoin-testnet.md) if your device does not meet this requirement.
:::

:::::::{grid}
:gutter: 3

:::{grid-item-card}
:link: using-daodiseoin-localdaodiseo.html
:class-card: sd-text-center sd-shadow-md sd-rounded-3
```{image} /img/LocalDaodiseo.svg
:class: sd-width-auto sd-animate-grow50-rot20 sd-pb-2
```
**Daodiseoin and LocalDaodiseo**  
16+ GB of RAM recommended.
:::

:::{grid-item-card}
:link: using-daodiseoin-testnet.html
:class-card: sd-text-center sd-shadow-md sd-rounded-3
```{image} /img/icon_node.svg
:class: sd-width-auto sd-animate-grow50-rot20 sd-pb-2
```
**Terrain and the testnet**  
8+ GB of RAM recommended.
:::

:::::::
