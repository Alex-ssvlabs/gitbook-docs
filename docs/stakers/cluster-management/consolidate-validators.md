---
title: Consolidate Validators
sidebar_position: 2
---

# Consolidate Validators

Since Pectra hardfork all validators are allowed to upgrade their withdrawal address to 0x02 and have up to 2048 ETH on validator balance. [Read more about 0x02 and Max Effective balance here](https://www.kiln.fi/post/next-ethereum-upgrade-how-pectra-will-enhance-the-staking-experience).

Consolidation is the process of migrating validator funds from one to another, the final validator has to be 0x02 type to allow >32 ETH on its balance. This process lowers operational costs, while your rewards remain the same. All validators have to have the same withdrawal address to consolidate.

## Upgrade to 0x02 
1. Navigate to the [Ethereum Launchpad’s “Validator Actions” section](https://launchpad.ethereum.org/en/validator-actions)
2. Connect your wallet with withdrawal address
3. Click on `Upgrade account to compounding`
4. Wait until the address upgrade is done, you can monitor on [beaconcha.in](https://beaconcha.in/)

## Consolidate Validators
1. Available once you have at least one validator with 0x02 withdrawal address.
2. Navigate to the [Ethereum Launchpad’s “Validator Actions” section](https://launchpad.ethereum.org/en/validator-actions)
3. Connect your wallet with withdrawal address
4. Click on `Absorb another validator`
5. Consolidated validator will fully exited, the other one will receive it's balance
6. Wait until the consolidated validator is fully exited, you can monitor on [beaconcha.in](https://beaconcha.in/)

## Remove Exited Validators from SSV
Once you're confirmed that consolidated validator is exited, you can proceed with removing it from SSV Network. Follow the [Removing a Validator guide](/stakers/validator-offboarding/removing-a-validator.md) to do that.