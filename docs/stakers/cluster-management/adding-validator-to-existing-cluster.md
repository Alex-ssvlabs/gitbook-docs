---
title: Add More Validators
sidebar_position: 1
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# Add Validator to Existing Cluster

Make sure to connect your Web3 address/wallet with the WebApp. Use the address you registered your validators with.

<Tabs>
  <TabItem value="detailed-guide" label="Detailed Guide">

1. [**In the Clusters page**](https://app.ssv.network/clusters), **select an active cluster** and then click on the "**+ Add Validator**" button.

![add-validator-to-cluster](/img/add-validator-to-cluster-1.avif)

2. You'll be asked how do you want to **handle operational costs**, in regards to your existing cluster balance.

![add-validator-to-cluster](/img/add-validator-to-cluster-2.webp)

3. **Generate KeyShares** via SSV Keys CLI command or other means. If unsure, refer to [this step-by-step guide](/stakers/validator-onboarding/split-keys.md).

![add-validator-to-cluster](/img/add-validator-to-cluster-6.avif)

<details>

<summary>Key Splitting on Testnet</summary>

On Testnet, this can be done Online, directly on the WebApp, or Offline on your computer.

![add-validator-to-cluster](/img/add-validator-to-cluster-3.avif)

:::warning Online Splitting
**Online splitting is not considered safe** and is only available on testnet for testing purposes.

Please never perform a Online key splitting on testnet, with a private key that you intend to use on mainnet.
:::

If the Online option is chosen, the next screen allows you to upload the Validator key (file named keystore) and enter the password to decrypt it.

![add-validator-to-cluster](/img/add-validator-to-cluster-5.avif)

</details>


4. **Upload the generated `keyshares-[DATE]-[TIME].json` file**.

![add-validator-to-cluster](/img/add-validator-to-cluster-7.avif)

5. **If the upload is successful click on "Next".**

   If you see an error such as "Keyshares are invalid", most often it is caused by incorrect nonce. Try to generate KeyShares once again, refer to [this step-by-step guide](/stakers/validator-onboarding/split-keys.md).

![add-validator-to-cluster](/img/add-validator-to-cluster-8.avif)

6. The following screen is a **Slashing warning**, [explained in details here](#slashing-warning).

![add-validator-to-cluster](/img/add-validator-to-cluster-9.avif)

7. The next screen presents a summary of your validator setup. Confirm everything is correct and click on "Register Validator".   
More [details about the summary are here](#validator-summary).

![add-validator-to-cluster](/img/add-validator-to-cluster-10.avif)

8. Finalize the validator registration by signing the transaction and adding SSV tokens to your account balance.

<div style={{ display: 'flex', justifyContent: 'center' }}>
  <img 
    src="/img/add-validator-to-cluster-12.png" 
    alt="Distribute a validator" 
    style={{ width: '30%', maxWidth: '500px' }}
  />
</div>

9. Once the transaction has been signed and confirmed by the network, you'll be presented with the summary screen.
**Congratulations! You're all set!🥳**

![add-validator-to-cluster](/img/add-validator-to-cluster-14.avif)

  </TabItem>
  <TabItem value="checklist" label="Checklist">

1. [**In the Clusters page**](https://app.ssv.network/clusters), **select an active cluster** and then click on the **"+ Add Validator"** button.

2. You'll be asked how do you want to **handle operational costs**, in regards to your existing cluster balance.

3. **Generate KeyShares** via SSV Keys CLI command or other means. If unsure, refer to [this step-by-step guide](/stakers/validator-onboarding/split-keys.md).

<details>

<summary>Key Splitting on Testnet</summary>

On Testnet, this can be done Online, directly on the WebApp, or Offline on your computer.

![add-validator-to-cluster](/img/add-validator-to-cluster-3.avif)

:::warning Online Splitting
**Online splitting is not considered safe** and is only available on testnet for testing purposes.

Please never perform a Online key splitting on testnet, with a private key that you intend to use on mainnet.
:::

If the Online option is chosen, the next screen allows you to upload the Validator key (file named keystore) and enter the password to decrypt it.

![add-validator-to-cluster](/img/add-validator-to-cluster-5.avif)

</details>

4. **Upload the generated `keyshares-[DATE]-[TIME].json` file**.

5. **If the upload is successful click on "Next"**.

   If you see an error such as "Keyshares are invalid", most often it is caused by incorrect nonce. Try to generate KeyShares once again, refer to [this step-by-step guide](/stakers/validator-onboarding/split-keys.md).

6. The following screen is a **Slashing warning**, [explained in details here](#slashing-warning).

7. The next screen presents a **summary of your validator setup**. Confirm everything is correct and click on "Register Validator".   
More [details about the summary are here](#validator-summary).

8. **Finalize the validator registration by signing the transaction** and adding SSV tokens to your account balance.

9. Once the transaction has been signed and confirmed by the network, you'll be presented with the summary screen.
**Congratulations! You're all set!🥳**

  </TabItem>
</Tabs>

### Slashing warning

The warning alerts you of the potential dangers of registering a validator on the SSV network. If the same set of validator keys is also being used by other consensus and validator clients your validators can be slashed.

**Please make sure to stop any other running validator setup**, if you have any. 

### Validator summary

By clicking on Register validator, you'll be proposed to sign transactions to confirm your choice and transfer the SSV balance necessary to cover for the operational costs.

:::info
**Note:** If this is the first time you are registering a validator to ssv.network, you will be required to make two transactions - one to approve the SSV smart contract and another one to register the validator.
:::

![add-validator-to-cluster](/img/add-validator-to-cluster-10.avif)