# Prysm Config for Schlesi v0.11

This document describes how to connect to and participate in the Schlesi testnet using the Prysm ETH2 client. https://github.com/prysmaticlabs/prysm/

### Requirements

This requires Bazel, get it here: https://bazel.build/

_Note:_ Bazel will manage the build and dependencies, for other options, please refer to the Prysm documentation.

To connect to Schlesi v0.11, you would have to compile Prysm from `v0.12` branch. _Right_ --- `v0.12` contains a patch that is necessary for the v0.11 spec. Let's not get confused about the versioning here. :)

```
git checkout v0.12
```

Bazel build compiles everything:

```
bazel build //beacon-chain:beacon-chain
bazel build //validator:validator
```

### Beacon Node

Run your patched beacon node:

```
bazel run //beacon-chain -- \
--schlesi-testnet \
--min-sync-peers 1 \
--contract-deployment-block 2596126 \
--deposit-contract "0xA15554BF93a052669B511ae29EA21f3581677ac5" \
--peer "/ip4/51.15.119.157/tcp/9000/p2p/16Uiu2HAkvLCWwVEfF365ZWXB6siDL1mUpcd1XQ1nSXAHmvM5W7wn" \
--peer "/ip4/51.15.119.157/tcp/9500/p2p/16Uiu2HAmSUvW1q4yH4QzZGpWHrLvpCzPdufSFex5odbhNj6zDEjQ" \
--peer "/ip4/51.15.119.157/tcp/13000/p2p/16Uiu2HAmNYCpko7ahZrZrzcpJRjL6bJ3JmPFiCbb9bgR3UHbHBsH" \
--peer "/ip4/51.15.119.157/tcp/13500/p2p/16Uiu2HAm37N426LzqRQF7YCo2u7HRCkAGrxPhv4QHxGu6YE51YWJ" \
--bootstrap-node "enr:-LK4QJ-6k6QytxOn7P9BdDZHXesHz3aaglpvo-VcTGc-rfr5H4DBzjQsjg6stZoy1H-p3yK21IISkJHe742QTVwRS_IEh2F0dG5ldHOIAAAAAAAAAACEZXRoMpCZJe_WAAAAAP__________gmlkgnY0gmlwhDMPd52Jc2VjcDI1NmsxoQINdLr6UY7y2CzshX4n_BbdYM1G40rpdEs84Mdoyv_ZyYN0Y3CCIyiDdWRwgiMo" \
--bootstrap-node "enr:-LK4QJS5Rn_kkA2MQpieVDUao5vkBj3kE15S_JJepGA9MNfndwHyfBWSjmAa5T_qvkGklrDiZXqlIAahXTm_eH_IXY8Ch2F0dG5ldHOIAAAAAAAAAACEZXRoMpCZJe_WAAAAAP__________gmlkgnY0gmlwhDMPd52Jc2VjcDI1NmsxoQOS1-hRSwsxLo2PH3RKtwWdjLdT1IMX2nqkQAlHs5E7LIN0Y3CCMsiDdWRwgi7g"
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
