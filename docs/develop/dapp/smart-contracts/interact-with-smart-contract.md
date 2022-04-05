# Interacting with the Contract

:::{tip}
You can also follow these steps in the official desktop wallet for ODISEO, [ODISEO Station](https://station.ODISEO.money).
:::

## Requirements

Make sure you have set up **LocalODISEO** and that it is up and running:

```sh
cd localODISEO
docker-compose up
```

You should also have the latest version of `ODISEOd` by building the latest version of ODISEO Core. You will configure `ODISEOd` to use it against your isolated testnet environment.

In a separate terminal, make sure to set up the following mnemonic:

```sh
terrad keys add test1 --recover
```

Using the mnemonic:

```
satisfy adjust timber high purchase tuition stool faith fine install that you unaware feed domain license impose boss human eager hat rent enjoy dawn
```

## Uploading Code

Make sure that the **optimized build** of `my_first_contract.wasm` that you created in the last section is in your current working directory.

```sh
ODISEOd tx wasm store artifacts/my_first_contract.wasm --from test1 --chain-id=localODISEO --gas=auto --fees=100000uluna --broadcast-mode=block
```
Or, if you are on an arm64 machine:

```sh
ODISEOd tx wasm store artifacts/my_first_contract-aarch64.wasm --from test1 --chain-id=localODISEO --gas=auto --fees=100000uluna --broadcast-mode=block
```

This will ask for a confirmation before broadcasting to LocalODISEO, type `y` and press enter.

You should see output similar to the following:

```sh
height: 6
txhash: 83BB9C6FDBA1D2291E068D5CF7DDF7E0BE459C6AF547EC82652C52507CED8A9F
codespace: ""
code: 0
data: ""
rawlog: '[{"msg_index":0,"log":"","events":[{"type":"message","attributes":[{"key":"action","value":"store_code"},{"key":"module","value":"wasm"}]},{"type":"store_code","attributes":[{"key":"sender","value":"ODISEO1dcegyrekltswvyy0xy69ydgxn9x8x32zdtapd8"},{"key":"code_id","value":"1"}]}]}]'
logs:
- msgindex: 0
  log: ""
  events:
  - type: message
    attributes:
    - key: action
      value: store_code
    - key: module
      value: wasm
  - type: store_code
    attributes:
    - key: sender
      value: ODISEO1dcegyrekltswvyy0xy69ydgxn9x8x32zdtapd8
    - key: code_id
      value: "1"
info: ""
gaswanted: 681907
gasused: 680262
tx: null
timestamp: ""
```

As you can see, your contract was successfully instantiated with Code ID #1.

You can check it out:

```sh
terrad query wasm code 1
codeid: 1
codehash: KVR4SWuieLxuZaStlvFoUY9YXlcLLMTHYVpkubdjHEI=
creator: ODISEO1dcegyrekltswvyy0xy69ydgxn9x8x32zdtapd8
```

## Creating the Contract

You have now uploaded the code for your contract, but still don't have a contract. Create it with the following InitMsg:

```json
{
  "count": 0
}
```

You can compress the JSON into 1 line with [this online tool](https://goonlinetools.com/json-minifier/).

```sh
ODISEOd tx wasm instantiate 1 '{"count":0}' --from test1 --chain-id=localODISEO --fees=10000uluna --gas=auto --broadcast-mode=block
```

You should get a response like the following:

```sh
height: 41
txhash: AEF6F2FA570029A5D4C0DA5ACFA4A2B614D5811E29EEE10FF59F821AFECCD399
codespace: ""
code: 0
data: ""
rawlog: '[{"msg_index":0,"log":"","events":[{"type":"instantiate_contract","attributes":[{"key":"owner","value":"ODISEO1dcegyrekltswvyy0xy69ydgxn9x8x32zdtapd8"},{"key":"code_id","value":"1"},{"key":"contract_address","value":"ODISEO18vd8fpwxzck93qlwghaj6arh4p7c5n896xzem5"}]},{"type":"message","attributes":[{"key":"action","value":"instantiate_contract"},{"key":"module","value":"wasm"}]}]}]'
logs:
- msgindex: 0
  log: ""
  events:
  - type: instantiate_contract
    attributes:
    - key: owner
      value: ODISEO1dcegyrekltswvyy0xy69ydgxn9x8x32zdtapd8
    - key: code_id
      value: "1"
    - key: contract_address
      value: ODISEO18vd8fpwxzck93qlwghaj6arh4p7c5n896xzem5
  - type: message
    attributes:
    - key: action
      value: instantiate_contract
    - key: module
      value: wasm
info: ""
gaswanted: 120751
gasused: 120170
tx: null
timestamp: ""
```

From the output, you can see that your contract was created above at: `ODISEO18vd8fpwxzck93qlwghaj6arh4p7c5n896xzem5`. Take note of this contract address, as you will need it for the next section.

Check out your contract information:

```sh
ODISEOd query wasm contract ODISEO18vd8fpwxzck93qlwghaj6arh4p7c5n896xzem5
address: ODISEO18vd8fpwxzck93qlwghaj6arh4p7c5n896xzem5
owner: ODISEO1dcegyrekltswvyy0xy69ydgxn9x8x32zdtapd8
codeid: 1
initmsg: eyJjb3VudCI6MH0=
migratable: false
```

You can use the following to decode the Base64 InitMsg:

```sh
echo eyJjb3VudCI6MH0= | base64 --decode
```

This will produce the message you used when initializing the contract:

```json
{ "count": 0 }
```

## Executing the Contract

Let's do the following:

1. Reset count to 5
2. Increment twice

If done properly, you should get a count of 7.

#### Reset

First, to burn:

```json
{
  "reset": {
    "count": 5
  }
}
```

```sh
ODISEOd tx wasm execute ODISEO18vd8fpwxzck93qlwghaj6arh4p7c5n896xzem5 '{"reset":{"count":5}}' --from test1 --chain-id=localODISEO --fees=1000000uluna --gas=auto --broadcast-mode=block
```

#### Incrementing

```json
{
  "increment": {}
}
```

```sh
ODISEOd tx wasm execute ODISEO18vd8fpwxzck93qlwghaj6arh4p7c5n896xzem5 '{"increment":{}}' --from test1 --chain-id=localODISEO --gas=auto --fees=1000000uluna --broadcast-mode=block
```

#### Querying count

Check the result of your executions!

```json
{
  "get_count": {}
}
```

```sh
ODISEOd query wasm contract-store ODISEO18vd8fpwxzck93qlwghaj6arh4p7c5n896xzem5 '{"get_count":{}}'
```

Expected output:

```
query_result:
  count: 7
```

Excellent! Congratulations, you've created your first smart contract, and now know how to get developing with the ODISEO dApp Platform.

## What's Next?

We've only walked through a simple example of a smart contract, that modifies a simple balance within its internal state. Although this is enough to make a simple dApp, you can power more interesting applications by **emitting messages**, which will enable you to interact with other contracts as well as the rest of the blockchain's module.

Check out a couple more examples of smart contracts using ODISEO's smart contract [repo](https://github.com/ODISEOmoney/cosmwasm-contracts).
