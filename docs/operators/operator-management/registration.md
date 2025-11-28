---
title: Registering an Operator
sidebar_position: 1
---

# Operator Management

After [you followed the guide on Node setup](/operators/operator-node/node-setup) and successfully started an SSV node, you can register your Operator in the network and start earning rewards 🥳

**Steps to finalize the registration:**
* [Register your Operator](#operator-registration) - start participating in SSV Network.
* [Set Operator Metadata](/operators/operator-management/setting-operator-metadata.md) - stakers will see this information on Explorer page.

There are other optional steps you might want to follow:
* [*Configure a Permissioned Operator*](/operators/operator-management/configuring-a-permissioned-operator.md) - in case you want to whitelist specific validator owners.
* [*Update Operator Fees*](/operators/operator-management/updating-operator-fees.md) - in case you'd like to change your fees.
* [Withdraw Earnings](/operators/operator-management/withdrawing-earnings.md) - to receive your fees.
* [Remove an Operator](/operators/operator-management/removing-an-operator.md) - if you wish to stop participating.

## Operator Registration

Once your SSV Node is up and running, an operator must be registered to the SSV Network in order to be discoverable by validators.

You can register your operator through the SSV [Web App](https://app.ssv.network) or via a transaction directly to the [smart contract](/developers/smart-contracts/ssvnetwork.md#registeroperatorpublickey-operatorfee-setprivate).

While registering your operator you will need to provide the following parameters:

* [Operator public key](/operators/operator-node/node-setup/manual-setup#generate-operator-keys-encrypted) - Generated in the node installation process. It can be found in the private key file, search for `pubKey`. 
* [Operator fee](/learn/tokenomics/fees) - The fee charged by the operator per each managed validator

:::info Owner Address
The wallet address used to register the operator is the operator owner address, it can't be changed.
:::

## Registering an Operator on the Web App

[Open the SSV Web App](https://app.ssv.network/join/operator) and connect your Web3 Wallet.

In the following screen, select _Register Operator_.

![register-operator](/img/register-an-operator-11.avif)

The next screen will ask you to input the Operator's public key and provide a confirmation of the Operator owner address. Public key can be found in the private key file, search for `pubKey`. 

Here you will also have to choose whether your Operator status is either [public or private](/learn/network-overview/operators/permissioned-operators).

:::warning Owner Address
Please verify again the owner address is the wallet address you want to manage your operators with.
:::

<div style={{ display: 'flex', justifyContent: 'center' }}>
  <img 
    src="/img/register-an-operator-2.png" 
    alt="Register an operator" 
    style={{ width: '70%', maxWidth: '500px' }}
  />
</div>

Then you will be asked to set the Operator Fee.

For more information about fees, please [head over to the related page](/learn/tokenomics/fees). Just know that it will be possible to update the Operator fees later, [with limitations imposed by the protocol, to protect stakers](/learn/network-overview/operators/update-fee), for a guide on how to do that, head over to [the dedicated page](/operators/operator-management/updating-operator-fees).

Enter a number and click _Next_ when ready.

![register-operator](/img/register-an-operator-3.avif)

This confirmation screen presents a recap of the information input so far. Double check everything and click _Register Operator_ when ready.

![register-operator](/img/register-an-operator-4.avif)

The WebApp will generate a blockchain transaction, make sure to open your Web3 wallet, if it does not automatically and confirm the transaction.

<div style={{ display: 'flex', justifyContent: 'center' }}>
  <img 
    src="/img/register-an-operator-5.png" 
    alt="Register an operator" 
    style={{ width: '45%', maxWidth: '500px' }}
  />
</div>

Congratulations, your Operator is successfully registered! 

To increase your chances of being chosen by stakers, set [your Operator's metadata](/operators/operator-management/setting-operator-metadata.md).

![register-operator](/img/register-an-operator-7.avif)