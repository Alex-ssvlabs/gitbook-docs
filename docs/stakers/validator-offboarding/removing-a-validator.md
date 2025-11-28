---
title: Remove a Validator
sidebar_position: 2
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# Remove a Validator

Make sure to connect your Web3 address/wallet with the WebApp. Use the address you registered your validators with.

### Bulk Removal

If a cluster is managing more than one validator, it is possible to select multiple validators at once.

<Tabs>
  <TabItem value="detailed-guide" label="Detailed Guide">

1. [**In the Clusters page**](https://app.ssv.network/clusters), **select the cluster that has validators you wish to remove**.

![remove-validator](/img/remove-a-validator-1.avif)

2. Click the **Actions** dropdown on top of the validators table. Select **Remove validators**.

![remove-validator](/img/remove-a-validator-3.webp)

3. In the following screen, you can **select the validators you want to remove**. When ready, press the **Next** button.

![remove-validator](/img/remove-a-validator-4.webp)

4. **Acknowledge Removal confirmation** *([details are here](#inactivity-penalties-warning))*

![remove-validator](/img/remove-a-validator-5.webp)

5. **Sign a transaction** *([details are here](#transaction-signature))*

<div style={{ display: 'flex', justifyContent: 'center' }}>
  <img 
    src="/img/remove-a-validator-6.png" 
    alt="Deposit SSV" 
    style={{ width: '30%', maxWidth: '500px' }}
  />
</div>

  </TabItem>
  <TabItem value="checklist" label="Checklist">

1. [**In the Clusters page**](https://app.ssv.network/clusters), **select the cluster that has validators you wish to remove**.

2. Click the **Actions** dropdown on top of the validators table. Select **Remove validators**.

3. In the following screen, you can **select the validators you want to remove**. When ready, press the **Next** button.

4. **Acknowledge Removal confirmation** *([details are here](#inactivity-penalties-warning))*

5. **Sign a transaction** *([details are here](#transaction-signature))*

  </TabItem>
</Tabs>

6. **Check out the** [**Next Steps**](#next-steps)

### Single Validator Removal

<Tabs>
  <TabItem value="detailed-guide" label="Detailed Guide">

1. [**In the Clusters page**](https://app.ssv.network/clusters), **select the cluster that has validator you wish to remove**.

![remove-validator](/img/remove-a-validator-1.avif)

2. **Tap the gear icon next to the validator** you want to remove and select "Remove Validator".

![remove-validator](/img/remove-a-validator-2.webp)

3. **Acknowledge Removal confirmation** *([details are here](#inactivity-penalties-warning))*

![remove-validator](/img/remove-a-validator-5.webp)

4. **Sign a transaction** *([details are here](#transaction-signature))*

<div style={{ display: 'flex', justifyContent: 'center' }}>
  <img 
    src="/img/remove-a-validator-6.png" 
    alt="Deposit SSV" 
    style={{ width: '30%', maxWidth: '500px' }}
  />
</div>

  </TabItem>
  <TabItem value="checklist" label="Checklist">

1. [**In the Clusters page**](https://app.ssv.network/clusters), **select the cluster that has validator you wish to remove**.

2. **Tap the gear icon next to the validator** you want to remove and select "Remove Validator".

3. **Acknowledge Removal confirmation** *([details are here](#inactivity-penalties-warning))*

4. **Sign a transaction** *([details are here](#transaction-signature))*

  </TabItem>
</Tabs>

5. **Check out the** [**Next Steps**](#next-steps)

### Next Steps

Once the transaction has been signed and confirmed by the network, your validator will have been successfully removed from the cluster and no longer handled by operators on the SSV network.

**If you removed all validators from the cluster**, you can safely [Withdraw SSV](./withdrawing-ssv.md) from this empty cluster.

### Inactivity penalties warning

:::warning
This will cause the validator to go offline. If you're planning to migrate and not exit - it is advised to have an alternative validator setup ready to continue operating outside ssv.network, [as explained here](/learn/network-overview/validators/validator-offboarding).

Removing the validator is **NOT** reversible, the validator will have to be registered anew on the ssv.network, should you intend to join again.
:::

The following screen alerts you of the implications of removing the validator from the cluster.

When you are ready, check the box and click the "Remove Validator" button.

<details>

<summary>Example of a removal confirmation</summary>

![remove-validator](/img/remove-a-validator-5.webp)

</details>

### Transaction Signature

Validator(s) removal is finalized by signing the transaction.

You will need to confirm the transaction in your web3 wallet.

<details>

<summary>Example of transaction in Metamask</summary>

<div style={{ display: 'flex', justifyContent: 'center' }}>
  <img 
    src="/img/remove-a-validator-6.png" 
    alt="Remove a validator" 
    style={{ width: '50%', maxWidth: '500px' }}
  />
</div>

![remove-validator](/img/remove-a-validator-7.webp)

</details>