---
title: Configure a Permissioned Operator
sidebar_position: 3
---
By default, all Operators are Public and allow any staker/address to onboard new validators to them.

Operator can be turned to Private, which restricts validator onboardings from a set of whitelisted addresses.

So this guide explains how to:
* [Change Operator status](#updating-your-operator-status)
* [Whitelist addresses](#addingremoving-authorized-addresses)
* [Use an external whitelist contract](#adding-an-external-contract)

:::info Owner Address
**Note:** You need to use the same Web3 address that you registered operator(s) with.
:::

### Updating your Operator Status

[**Open the Web App**](https://app.ssv.network/operators) and select the Operator you want to update from the _Operator Dashboard_.

![config-operator](/img/configure-a-permissioned-operator-1.avif)

Then, on the _Operator Details_ screen, click on the three vertical dots on the top-right corner, from the dropdown, choose the _Access Settings_ option.

![config-operator](/img/configure-a-permissioned-operator-2.avif)

In the following screen, you will see options to change the status of your operator, add authorized addresses, and set an external whitelisting contract to manage these addresses.

![config-operator](/img/configure-a-permissioned-operator-3.avif)


Let's start by changing the status of our operator to private, start by clicking on the Operator Status option which will bring you to the following screen:

![config-operator](/img/configure-a-permissioned-operator-4.avif)

After clicking Switch to Private, you will be prompted to sign a transaction with your Web3 wallet.

<div style={{ display: 'flex', justifyContent: 'center' }}>
  <img 
    src="/img/configure-a-permissioned-operator-5.png" 
    alt="Switch to private" 
    style={{ width: '50%', maxWidth: '500px' }}
  />
</div>

Once the transaction is signed, you will only need to wait for the blockchain to validate it, and the settings will be live.

To change your operator status back to public, follow the same steps and turn the flag off again.

### Adding/Removing Authorized addresses

[**Open the Web App**](https://app.ssv.network/operators) and select the Operator you want to update from the _Operator Dashboard_.

![config-operator](/img/configure-a-permissioned-operator-1.avif)

Then, on the _Operator Details_ screen, click on the three vertical dots on the top-right corner, from the dropdown, choose the _Access Settings_ option.

![config-operator](/img/configure-a-permissioned-operator-2.avif)

Start by clicking on the *Authorized Addresses* option, which will bring you to the following screen:

![config-operator](/img/configure-a-permissioned-operator-3.avif)

Here we're adding two authorized addresses, simply add valid Ethereum addresses you wish to whitelist.

![config-operator](/img/configure-a-permissioned-operator-6.avif)

Once done, click "Add and Save" to sign the transaction with your Web3 wallet.

<div style={{ display: 'flex', justifyContent: 'center' }}>
  <img 
    src="/img/configure-a-permissioned-operator-7.png" 
    alt="Switch to private" 
    style={{ width: '50%', maxWidth: '500px' }}
  />
</div>

### Adding an External Contract

SSV also gives you the option to add your own whitelisting contract for managing authorized addresses. This contract must follow certain specifications [which can be found here](/developers/smart-contracts/external-whitelist-contract-example.md).

To start, [**open the Web App**](https://app.ssv.network/operators) and select the Operator you want to update from the _Operator Dashboard_.

![config-operator](/img/configure-a-permissioned-operator-1.avif)

Then, on the _Operator Details_ screen, click on the three vertical dots on the top-right corner, from the dropdown, choose the _Access Settings_ option.

![config-operator](/img/configure-a-permissioned-operator-2.avif)

Click on the *External Contract* option, which will bring you to the following screen:

![config-operator](/img/configure-a-permissioned-operator-3.avif)

After clicking the External Contract option, you will be brought to the following screen. Enter a valid whitelisting contract address.

![config-operator](/img/configure-a-permissioned-operator-8.avif)

Once donce, click *Save* and you will be prompted to sign the transaction with your Web3 wallet.

![config-operator](/img/configure-a-permissioned-operator-9.avif)