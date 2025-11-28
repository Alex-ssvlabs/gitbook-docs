---
title: DKG Operator Migration
sidebar_position: 4
---

If you need to migrate the DKG operator node to a different machine, follow the procedure described below.

### Procedure

It is advised to shut down the current setup, before launching the new one.

The recommended migration process summary:

1. [Backup DKG files](#dkg-backup)
2. Copy the files to the new machines
3. On the current machine, shut down DKG operator
4. On the new machine, [start DKG operator](/operators/operator-node/setup-sidecars/enabling-dkg/start-dkg-node/)
5. [Update operator metadata on the SSV WebApp](/operators/operator-node/setup-sidecars/enabling-dkg/final-steps#update-operator-metadata)

:::info Please note
DKG node does *not* have to be on the same machine as the SSV node. One can be migrated without having to migrate the other.
:::

### DKG backup

You most likely have (at least) the files below, if you have followed [the dedicated guide to enable DKG for your operator](/operators/operator-node/setup-sidecars/enabling-dkg/start-dkg-node/).

Usually, the folder with your node configuration will look as follows:

```
⇒   tree .
.
├── config.yaml
├── debug.log
├── encrypted_private_key.json
├── output
... (could be multiple ceremony folders)
│   └── ceremony-<DATE>--<TIME>--<RANDOM_ID>
│       └── NONCE-<PUBKEY>
│           ├── deposit_data.json
│           ├── keyshares.json
│           └── proofs.json
└── password
```

**What you need to copy over to the new machine:**
- [Operator keys](#operator-keys) - strictly required.
- [Configuration file](#configuration-file) - neccessary, useful.
- [Ouput folder](#output-folder-optional) - optional.

#### Operator keys

Similarly to the SSV Node, Operator keys are a vital requirement to run the DKG operator server, as they the link that connects it to the SSV node itself.

The files are `encrypted_private_key.json` and `password` in the snippet above, and the filenames should be the same for you.

#### Configuration file

The configuration file (`config.yaml` in the code snippet above), is necessary for the DKG operator to work. You can copy the old configuration file and use it as a template, making sure to change any parameter that needs changing, such as paths to the Operator Keys.

#### Output folder (optional)

The output folder represents the product of various DKG ceremonies the operator node was involved in. These files can be thought as "traces" or debug artefacts.

They are useful, and it could be convenient to have a backup as well, but it is not mandatory, and the DKG operator node will not lose any of its functionality if this was not done.