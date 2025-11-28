---
title: Update Operator Fees
sidebar_position: 4
---

Any Operator can update their fees. Please note, there are limits imposed by the protocol for changing the Operator fee. You can read more about this in [the dedicated section](/learn/network-overview/operators/update-fee).

:::info Owner Address
**Note:** You need to use the same Web3 address that you registered operator(s) with.
:::

[**Open the Web App**](https://app.ssv.network/operators) and select the Operator you want to update from the _Operator Dashboard_.

![update-fee](/img/update-operator-fees-1.avif)

Then, on the _Operator Details_ screen, click on the _Update Fee_ button at the bottom left.

![update-fee](/img/update-operator-fees-2.avif)

Now, you have two options, choose the one you need:
- [Increase Fee](#increasing-operator-fee)
- [Decrease Fee](#decreasing-operator-fee)

### Increasing Operator Fee

In the following screen you'll be asked to enter a new fee. 

![update-fee](/img/update-operator-fees-3.avif)

If the proposed updated fee is within the limits, you can select _Next_, and the following screen is going to explain that the procedure is divided in two steps:

* fee update declaration
* fee update execution

The current operation is about declaring the new fee.

![update-fee](/img/update-operator-fees-4.avif)

You'll have to submit and confirm a transaction to interact with the smart contract, in order for the fee updates to be declared.

<div style={{ display: 'flex', justifyContent: 'center' }}>
  <img 
    src="/img/update-operator-fees-5.png" 
    alt="Declare fee update" 
    style={{ width: '45%', maxWidth: '500px' }}
  />
</div>

Then, a waiting period is necessary to let all the validators using this operators know about the fee update.

You can cancel the fee update at any time, but you will have to wait until the end of the waiting period to _Execute._

So, after the period has ended you will have to come back to this page and confirm the _Execution_ of the fee update.

![update-fee](/img/update-operator-fees-7.avif)

### Decreasing Operator Fee

There are no limitations for decreasing the Operator fee, as it is advantagious for Stakers.

Once you have decided a new fee which complies with the protocol's limits, click _Next_.

![update-fee](/img/update-operator-fees-8.avif)

The following screen summarizes the changes, asking for confirmation.

![update-fee](/img/update-operator-fees-9.avif)

When clicking on _Update Fee_ button you will be requested to sign a transaction. 

If you don't see the transaction - open your web3 wallet and confirm the transaction.

When the transaction is confirmed by the network, the changes will take place.

<div style={{ display: 'flex', justifyContent: 'center' }}>
  <img 
    src="/img/update-operator-fees-10.png" 
    alt="Declare fee update" 
    style={{ width: '45%', maxWidth: '500px' }}
  />
</div>