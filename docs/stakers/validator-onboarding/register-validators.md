---
description: Register Validators
sidebar_position: 4
---

# Register Validators

## Prerequisites
Before registering validators, make sure you are fully prepared:
- [**Ensure sufficient funds**](./calculate-costs.md) in your wallet to cover validator fees + collateral.
- Gather your **operator IDs** obtained during operator registration.
- Verify your keyshare file.
- **Turn off** previous validator setup.
:::danger Slashing Warning
Make sure the previous validator setup is down before registering validators. Wait for 2–3 epochs to confirm there are **no successful attestations** before proceeding.
:::

## Register Validators
#### Add a Cluster
- Navigate to the [SSV Webapp](http://app.ssv.network).
- **Connect your wallet** → **My Account** → **Validators** → **Add Cluster**.
- On subsequent registration → **Open your existing cluster** → **Add Validator**.

#### Upload Keyshares & Bulk Register
- Select **“I already have key shares”**.
- Upload your keyshares file.
  - The Web App supports **≤ 80 validators per registration**. You will **re-upload the same keyshares file** until all validators are registered:
  - 500 validators → **7 registration batches** (6 × 80 + 1 × 20).
  - 1,000 validators → **13 registration batches** (12 × 80 + 1 × 40).
- Confirm **operator IDs match** your recorded values.
- Check the **validator counts** during each registration.
- Approve funding and register validators batch.


#### Verify First Batch
After registering the first 80 validators, pause and confirm that:
- Validators have resumed attesting.
- Only continue with the remaining uploads once the first batch is healthy.
- No issues are shown in monitoring tools.


#### Repeat Until Complete
- Continue until all validators are registered.
- After completion, click “Manage Validators” to review your setup

## Set the Fee Recipient Address
By default, your own address will be set as Fee Recipient for block proposals. 

Depending on your operations and off-chain arrangements, you might need to change that address. Use the **SSV Docs guide to change the Fee Recipient** ←←←.

## Monitor Validators
Once onboarding is complete, monitor validator performance and cluster health:
- [SSV Explorer](https://explorer.ssv.network/mainnet/overview)
- [SSV Scan](https://ssvscan.io/)
:::info Note
Attestations may take up to 3 epochs to appear after registration.
:::

## Next Steps
Congratulations! Your validators were migrated successfully 🥳.

You can check out [**Post-Migration steps**](../post-migration/README.md) to ensure smooth long-term operations.