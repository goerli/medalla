# Prysm Config for Schlesi v0.11

This document describes how to connect to and participate in the Schlesi testnet using the Prysm ETH2 client. https://github.com/prysmaticlabs/prysm/

### Requirements

This requires Bazel, get it here: https://bazel.build/

_Note:_ Bazel will manage the build and dependencies, for other options, please refer to the Prysm documentation.

To connect to Schlesi v0.11, you would have to compile Prysm from `v0.12` branch. _Right_ --- `v0.12` contains a patch that is necessary for the v0.11 spec. Let's not get confused about the versioning here. :)

In addition, it requires a custom patch for allowing a lower deposit count threshold: [gist/q9f/090f017abba9809f8cf7055aac5ecf16](https://gist.github.com/q9f/090f017abba9809f8cf7055aac5ecf16)

```
git checkout v0.12
wget https://gist.github.com/q9f/090f017abba9809f8cf7055aac5ecf16/raw/fe7385845670e137fabbd77b8e9d22b8ebf9efa2/schlesi.patch
git apply schlesi.patch
```

We'll be working towards adding a Schlesi flag to Prysm in future to ease this process.

Bazel build compiles everything:

```
bazel build //beacon-chain:beacon-chain
bazel build //validator:validator
```

### Beacon Node

Run your patched beacon node:

```
bazel run //beacon-chain -- \
--min-sync-peers 1 \
--contract-deployment-block 2596126 \
--deposit-contract "0xA15554BF93a052669B511ae29EA21f3581677ac5" \
--custom-genesis-delay 3600 \
--bootstrap-node "/ip4/51.15.119.157/tcp/9000/p2p/16Uiu2HAkvLCWwVEfF365ZWXB6siDL1mUpcd1XQ1nSXAHmvM5W7wn,/ip4/51.15.119.157/tcp/13000/p2p/16Uiu2HAmNYCpko7ahZrZrzcpJRjL6bJ3JmPFiCbb9bgR3UHbHBsH"
```

### Validator Deposits

The validator contract is deployed on Goerli testnet address [0xA15554BF93a052669B511ae29EA21f3581677ac5](https://goerli.etherscan.io/address/0xA15554BF93a052669B511ae29EA21f3581677ac5).

To generate a new validator keypair, run:

```
bazel run //validator -- accounts create \
--password="CHANGE-ME"
```

This will output binary data that can be directly sent to the deposit contract along with 32 GöETH, e.g., for the Geth Console: 

```
eth.sendTransaction({from:eth.coinbase, to:"0xA15554BF93a052669B511ae29EA21f3581677ac5", value:32000000000000000000, data:"0xRAW-TRANSACTION-DATA"})
```

### Validator Client

To start validating, open another terminal and launch the validator client:

```
bazel run //validator -- \
--password="CHANGE-ME" \
--graffiti "OMG THANKS SCHLESI\!"
```

Please create an issue if this does not work. We will figure it out: https://github.com/goerli/schlesi/issues/new
