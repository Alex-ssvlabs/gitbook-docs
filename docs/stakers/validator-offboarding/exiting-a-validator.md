---
title: Exit a Validator
sidebar_position: 1
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# Exit a Validator

:::warning Remember
To exit a validator via SSV, it has to be registered with ssv.network.

If the validator is removed first, the following operations won't be possible. Then the validator will have to be exited via [Ethereum Launchpad](https://launchpad.ethereum.org/en/validator-actions) or another validator stack.
:::

Make sure to connect your Web3 address/wallet with the WebApp. Use the address you registered your validators with.

### Bulk Exit

If a cluster is managing more than one validator, it is possible to select multiple validators at once. 

<Tabs>
  <TabItem value="detailed-guide" label="Detailed Guide">

1. [**In the Clusters page**](https://app.ssv.network/clusters), **select the cluster that has validators** you wish to exit.

![exit-validator](/img/exit-a-validator-1.avif)

2. Click the **Actions** dropdown on top of the validators table. Select **Exit validators**.

![exit-validator](/img/exit-a-validator-3.avif)

3. In the following screen, you can **select the validators you want to exit**. When ready, press the **Next** button.

![exit-validator](/img/exit-a-validator-4.avif)

4. **Acknowledge Exit confirmation** *([details are here](#summary-and-confirmation))*

![exit-validator](/img/exit-a-validator-6.avif)

5. **Sign a transaction** *([details are here](#transaction-signature))*

<div style={{ display: 'flex', justifyContent: 'center' }}>
  <img 
    src="/img/exit-a-validator-7.png" 
    alt="Deposit SSV" 
    style={{ width: '30%', maxWidth: '500px' }}
  />
</div>

  </TabItem>
  <TabItem value="checklist" label="Checklist">

1. [**In the Clusters page**](https://app.ssv.network/clusters), **select the cluster that has validators** you wish to exit.

2. Click the **Actions** dropdown on top of the validators table. Select **Exit validators**.

3. In the following screen, you can **select the validators you want to exit**. When ready, press the **Next** button.

4. **Acknowledge Exit confirmation** *([details are here](#summary-and-confirmation))*

5. **Sign a transaction** *([details are here](#transaction-signature))*

  </TabItem>
</Tabs>

6. Check out the [Next Steps](#next-steps)

### Single Validator Exit

<Tabs>
  <TabItem value="detailed-guide" label="Detailed Guide">

1. [**In the Clusters page**](https://app.ssv.network/clusters), **select the cluster that has validator** you wish to exit.

![exit-validator](/img/exit-a-validator-1.avif)

2. **Tap the gear icon next to the validator** you want to remove and select **"Exit Validator"**.

![exit-validator](/img/exit-a-validator-2.avif)

3. **Acknowledge Exit confirmation** *([details are here](#summary-and-confirmation))*

![exit-validator](/img/exit-a-validator-5.avif)

4. **Sign a transaction** *([details are here](#transaction-signature))*

<div style={{ display: 'flex', justifyContent: 'center' }}>
  <img 
    src="/img/exit-a-validator-7.png" 
    alt="Deposit SSV" 
    style={{ width: '30%', maxWidth: '500px' }}
  />
</div>

  </TabItem>
  <TabItem value="checklist" label="Checklist">

1. [**In the Clusters page**](https://app.ssv.network/clusters), **select the cluster that has validator** you wish to exit.

2. **Tap the gear icon next to the validator** you want to remove and select **"Exit Validator"**.

3. **Acknowledge Exit confirmation** *([details are here](#summary-and-confirmation))*

4. **Sign a transaction** *([details are here](#transaction-signature))*

  </TabItem>
</Tabs>

5. Check out the [Next Steps](#next-steps)

### Next Steps

Once the transaction has been signed, your validator(s) are scheduled to be exited from the beacon chain.

**Exit confirmation can take from hours to weeks**. [Exit queue](https://www.validatorqueue.com/) dictates the time you have to wait until the validator(s) are fully exited. 

Once the Exit is confirmed by the network, your validator(s) will no longer be considered for validator duties. **Only at this point**, validator(s) can be safely [removed from SSV network](./removing-a-validator.md), without incurring in penalties.

The 32 ETH stake will be available for withdrawal shortly after the Exit is fully complete.

### Summary and Confirmation

:::danger Attention
Exiting your validator signals to the network that you wish to **permanently cease** your validator's participation in the Beacon Chain and **retrieve your 32 ETH stake principal**.

Initiating an exit places your validator in the exit queue. The duration in the queue depends on the number of validators already waiting. During this period, your validator must remain active, so it is crucial to maintain your validator's performance and keep it registered with the SSV network until it has fully exited.
:::

This operation will generate a transaction to the [SSV Network smart contract](../../developers/smart-contracts/ssvnetwork.md#exitvalidatorpublickey-operatorids), and will make sure that the operators in the cluster will sign and execute a voluntary exit of the specified validator(s), on behalf of the validator owner.

<details>

<summary>Examples of Exit Validator confirmations</summary>

- Confirmation for a single validator exit:

![exit-validator](/img/exit-a-validator-5.avif)

- In case of multiple validators, this screen will look like this:

![exit-validator](/img/exit-a-validator-6.avif)

</details>

### Transaction Signature

Validator(s) Exit is finalized by signing the transaction. 

You will need to confirm the transaction in your Web3 wallet.

<details>

<summary>Example of transaction in Metamask</summary>

<div style={{ display: 'flex', justifyContent: 'center' }}>
  <img 
    src="/img/exit-a-validator-7.png" 
    alt="Exit a validator" 
    style={{ width: '50%', maxWidth: '500px' }}
  />
</div>

</details>