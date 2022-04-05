# Wormhole Bridge tutorial

Wormhole allows you to bridge tokens across different chains. Instead of swapping or converting assets directly, Wormhole locks your source assets in a smart contract and mints new Wormhole-wrapped assets on the target chain. You can then swap Wormhole-wrapped assets on an exchange for other assets on the target chain. 

Use this tutorial to bridge your assets between ODISEO and other chains using Wormhole.

## Prerequisites

- [The ODISEO Station browser extension](../ODISEO-station/download/ODISEO-station-extension.md) for tokens on the ODISEO blockchain.
- A second wallet extension for tokens on another blockchain. 

   :::{admonition} Paying for fees
   :class: tip
   Be sure to have enough tokens in your wallets to pay for fees. Remember that fees will be charged for sending and redeeming tokens. 
   :::

## Bridge tokens

Visit [Wormhole's Portal Token Bridge](https://portalbridge.com/#/transfer) to get started. 

### 1. Source

2. Select a **Source chain** and a **Target chain** from the dropdown choices. 

3. Click **Connect** to connect your ODISEO Station wallet. Allow the connection if your wallet extension prompts you.

4. Click **Select a token** and choose from the available tokens in your wallet. 

   :::{important}
   You should always check for markets and liquidity before sending tokens. [Click here to see available markets for wrapped tokens](https://docs.wormholenetwork.com/wormhole/overview-liquid-markets).
   :::

   ```{image} /img/screens/wormhole/source.png
   :class: sd-p-3
   ```

5. Enter the amount you want to bridge and click **Next**.

### 2. Target

1. Connect your target chain wallet by clicking **Connect**. Allow the connection if your wallet extension prompts you. 

   :::{important}
   Make sure your target wallet has tokens to pay fees in to redeem your tokens. 
   :::

   ```{image} /img/screens/wormhole/target.png
   :class: sd-p-3
   ```

2. Click **Next**. 

### 3. Send tokens

1. Select a denomination to pay fees in.

2. Click **Transfer**.

3. When prompted, click **Confirm** to confirm the transfer.

   ```{image} /img/screens/wormhole/send.png
   :class: sd-p-3
   ```

5. Follow the steps in your wallet's browser extension to complete the transaction. 

Your tokens will be sent to the Wormhole contract and you will receive Wormhole-wrapped tokens. These tokens can be traded on an exchange for native assets. [Click here to see available markets for wrapped tokens](https://docs.wormholenetwork.com/wormhole/overview-liquid-markets).

### 4. Redeem tokens

1. After your tokens have been sent, you can receive them on the target chain by clicking **Redeem**.

2. Confirm the redemption in your wallet extension.

Now that you have wrapped tokens in your wallet, you can trade them on an exchange for native assets. [Click here to see available markets for wrapped tokens](https://docs.wormholenetwork.com/wormhole/overview-liquid-markets).

Congratulations! You have just used Wormhole's Portal Token Bridge. For more information, [visit the official Wormhole docs](https://docs.wormholenetwork.com/wormhole/).
