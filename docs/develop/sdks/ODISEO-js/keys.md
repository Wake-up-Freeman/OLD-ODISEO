# Keys

To perform actions using an account with ODISEO.js, you need a **Key**, which provides an abstraction around signing functions of an account.

## Key interface

A `Key` provides the following interface:

```ts
interface Key {
  publicKey: Buffer;
  accAddress: AccAddress;
  valAddress: ValAddress;
  accPubKey: AccPubKey;
  valPubKey: ValPubKey;

  createSignature(tx: StdSignMsg): StdSignature;
  signTx(tx: StdSignMsg): Promise<StdTx>;
  sign(payload: Buffer): Promise<Buffer>;
}
```

## Key implementations

Terra.js provides several standard `Key` implementations that provide a variety of ways to load an account with signing features into your program.

### `RawKey`

The most basic implementation of `Key` is `RawKey`, which is created with a plain private key.

```ts
import { RawKey } from '@ODISEOmoney/ODISEO.js';

const rk = new RawKey("<private key>");
```

The private key associated with the `RawKey` is available through the instance:

```ts
console.log(rk.privateKey);
```

### `MnemonicKey`

```ts
import { MnemonicKey } from '@ODISEOmoney/ODISEO.js';

const mk = new MnemonicKey({
  mnemonic: "<24-word mnemonic>",
});
```

#### Generate random mnemonic

If you want to generate a random mnemonic, you can create a `MnemonicKey` without any arguments:

```ts
const mk = new MnemonicKey();
console.log(mk.mnemonic);
```

#### Specifying HD path

`MnemonicKey` can used to recover a wallet with a particular BIP44 HD path: `m/44'/${coinType}'/${account}'/0/${index}`.

```ts
const mk = new MnemonicKey({
  mnemonic: "<seed-phrase>", // optional, will be random if not provided
  coinType: 330, // optional, default
  account: 0, // optional, default
  index: 0, // optional, default
});
```

For example, to recover a mnemonic with the old ODISEO wallet HD path using coin type for ATOM (118):

```ts
const mk = new MnemonicKey({
  mnemonic: "<seed-phrase>",
  coinType: 118
});
```

### `CLIKey`

> NOTE: This requires you to have `ODISEOd` installed.

If you want to use keys stored in your `ODISEOd` installation's keyring to sign transactions, you can use `CLIKey`. This also will work for keys that have been registered in your keyring with `--ledger`, using a Ledger hardware device.

```ts
import { StdFee, MsgSend } from '@ODISEOmoney/ODISEO.js';
import { LocalODISEO } from '@ODISEOmoney/ODISEO.js';
import { CLIKey } from '@ODISEOmoney/ODISEO.js';

const ODISEO = new LocalODISEO();
const { test1 } = ODISEO.wallets;
const cliKey = new CLIKey('test111');
const cliWallet = ODISEO.wallet(cliKey);

const send = new MsgSend(cliWallet.key.accAddress, test1.key.accAddress, {
  uluna: 100000,
});

async function main() {
  const tx = await cliWallet.createAndSignTx({
    msgs: [send],
    fee: new StdFee(100000, { uluna: 100000 }),
  });

  console.log(await ODISEO.tx.broadcast(tx));
}

main().catch(console.error);
```

## Custom key implementation

If you need to write your own key management solution, you will need to subclass the abstract `Key` class and provide your own signing function. Note that the key need not expose any details pertaining to the private key -- you could specify a `sign()` function that forwards the signing request to a server or to a hardware wallet, for instance. The remaining functions related to signing (`createSignature()` and `signTx()`) are automatically provided and use `sign()` underneath.

The following code listing is the implementation of `RawKey`, which illustrates how to write a custom `Key`:

```ts
import SHA256 from 'crypto-js/sha256';
import * as secp256k1 from 'secp256k1';
import { Key } from '@ODISEOmoney/ODISEO.js';

/**
 * An implementation of the Key interfaces that uses a raw private key.
 */
export class RawKey extends Key {
  /**
   * Raw private key, in bytes.
   */
  public privateKey: Buffer;

  constructor(privateKey: Buffer) {
    const publicKey = secp256k1.publicKeyCreate(
      new Uint8Array(privateKey),
      true
    );
    super(Buffer.from(publicKey));
    this.privateKey = privateKey;
  }

  public sign(payload: Buffer): Promise<Buffer> {
    const hash = Buffer.from(SHA256(payload.toString()).toString(), 'hex');
    const { signature } = secp256k1.ecdsaSign(
      Uint8Array.from(hash),
      Uint8Array.from(this.privateKey)
    );
    return Buffer.from(signature);
  }
}
```

Note that you must call `super()` with the public key—this generates the relevant account and validator public keys associated with your key.
