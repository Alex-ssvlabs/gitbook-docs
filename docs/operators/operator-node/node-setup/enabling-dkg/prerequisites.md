---
title: Prerequisites
sidebar_position: 1
---

# Prerequisites

## Minimum requirements

The minimum requirement is an AWS `t3.small` or equivalent machine dedicated to run DKG.&#x20;
The recommend requirement is an AWS `t3.medium` or higher tier machine  ([https://aws.amazon.com/ec2/instance-types/](https://aws.amazon.com/ec2/instance-types/)).

Minimum docker resource allocations:

```yaml
deploy:
  resources:
    limits:
      cpus: "1"
      memory: 500M
```

:::info Please Note
Computational demands are raising depending on amount validators being created at once.
An idle DKG node needs almost none resources.
:::

## Prerequisites

In order to successfully participate in DKG ceremonies initiated by stakers, you will need to possess and/or provide this information:

* **Operator ID** - the ID of your operator within the SSV network.
* **Operator Key Pair**
  * **Public Key** - the public key of the operator&#x20;
  * **Private Key** - the private key of the operator as an password-encrypted file (if you are in possession of raw text private key, follow [this migration guide to encrypt your existing operator keys](/operators/operator-node/maintenance/troubleshooting/#faq))
* **Machine Endpoint** - the endpoint (`protocol:ip:port`,  e.g. `https://my-dkg.com:3030`) of the machine intended to run the `ssv-dkg` client (if you have a domain name, instead of an `ip` that works as well)

:::warning
You **must** **use the same Private and Public Keys** of your SSV operator when running `ssv-dkg` node. Using a different key will result in the inability to successfully complete the DKG ceremony.
:::
