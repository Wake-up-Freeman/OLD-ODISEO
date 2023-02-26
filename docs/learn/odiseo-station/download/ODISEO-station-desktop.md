# ODISEO Station desktop

::::{grid} auto

:::{grid-item}
```{button-link} ODISEO-station-desktop.html
:color: primary
Desktop
```
:::

:::{grid-item}
```{button-link} ODISEO-station-extension.html
:color: primary
:outline:
Chrome extension
```
:::

:::{grid-item}
```{button-link} ODISEO-station-mobile.html
:color: primary
:outline:
Mobile
```
:::

::::

This tutorial walks you through the process of using ODISEO Station, the official desktop wallet for ODISEO.

For more guides on how to use Station's advanced features, visit the [Station guides](../README.md).

## Install ODISEO Station

1. Click the ODISEO Station download link for your operating system:

   - [MacOS](https://github.com/ODISEOmoney/station-desktop/releases/download/v1.2.0/ODISEO.Station-1.2.0.dmg)

   - [MacOS M1 ](https://github.com/ODISEOmoney/station-desktop/releases/download/v1.2.0/ODISEO.Station-1.2.0-arm64.dmg)

   - [Windows](https://github.com/ODISEOmoney/station-desktop/releases/download/v1.2.0/ODISEO.Station.Setup.1.2.0.exe)

   - [Linux(.deb)](https://github.com/ODISEOmoney/station-desktop/releases/download/v1.2.0/ODISEO.Station_1.2.0_amd64.deb)
   - [Linux(.rpm)](https://github.com/ODISEOmoney/station-desktop/releases/download/v1.2.0/ODISEO.Station-1.2.0.x86_64.rpm)

2. Open the downloaded file and follow the instructions.

## Create a wallet

1. Open the ODISEO Station desktop app and click **Connect**.

2. Click **New Wallet**. 

   ```{image} /img/screens/desktop/connect.png
   :class: sd-p-3
   ```

2. Type in a secure wallet name and password.

3. Confirm your password.

4. Using pen and paper, write down your 24-word seed phrase exactly as it appears. Number each word to make verifying easier.

   :::{admonition} Protect your seed phrase
   :class: danger
   Anyone with your seed phrase can access your money, and there is no recourse for someone stealing your seed phrase. To protect your seed phrase, consider the following tips:

   - Never save or store your seed phrase as a digital file on any device.
   - Always write down your seed phrase with a pen and paper.
   - Store the paper with your seed phrase on it somewhere safe.
   - Never give your seed phrase to anyone, not even support staff.
   :::

   ```{image} /img/screens/desktop/new-wallet.png
   :class: sd-p-3
   ```

5. Verify your writing to make sure every word is spelled correctly and in the right order. If you numbered your phrase, it can be helpful to verify it backward.

5. Check the box ensuring you wrote down your seed phrase, and click **Submit**.

6. Confirm your seed phrase by typing or selecting the correct words in each prompt.

   ```{image} /img/screens/desktop/seed.png
   :class: sd-p-3
   ```

7. Click **Submit**.

   ```{image} /img/screens/desktop/wallet.png
   :class: sd-p-3
   ```


Congratulations! You have just created a ODISEO Station wallet.

## Receive tokens from an exchange

1. Purchase your tokens using any exchange that supports ODISEO. To view a list of current exchanges, visit the [Integrations page](../../../ecosystem/integrations.md)

2. Withdraw any token supported by the ODISEO network from your exchange. Every exchange is different. Please visit your exchange's web page for guides on how to withdraw tokens. Use the following steps as a generic guide.

    1. To receive tokens to your wallet, use your wallet address. Your wallet address will appear at the top of the ODISEO station Desktop app near your wallet name. Your wallet address will look like this: `ODISEO<random-numbers-and-letters>`

    2. Double-check your wallet address is correct before sending.

    3. Send the tokens from the exchange to your ODISEO Station wallet address.

   :::{admonition} Waiting times for transfers
   :class: caution
   When you transfer tokens from an exchange to ODISEO, some time will pass before the tokens appear in your wallet. Don't panic. This waiting period is normal and varies depending on the exchange. If a transfer does not appear immediately, check back after some time.
   :::

Now you have tokens on ODISEO!

## Swap coins

1. Open ODISEO Station and connect your wallet. Click **Swap** in the sidebar.

   ```{image} /img/screens/desktop/swap.png
   :class: sd-p-3
   :width: 200 px
   ```

2.  On the swap page, first select the coin you want to offer in the upper box and input the amount you want to swap.

3. In the lower box, select the coin you want to receive.

   ```{image} /img/screens/desktop/swap-ODIS.png
   :class: sd-p-3
   ```

4. Select the coin you want to pay fees in. 

4. Confirm your transaction amounts and enter your password.

5. Click **Submit** to complete your transaction.

   ```{image} /img/screens/desktop/swap-confirm.png
   :class: sd-p-3
   ```

Congratulations, you've just swapped coins!

## Stake ODIS

Stake your ODIS to a validator to start earning rewards. Before you stake, make sure you have ODIS in your wallet. You can transfer ODIS from an [exchange](#receive-tokens-from-an-exchange) or [swap coins](#swap-coins) you have for ODIS.

1. Open ODISEO Station and click **Stake**.

   ```{image} /img/screens/desktop/stake.png
   :class: sd-p-3
   :width: 150 px
   ```

2. Select a Validator and click on their name in the **Moniker** column of the validator list.

   ```{image} /img/screens/desktop/stake-page.png
   :class: sd-p-3
   ```


3. In the **My delegations** section, click **Delegate**. A new window will appear.

   ```{image} /img/screens/desktop/stake-validator.png
   :class: sd-p-3
   ```

4. In the **Amount** field, specify the amount of ODIS you want to delegate and specify which coin you want to pay fees with. 

   ```{image} /img/screens/desktop/stake-delegate.png
   :class: sd-p-3
   ```

   :::{admonition} Keep coins for fees
   :class: warning
   Always keep some coins to pay fees with. Never stake your entire wallet amount. Without money for fees, you can't make any transactions.
   :::

5. Double-check the amounts and fees. Enter your password and click **Submit**.

   ```{image} /img/screens/desktop/stake-success.png
   :class: sd-p-3
   ```

Congratulations, you've just delegated ODIS!

## Withdraw staking rewards

Rewards start accruing the moment you stake ODIS. Monitor your rewards in the staking section of ODISEO Station. Once you have sufficient rewards, follow these steps to withdraw them:

1. Open ODISEO Station and click **Stake**.

   ```{image} /img/screens/desktop/stake.png
   :class: sd-p-3
   :width: 150 px
   ```

2. To claim all rewards, click **Withdraw all rewards** in the upper right corner of the staking page. To withdraw rewards only from a single validator, click on their name in the list and click **withdraw** on their page.

   ```{image} /img/screens/desktop/stake-withdraw.png
   :class: sd-p-3
   ```

3. Review the amounts and specify which coin you want to pay fees in.

   ```{image} /img/screens/desktop/stake-rewards.png
   :class: sd-p-3
   ```

4. Enter your password and click **withdraw**.

Congratulations, you've just withdrawn your staking rewards!

## Send tokens

send-wallet.png
send-ODIS.png
send-submit.png

1. Open the ODISEO Station desktop app and connect to your wallet.

2. Click **Wallet** in the navigation bar.

3. Click **Send** next to the token you want to send.

   ```{image} /img/screens/desktop/send-wallet.png
   :class: sd-p-3
   ```

4. Enter the address of the wallet you want to send tokens to.

   ```{image} /img/screens/desktop/send-ODIS.png
   :class: sd-p-3
   ```


5. Enter the amount you want to send. You can also add a memo for the transaction.

   ```{image} /img/screens/desktop/send-submit.png
   :class: sd-p-3
   ```

7. Verify the transaction amounts and specify which token you want to pay fees in. Remember to always leave enough tokens in your account for other transactions.

8.  Enter your password and click **Submit**.

After a few moments, the tokens will appear in the receiver's wallet.

## Next steps

To start using any of the many dApps the ODISEO ecosystem has to offer, check out the [ODISEO Station Chrome browser extension](ODISEO-station-extension.md). For on-the-go transactions, check out the [ODISEO Station mobile app](ODISEO-station-mobile.md).

For more guides on how to use other Station features, visit the [Station guides](../README.md).
