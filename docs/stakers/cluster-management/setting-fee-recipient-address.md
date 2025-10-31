---
title: Set Fee Recipient
sidebar_position: 5
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# Setting Fee Recipient Address

:::danger
This procedure will set the fee recipient address for block proposal rewards **for all your validators**.
:::

### Introduction

Fee Recipient is an address that receives execution layer rewards. The default Fee Recipient for all validators in a given account the owner address. This page explains how to change this.

For more information on this topic, please refer to [the dedicated learning page](../../stakers/validators/validator-rewards.md). 

### How to Change Fee Recipient

Make sure to connect your Web3 address/wallet with the WebApp. Use the address you registered your validators with.

<Tabs>
  <TabItem value="detailed-guide" label="Detailed Guide">

1. [**In the Clusters page**](https://app.ssv.network/clusters), click on the **"Fee Address"** button.

![change-fee-recipient](/img/fee-recipient-1.avif)

2. **Enter the address of the wallet** you want to receive rewards for all your validators, **then click on Update**.

![change-fee-recipient](/img/fee-recipient-3.avif)

3. **Confirm and sign the transaction** from your Web3 wallet.

<div style={{ display: 'flex', justifyContent: 'center' }}>
  <img 
    src="/img/fee-recipient-4.png" 
    alt="change-fee-recipient" 
    style={{ width: '30%', maxWidth: '500px' }}
  />
</div>

  </TabItem>
  <TabItem value="checklist" label="Checklist">

1. [**In the Clusters page**](https://app.ssv.network/clusters), click on the **"Fee Address"** button.

2. **Enter the address of the wallet** you want to receive rewards for all your validators, **then click on Update**.

3. **Confirm and sign the transaction** from your Web3 wallet.

  </TabItem>
</Tabs>

Once the transaction has been signed and confirmed by the network, the fee recipient address for block proposal rewards will be correctly set for all your validators.