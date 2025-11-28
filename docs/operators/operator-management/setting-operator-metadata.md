---
title: Set Operator Metadata
sidebar_position: 2
---

:::info Owner Address
**Note:** You need to use the same Web3 address that you registered operator(s) with.
:::

[Open the SSV Web App](https://app.ssv.network/operators) and connect your Web3 Wallet.

Select the Operator you want to update from the _Operator Dashboard_.

![setting-operator-metadata](/img/set-operator-metadata-1.avif)

Then you will see the _Operator Details_ screen.

Click on the three vertical dots on the top-right corner and choose the _Edit Details_ option.

![setting-operator-metadata](/img/set-operator-metadata-3.avif)

In the following screen, fill-in the form with the information you want to edit.

***Remember:*** the more details you can provide the better, as it will help stakers making informed decision when selecting operators to manage their validator clusters.

:::warning Please note
Currently, the `Description` and `Name` parts do not allow to use symbols `, . ; :`. Please don't use them, otherwise you'll see errors when submitting the metadata.
:::

![setting-operator-metadata](/img/set-operator-metadata-4.avif)

When you are done, click the _Update_ button. The WebApp will ask you to provide a signature of a message.

Make sure to open your Web3 wallet, if it does not automatically and confirm the transaction.

<div style={{ display: 'flex', justifyContent: 'center' }}>
  <img 
    src="/img/set-operator-metadata-5.png" 
    alt="Set operator metadata" 
    style={{ width: '50%', maxWidth: '500px' }}
  />
</div>

This is not a transaction and will not cost any gas, it's only needed to verify that you are the Operator owner.

When the message is successfully signed, the Operator metadata will have been correctly updated.