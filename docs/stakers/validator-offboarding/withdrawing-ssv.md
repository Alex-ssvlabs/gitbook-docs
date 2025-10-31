---
title: Withdraw SSV
sidebar_position: 3
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# Withdraw SSV

Make sure to connect your Web3 wallet with the WebApp, and that the address corresponds with the one you want to manage your Validators with.

<Tabs>
  <TabItem value="detailed-guide" label="Detailed Guide">

1. [**In the Clusters page**](https://app.ssv.network/clusters), **select the needed cluster**. Then click on the **"Withdraw"** button.

![withdraw-ssv](/img/withdraw-ssv-1.avif)

2. **Enter the amount of SSV** you want to withdraw.

![withdraw-ssv](/img/withdraw-ssv-2.avif)

3. Please **inspect the updated estimated cluster runway.** Once done, click on the **"Withdraw"** button. 

![withdraw-ssv](/img/withdraw-ssv-3.avif)

4. **Finalize the withdrawal** from the Cluster by **signing the transaction**.
[You can read more here](/developers/smart-contracts/ssvnetwork#withdrawoperatorids-amount-cluster) about `withdraw` method on our smart contract.

<div style={{ display: 'flex', justifyContent: 'center' }}>
  <img 
    src="/img/withdraw-ssv-4.png" 
    alt="Withdraw SSV" 
    style={{ width: '30%', maxWidth: '500px' }}
  />
</div>

5. You'll be taken back to the Cluster page, with the updated SSV token balance.

![withdraw-ssv](/img/withdraw-ssv-5.avif)

  </TabItem>
  <TabItem value="checklist" label="Checklist">

1. [**In the Clusters page**](https://app.ssv.network/clusters), **select the needed cluster**. Then click on the **"Withdraw"** button.

2. **Enter the amount of SSV** you want to withdraw.

3. Once you enter the amount, click on the **"Withdraw"** button. Please take a close **look at the updated estimated cluster runway.**

4. **Finalize the withdrawal** from the Cluster by **signing the transaction**.
[You can read more here](/developers/smart-contracts/ssvnetwork#withdrawoperatorids-amount-cluster) about the `withdraw` method on our smart contract.

5. You'll be taken back to the Cluster page, with the updated SSV token balance.

  </TabItem>
</Tabs>

