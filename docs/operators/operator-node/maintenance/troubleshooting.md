---
title: Troubleshooting
sidebar_position: 1
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# Troubleshooting

## Overview
This section is designed to arm you with tools to troubleshoot issues with your SSV node:
- [FAQ](#faq) - short answers on the most common questions.
- [Health endpoint](#ssv-node-health-endpoint) - the starting point to troubleshooting your node.
- [SSV-Pulse benchmarking](#ssv-pulse-benchmarking-tool) - powerful tool that will give insight into potential issue source.
- [Common errors](#common-errorwarning-messages) - a list of specific errors with a short explanation on how to fix them.

***

## FAQ

<details>

<summary><strong>How do I update my node?</strong></summary>

**Docker compose:**

Run the following commands to update your node to the latest version:

```
docker compose down
docker pull ssvlabs/ssv-node:latest
docker compose up -d
```

_Alternatively_, you can set the exact version in your `docker-compose.yaml` configuration file with `image: ssvlabs/ssv-node:v1.2.3`. But in that case you will have to change the version in your file with each new update [posted on SSV Docker Hub](https://hub.docker.com/r/ssvlabs/ssv-node/tags).

**Docker run:**

If you followed our documentation, you named your node with the `--name=ssv_node`  docker flag. This is how you will reference your node with other docker commands.

To update your SSV node, you will need to stop your current node:

```bash
docker stop ssv_node
```

Then remove it (this only removes the old Docker image, not all of your data!):

```bash
docker rm -f ssv_node
```

Then pull the latest image from SSV:

```bash
docker pull ssvlabs/ssv-node:latest
```

And finally... [run the creation command again](../node-setup/manual-setup#start-the-node) to create a new Docker container with the latest SSV image.

</details>

<details>

<summary><strong>What happens if my machine restarts?</strong></summary>

If you look at the Docker command you ran to start the node you'll see the part that says:

```bash
--restart unless-stopped
```

This means that the Docker container running your node will always try to restart if it crashes, or if the whole machine turns off and then restarts.

</details>

<details>

<summary><strong>My node is not participating in cluster consensus</strong></summary>

1. Verify that the `network` in config has the correct value for the blockchain you are trying to operate on.

2. Next, verify in the SSV node logs that the connection to execution and beacon nodes has been established.

3. Check correctness of the path to private key/password files. Check the files are correct too, e.g. in your private key there is `pubKey` section - it should be exactly the same as your registered public key of this operator.

4. If the SSV node logs don't report any errors, please verify the clients logs themselves. If the disk they are running on does not support fast IOPS, they might struggle to stay in sync with the blockchain.

5. It is finally possible that the clients don't report any errors, but the issue persists. In this cases, try and re-sync execution and/or beacon client(s), to fix potential initialization issues.

6. If you can't find the reason for this issue, feel free to ask our team for help in our [Discord channel](https://discord.com/invite/ssvnetworkofficial).

</details>

<details>

<summary>How do I start the node?</summary>

If for some reason your node has stopped (maybe you manually stopped it 🤔) you don't need to run the full creation command again, as that will actually throw an error saying that the Docker container already exists.

In the command above, you named your node:

```bash
--name=ssv_node
```

This is how you will reference your node with other docker commands.

To start a container, run the command:

```bash
docker start ssv_node
```

</details>

<details>

<summary>How do I stop the node?</summary>

In the command above, you named your node:

```bash
--name=ssv_node
```

This is how you will reference your node with other docker commands.

To stop the node run:

```bash
docker stop ssv_node
```

</details>

<details>

<summary>How do I view the logs again?</summary>

In the command above, you named your node:

```bash
--name=ssv_node
```

This is how you will reference your node with other docker commands.

To view the logs when your node is running, use the command:

```bash
docker logs ssv_node
```

</details>

<details>

<summary>How do I migrate raw (deprecated) Operator Keys</summary>

If you are already in possession of raw (unencrypted) Operator Keys, please copy the private key into a text file and make sure the file only contains the key in a single line. For this mini-guide, we are going to call this file: `private-key`.

**Password file**

You will need to create a file (named `password` in this example) containing the password you chose for your Secret Key:

```bash
echo "<MY_OPERATOR_PASSWORD>" >> password
```

**Secret Key encryption**

Then, you can generate a KeyStore using this command:

```bash
docker run --name ssv-node-key-generation \
-v "$(pwd)/password":/password \
-v "$(pwd)/private-key":/private-key \
-it ssvlabs/ssv-node:latest /go/bin/ssvnode generate-operator-keys \
--password-file=/password  --operator-key-file=/private-key && \
docker cp ssv-node-key-generation:/encrypted_private_key.json \
./encrypted_private_key.json && \
docker rm ssv-node-key-generation
```

**Configuration update**

At this point the node configuration needs to be changed, please edit the `config.yaml` file for your node, find the line with `OperatorPrivateKey` and delete it entirely. Replace it with this section:

```yaml
KeyStore:
  PrivateKeyFile: <ENCRYPTED_PRIVATE_KEY_JSON> # e.g. ./encrypted_private_key.json
  PasswordFile: <PASSWORD_FILE> # e.g. ./password
```

And make sure to replace `ENCRYPTED_PRIVATE_KEY_JSON` with the operator encrypted private key file just generated (e.g. `encrypted_private_key.json`) and `PASSWORD_FILE` with the file containing the password used to generate the encrypted key itself (e.g. `password`).

**Restart node and apply new configuration**

The node needs to be restarted, in order for the new configuration to be applied. Please connect to the machine running the node via terminal and execute the command:

```bash
docker stop ssv_node && docker rm ssv_node && docker run -d --restart unless-stopped --name ssv_node -e \
CONFIG_PATH=/config.yaml -p 13001:13001 -p 12001:12001/udp -p 15000:15000 \
-v "$(pwd)/config.yaml":/config.yaml \
-v "$(pwd)":/data \
-v "$(pwd)/password":/password \
-v "$(pwd)/encrypted_private_key.json":/encrypted_private_key.json \
-it "ssvlabs/ssv-node:latest" make BUILD_PATH="/go/bin/ssvnode" start-node && \ 
docker logs ssv_node --follow
```
</details>

## SSV Node health endpoint

To use this endpoint you'll first need to configure and open a specific port:
1. By default, you can use port `16000`.
2. *If* you want to use another port:
    - In `.yaml` configuration file you can edit  `SSVAPIPort: 16000` and restart to apply.
    - In `.env` configuration file you can edit `SSV_API=16000` variable and restart to apply.
3. Make sure your SSV node/container has `16000` port opened (or other port you chose).

The health check endpoint can be reached using the `curl` command, for example:

```bash
curl http://localhost:16000/v1/node/health
```

<details>

<summary>How to understand the results?</summary>

This request will provide a JSON response. Here is an example of response from **healthy node**:

```json
{
  "p2p": "good",
  "beacon_node": "good",
  "execution_node": "good",
  "event_syncer": "good",
  "advanced": {
    "peers": 19,
    "inbound_conns": 7,
    "outbound_conns": 17,
    "p2p_listen_addresses": [
      "tcp://<X.Y.W.Z>:13001",
      "udp://<X.Y.W.Z>:12001"
    ]
  }
}
```

This "self-diagnose" report of the node can be useful to make sure that some essential indicators have the correct values:

* `p2p_listen_addresses` should show the correct public IP & port and the TCP port should be open when checking this IP with a port checker (they have been rendered anonymous for the purpose of this page)
* `peers` should be at least 15 for operators with more than 100 validators
* `inbound_conns` should be at least 20% of the peers (though not an exact number, this is a good indication of healthy connections from the node)

Below, an example of the same report, from a **node in bad state**:

```json
{
  "p2p": "bad: not enough connected peers",
  "beacon_node": "good",
  "execution_node": "good",
  "event_syncer": "good",
  "advanced": {
    "peers": 5,
    "inbound_conns": 0,
    "outbound_conns": 4,
    "p2p_listen_addresses": [
      "tcp://<X.Y.W.Z>:13004",
      "udp://<X.Y.W.Z>:12004"
    ]
  }
}
```
</details>

## SSV-Pulse benchmarking tool

**Before using this tool** make sure to open [SSV Node Health Endpoint](#ssv-node-health-endpoint).

Benchmark analyzes SSV, Consensus, and Execution Nodes at the same time. If curious, you can find more details on [ssv-pulse GitHub page](https://github.com/ssvlabs/ssv-pulse).

To use this tool you can use docker compose or a docker command below:
<Tabs>
  <TabItem value="docker-compose" label="docker compose">

If you used docker compose to run your SSV node — add the following part after the `services:` to your `docker-compose.yml` file:

```yaml
services:
  ssv-pulse:
    container_name: ssv-pulse
    image: ghcr.io/ssvlabs/ssv-pulse:latest
    command: 
      - 'benchmark'
      - '--consensus-addr=<YOUR_ADDRESS_HERE>' # Change to Consensus Node's address, e.g. http://lighthouse:5052
      - '--execution-addr=<YOUR_ADDRESS_HERE>' # Change to Execution Node's address, e.g. http://geth:8545
      - '--ssv-addr=<YOUR_ADDRESS_HERE>' # Change to SSV Node's address, e.g. http://ssv_node:16000
      - '--duration=60m'
      # - '--network=holesky' # Add this if you run a Holesky Node
      # - '--platform linux/arm64' # Add this if you run on an arm64 machine
    networks:
      - host # This allows ssv-pulse to access any docker container hosted on the machine
            # Alternatively, you can use your existing network instead. Check with docker network ls.
    pull_policy: always
```

Then run `docker compose up ssv-pulse` to run the benchmark tool.

  </TabItem>
  <TabItem value="docker-run" label="docker run">

  Use the following command to run the benchmark tool:

  ```bash
  docker run --rm --network=host --pull=always --name ssv-pulse \
  ghcr.io/ssvlabs/ssv-pulse:latest benchmark \
  --consensus-addr=REPLACE_WITH_ADDR \
  --execution-addr=REPLACE_WITH_ADDR \
  --ssv-addr=REPLACE_WITH_ADDR \
  --duration=60m
  ```

  Replace the various addresses with the respective endpoints, e.g. `http://lighthouse:5052`, `http://geth:8545`, and SSV `http://ssv_node:16000` (or your other SSVAPIPort).

  - If you run a Holesky Node you should add `--network=holesky` to the command.
  - If you run this on a arm64 machine you should add `--platform linux/arm64` to the command.
  </TabItem>
</Tabs>

<details>

<summary><strong>Beware the benchmark results</strong></summary>

The tool will run for 1 hour and provide you with results as a table.

:::warning Please note
Use the `Value` column as the ultimate validation tool. Don't just look at the `Health` column, as this can sometimes be misleading. 
:::

Let's look at example below. `Unhealthy` statuses on SSV and Execution are there because minimum peer value was 0, that is likely due to restart right before running the benchmark. p50 values are completely normal, so this is a false alarm:
```log
┌────────────────┬─────────────┬──────────────────────────────────────────────────────────┬────────────┬──────────────────────────────────────────────────────────┐
│   Group Name   │ Metric Name │                          Value                           │   Health   │                         Severity                         │
├────────────────┼─────────────┼──────────────────────────────────────────────────────────┼────────────┼──────────────────────────────────────────────────────────┤
│   Consensus    │   Client    │          Lighthouse/v5.3.0-d6ba8c3/x86_64-linux          │ Healthy✅  │                      Version: None                       │
├────────────────┼─────────────┼──────────────────────────────────────────────────────────┼────────────┼──────────────────────────────────────────────────────────┤
│   Consensus    │   Latency   │ min=63.301µs, p10=99.168µs, p50=147.59µs, p90=386.902µs, │ Healthy✅  │ DurationMin: None, DurationP10: None, DurationP50: None, │
│                │             │                      max=1.697228ms                      │            │           DurationP90: None, DurationMax: None           │
├────────────────┼─────────────┼──────────────────────────────────────────────────────────┼────────────┼──────────────────────────────────────────────────────────┤
│   Consensus    │    Peers    │        min=98, p10=100, p50=104, p90=110, max=110        │ Healthy✅  │                       Count: None                        │
├────────────────┼─────────────┼──────────────────────────────────────────────────────────┼────────────┼──────────────────────────────────────────────────────────┤
│   Consensus    │ Attestation │     missed_attestations=0, unready_blocks_200_ms=0,      │ Healthy✅  │ Correctness: None, MissedBlock: None, FreshAttestation:  │
│                │             │                     missed_blocks=2                      │            │                None, ReceivedBlock: None                 │
│                │             │       fresh_attestations=294 received_blocks=294,        │            │                                                          │
│                │             │                   correctness=100.00 %                   │            │                                                          │
├────────────────┼─────────────┼──────────────────────────────────────────────────────────┼────────────┼──────────────────────────────────────────────────────────┤
│   Execution    │    Peers    │          min=0, p10=50, p50=50, p90=50, max=50           │ Unhealthy⚠️ │                       Count: High                        │
├────────────────┼─────────────┼──────────────────────────────────────────────────────────┼────────────┼──────────────────────────────────────────────────────────┤
│   Execution    │   Latency   │ min=63.362µs, p10=96.627µs, p50=146.984µs, p90=382.03µs, │ Healthy✅  │ DurationP10: None, DurationP50: None, DurationP90: None, │
│                │             │                      max=1.672445ms                      │            │           DurationMax: None, DurationMin: None           │
├────────────────┼─────────────┼──────────────────────────────────────────────────────────┼────────────┼──────────────────────────────────────────────────────────┤
│      SSV       │    Peers    │          min=0, p10=27, p50=28, p90=30, max=31           │ Unhealthy⚠️ │                       Count: High                        │
├────────────────┼─────────────┼──────────────────────────────────────────────────────────┼────────────┼──────────────────────────────────────────────────────────┤
│      SSV       │ Connections │      inbound_min=0, inbound_P50=20, outbound_min=0,      │ Unhealthy⚠️ │   InboundConnections: High, OutboundConnections: High    │
│                │             │                      outbound_P50=9                      │            │                                                          │
├────────────────┼─────────────┼──────────────────────────────────────────────────────────┼────────────┼──────────────────────────────────────────────────────────┤
│ Infrastructure │     CPU     │   user_P50=8.37%, system_P50=1.06%, total=17826400938    │ Healthy✅  │                 System: None, User: None                 │
├────────────────┼─────────────┼──────────────────────────────────────────────────────────┼────────────┼──────────────────────────────────────────────────────────┤
│ Infrastructure │   Memory    │        total_P50=31978.74MB, used_P50=27604.35MB,        │ Healthy✅  │    Used: None, Free: None, Total: None, Cached: None     │
│                │             │         cached_P50=3264.24MB, free_P50=493.46MB          │            │                                                          │
└────────────────┴─────────────┴──────────────────────────────────────────────────────────┴────────────┴──────────────────────────────────────────────────────────┘
```

Another example where `Unhealthy` **is actually accurate**. You can see low Peer connection on SSV Node, this most likely caused by closed 16000 port:

```log
┌────────────────┬─────────────┬──────────────────────────────────────────────────────────────┬────────────┬───────────────────────────────────────────────────────────┐
│   Group Name   │ Metric Name │                            Value                             │   Health   │                         Severity                          │
├────────────────┼─────────────┼──────────────────────────────────────────────────────────────┼────────────┼───────────────────────────────────────────────────────────┤
│ Infrastructure │     CPU     │     user_P50=13.54%, system_P50=1.80%, total=87903220930     │ Healthy✅  │                 System: None, User: None                  │
├────────────────┼─────────────┼──────────────────────────────────────────────────────────────┼────────────┼───────────────────────────────────────────────────────────┤
│ Infrastructure │   Memory    │         total_P50=128580.05MB, used_P50=54250.51MB,          │ Healthy✅  │     Cached: None, Used: None, Free: None, Total: None     │
│                │             │          cached_P50=66262.48MB, free_P50=4250.07MB           │            │                                                           │
├────────────────┼─────────────┼──────────────────────────────────────────────────────────────┼────────────┼───────────────────────────────────────────────────────────┤
│   Consensus    │   Client    │ teku/v24.10.0/linux-x86_64/-eclipseadoptium-openjdk64bitser- │ Healthy✅  │                       Version: None                       │
│                │             │                        vervm-java-21                         │            │                                                           │
├────────────────┼─────────────┼──────────────────────────────────────────────────────────────┼────────────┼───────────────────────────────────────────────────────────┤
│   Consensus    │   Latency   │        min=415.643µs, p10=720.518µs, p50=2.856258ms,         │ Healthy✅  │                      Duration: None                       │
│                │             │               p90=3.519113ms, max=595.473628ms               │            │                                                           │
├────────────────┼─────────────┼──────────────────────────────────────────────────────────────┼────────────┼───────────────────────────────────────────────────────────┤
│   Consensus    │    Peers    │         min=276, p10=287, p50=299, p90=300, max=300          │ Healthy✅  │                        Count: None                        │
├────────────────┼─────────────┼──────────────────────────────────────────────────────────────┼────────────┼───────────────────────────────────────────────────────────┤
│   Consensus    │ Attestation │       missed_attestations=0, unready_blocks_200_ms=0,        │ Healthy✅  │ Correctness: None, ReceivedBlock: None, FreshAttestation: │
│                │             │                       missed_blocks=1                        │            │                  None, MissedBlock: None                  │
│                │             │         fresh_attestations=296 received_blocks=297,          │            │                                                           │
│                │             │                     correctness=99.66 %                      │            │                                                           │
├────────────────┼─────────────┼──────────────────────────────────────────────────────────────┼────────────┼───────────────────────────────────────────────────────────┤
│   Execution    │    Peers    │         min=232, p10=238, p50=245, p90=250, max=253          │ Healthy✅  │                        Count: None                        │
├────────────────┼─────────────┼──────────────────────────────────────────────────────────────┼────────────┼───────────────────────────────────────────────────────────┤
│      SSV       │    Peers    │            min=0, p10=0, p50=0, p90=0, max=0                 │ Unhealthy⚠️ │                        Count: High                        │
├────────────────┼─────────────┼──────────────────────────────────────────────────────────────┼────────────┼───────────────────────────────────────────────────────────┤
│      SSV       │ Connections │        inbound_min=0, inbound_P50=0, outbound_min=0,         │ Unhealthy⚠️ │    OutboundConnections: High, InboundConnections: High    │
│                │             │                       outbound_P50=0                        │            │                                                           │
└────────────────┴─────────────┴──────────────────────────────────────────────────────────────┴────────────┴───────────────────────────────────────────────────────────┘
```
</details>

## Common error/warning messages

This section is a collection of common warnings, error messages, statuses and other unexpected behaviours you might encounter and the possible related known causes.

### `failed to create beacon go-client`

```bash
FATAL	failed to create beacon go-client	{"error": "failed to create http client: failed to confirm node connection: failed to fetch genesis: failed to request genesis: failed to call GET endpoint: Get \"http://5.104.175.133:5057/eth/v1/beacon/genesis\": context deadline exceeded", "errorVerbose":…………….\nfailed to create http client", "address": "http://5.104.175.133:5057"}
```

This is likely due to issues with the Beacon layer Node. Verify that `BeaconNodeAddr` has the correct address and port in [`config.yaml` configuration file](../node-setup/manual-setup#create-configuration-file).

***

### `could not connect to execution client`

```bash
FATAL	could not connect to execution client	{"error": "failed to connect to execution client: dial tcp 5.104.175.133:8541: i/o timeout"}
```

This is likely due to issues with the Execution layer Node. Verify that `ETH1Addr` has the correct address and port in [`config.yaml` configuration file](../node-setup/manual-setup#create-configuration-file).

Finally, make sure that your ETH1 endpoint is running using Websocket. This is required in order to stream events from the network contracts.

***

### `could not setup operator private key`

```bash
FATAL	could not setup operator private key	{"error": "Operator private key is not matching the one encrypted the storage", "errorVerbose": ...{
```

Verify that the Operator Private Key is correctly set in [`config.yaml` configuration file](../node-setup/manual-setup#create-configuration-file). In particular, if using unencrypted (raw) keys, that the **private (secret) key** was copied in the configuration file and that it contains all characters (sometimes it contains a  `=`  character that can easily be left out).

If the node has been stopped and restart, verify that the same configuration has been applied, that the private key has not been changed, and that the `db.Path` configuration points to the same directory as before.

***

### `could not setup network`

```bash
FATAL	could not setup network	{"error": "network not supported: jatov2"}
```

In the example above, the `Network` in [`config.yaml` configuration file](../node-setup/manual-setup#create-configuration-file) was wrongly set to `jatov2` instead of `jato-v2`, so be sure to look for thinks like spelling mistakes.

***

### `could not create loggerlogging.SetGlobalLogger`

```bash
could not create loggerlogging.SetGlobalLogger: unrecognized level: "infor"
make: *** [Makefile:97: start-node] Error 1
```

In the example above, the `LogLevel` variable in [`config.yaml` configuration file](../node-setup/manual-setup#create-configuration-file) was wrongly set to `infor` instead of `info`, so be sure to look for thinks like spelling mistakes.

***

### `failed to get attestation data`

```bash
"error":"could not start committee duty: failed to get attestation data: failed to get attestation data: failed to call GET endpoint\nGet 
```

This error could be caused by using multiple SSV nodes within one Nimbus setup. It is advised to only run one SSV node per Nimbus instance.

***

### `ERROR P2PNetwork`

```bash
ERROR P2PNetwork unable to create external multiaddress {"error": "invalid ip address provided: ...
```

This error signalizes the node could not figure the public IP address of your node on a startup. You need to provide your SSV Node's address in `p2p: HostAddress:` variable in [your `config.yaml` file.](../node-setup/manual-setup#peer-to-peer-ports-configuration-and-firewall)

***

### Node Metrics not showing up in Prometheus/Grafana

Please verify that the `MetricsAPIPort` variable is correctly set in [`config.yaml` configuration file](../node-setup/manual-setup#create-configuration-file).

For a more in-depth guide on how to set up Node monitoring, refer to [the dedicated page in this section](../monitoring).

***

### Node does not generate a log file

Please verify that the `LogFilePath` variable is correctly set in [`config.yaml` configuration file](../node-setup/manual-setup#create-configuration-file). Be sure to look for thinks like spelling mistakes.

***

### Node takes a long time to become active

Please verify that the `Path` under the `db` section is correctly set in [`config.yaml` configuration file](../node-setup/manual-setup#create-configuration-file). Be sure to look for thinks like spelling mistakes.

If the Node was working correctly and becomes inactive after a configuration change, make sure that `Path` wasn't accidentally changed. This will cause the database to be recostructed and will lead to a slower startup.

***

### `"no indices, duties won't be fetched"` message

This could be due to one of the following causes:

1. No validator has chosen your operator as one of its operators (for testing purposes you can always open one and select yourself as one of its managing operators).
2. Your node uses a different operator public key than the one you have registered to the network (using the SSV webapp).

Steps to confirm you use the same key:

1. Find the operator key that you have registered to the network in the [ssv explorer](https://explorer.ssv.network/).
2. Find the operator public key you have generated in your node during setup.
3. Compare between the keys -  if they do not match you must update your private key in the node config.yaml file, according to the key generated during your node node-setup/manual-setup#create-configuration-file.

:::info
Example log output showing the public key:
```json
{
  "level": "info",
  "time": "2021-12-13T06:45:14.466457Z",
  "caller": "operator/storage.go:122",
  "message": "setup operator privateKey is DONE!",
  "app": "SSV-Node:v0.1.7",
  "who": "operatorKeys",
  "public-key": "LS0tLS1CRUdJTiBSU0EgUFVCTElDIEtFWS0tLS0tCk1JSUJJakFOQmdrcWhraUc5dzBCQVFFRkFBT0NBUThBTUlJQkNnS0NBUUVBOHRXRG0xbTNtYW5Ra0xweVpLMzcKMGNHRGoydlBTWStRWVFBd3BWOXZpWThKVlgzT2J0VjNLL24xNy9peGZ2VEx5aGZKckgzYStpS1NIcDl5WEU4cQp6N2RhOTlaVzU4RzAyeDF0ZnpuV1REMmFpbklpMDAwdjQ5RjFTdzlYOUttQUg5VzNGdjBaREpadzZKVFd3R0ZiCmZiTmM2cGVvTG5ucnllWlVXb09ZQms0TVg2Um9QV2ZXNUJEaURaeHFqVjdvbFV3ZnFBMW5OeU96RXFCMEtkSW8KbExSZFA4ODZBNFJrZGpjUDc5aWdrM0RjVVdCMDhpZlM4SFlvS012ZUZrek0yR2dmOG5LRnFmSnFYNzlybFR4cApSTnlheUZOYXhZWEY4enBBMHlYRGFHQ0I1TitzZ1N2Yjg1WDAydWVCa1NadFFUMUMyTGMxWlZkbERFZVpGNFNlCkh3SURBUUFCCi0tLS0tRU5EIFJTQSBQVUJMSUMgS0VZLS0tLS0K"
}
```
:::

:::info
Didn't find the answer you are looking for? Reach out to other network operators on our [Discord channel](https://discord.gg/ssvnetworkofficial)
:::

[^1]: 
