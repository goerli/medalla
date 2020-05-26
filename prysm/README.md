# Prysm Config for Witti v0.11.3
This document describes how to connect to and participate in the Witti testnet using the Prysm ETH2 client. [github.com/prysmaticlabs/prysm](https://github.com/prysmaticlabs/prysm/)

### Requirements
This requires Bazel, get it here: [bazel.build](https://bazel.build/)

_Note:_ Bazel will manage the build and dependencies, for other options, please refer to the Prysm documentation. [prysmaticlabs.gitbook.io/prysm](https://prysmaticlabs.gitbook.io/prysm/)

To connect to Witti v0.11.3, you would have to compile Prysm from the `witti` branch. See https://github.com/prysmaticlabs/prysm/tree/witti
```
git clone https://github.com/prysmaticlabs/prysm.git
cd prysm/
git checkout witti
```

Bazel `build` compiles everything.
```
bazel build //beacon-chain:beacon-chain
bazel build //validator:validator
```

### Beacon Node
Run your beacon node.
```
bazel run //beacon-chain -- \
--witti-testnet \
--web3provider ws://127.0.0.1:8546 \
--min-sync-peers 1 \
--bootstrap-node "enr:-Ku4QMucba73OPBz2mgyYduH1tM50mZjaiLNEXMrEmTSnrgyEWMEF0zFK0QT6URu_wFfqW04gYn1wze-VQe-jb0L8r8Bh2F0dG5ldHOIAAAAAAAAAACEZXRoMpD1pf1CAAAAAP__________gmlkgnY0gmlwhFzAVJaJc2VjcDI1NmsxoQIX4kyr2PR-bGTptaN9DbXa2A2L_rVfuIpMj7sCjPBov4N1ZHCCW8w" \
--bootstrap-node "enr:-Ku4QJsxkOibTc9FXfBWYmcdMAGwH4bnOOFb4BlTHfMdx_f0WN-u4IUqZcQVP9iuEyoxipFs7-Qd_rH_0HfyOQitc7IBh2F0dG5ldHOIAAAAAAAAAACEZXRoMpD1pf1CAAAAAP__________gmlkgnY0gmlwhLAJM9iJc2VjcDI1NmsxoQL2RyM26TKZzqnUsyycHQB4jnyg6Wi79rwLXtaZXty06YN1ZHCCW8w" \
--bootstrap-node "enr:-Ku4QF5CI2Ndig0cxR0fQjRolG1k6TggK0BV4Z5neog4U9LDYsTHz6Vv6qVyJ7b9L2r6S2Gu4Ek4Z7i7j-jAJBxHbmYBh2F0dG5ldHOIAAAAAAAAAACEZXRoMpD1pf1CAAAAAP__________gmlkgnY0gmlwhFe0zw-Jc2VjcDI1NmsxoQPD9aDKsFoUfpEMPuTgZ13qNsJZ31zMMrl3PsQXeX2cwYN1ZHCCW8w" \
--bootstrap-node "enr:-Ku4QLE_fTEjP6K3OII1RYRLUMUbwV9dAh7-2vr7gkZnRXLxSy2B6C-b0nVVQcFYsUvp2Tgli7GKHBYpWiknTse7rrUBh2F0dG5ldHOIAAAAAAAAAACEZXRoMpD1pf1CAAAAAP__________gmlkgnY0gmlwhFzAVJaJc2VjcDI1NmsxoQKxhcZJCugFnVuRMMzE4JJe0E0FS71ctmAnx1Y2wCJwKoN1ZHCCpgQ" \
--bootstrap-node "enr:-Ku4QKsKa3HbJjz8cZn4mEh-stIF6kACLh2rmCGscEsLUe4XUSt-xZEAx7SK6R3zqAc2WAVBpLkh5fu-r-PHr_8d4B8Bh2F0dG5ldHOIAAAAAAAAAACEZXRoMpD1pf1CAAAAAP__________gmlkgnY0gmlwhDMPd52Jc2VjcDI1NmsxoQMLvOjDnLAqnQsTKqUqNr1qcleEBgkin3KOW9BeIxAJ54N1ZHCCW8w"

```

_Note,_ the config assumes you have an ETH1 Goerli node running on localhost with WS APIs enabled. If you don't have any ETH1 node locally, just skip the `web3provider` flags and the node will default to the public Prysmatic Labs Goerli endpoint.

_Note,_ Prysm allows you to use the `--peer` and `--bootstrap-node` flags multiple times.

### Validator Deposits
The validator contract is deployed on Goerli testnet address [`0x42cc0FcEB02015F145105Cf6f19F90e9BEa76558`](https://goerli.etherscan.io/address/0x42cc0FcEB02015F145105Cf6f19F90e9BEa76558).

To generate a new validator keypair, run:
```
bazel run //validator -- accounts create \
--witti-testnet \
--keystore-path ${PATH_TO_SECURE_BACKUP}/validators \
--password "${MY_SECRET_PASSWORD}"
```

This will output binary data that can be directly sent to the deposit contract along with 32 GöETH, e.g., for the Geth Console:
```
eth.sendTransaction({from:eth.coinbase, to:"0x42cc0FcEB02015F145105Cf6f19F90e9BEa76558", value:32000000000000000000, data:"0x22895118000000000000000000000000000000000000000000000000000000000000008000000000000000000000000000000000000000000000000000000000000000e00000000000000000000000000000000000000000000000000000000000000120e186fd32a8665a0212b919b0c5847f187f2661c85bda6d5afa3f2cd20ee9ceda0000000000000000000000000000000000000000000000000000000000000030a5db4a6e35523d4bc4537c8db168f1913977104b3366d695b5ed6bd32eb3b4f7d92170f52934b6b49f3cc21f078cc3cc00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000002000c435e9dcd6605b47046e3f9f52f3fe1609a6677a883ff22c0628a70ad3571300000000000000000000000000000000000000000000000000000000000000608b131cb82d47d552c6009d0985362626a692895ebc4c001f25cd6144489db58487ab4d64a141be898c9ba9428012954a0c57b2f819092f9b4c5c822b09007f11cd4a137a1b4629f0a3a412f6ebfdb36ba22be665d973e14cb637080ea7476aa6"})
```

### Validator Client
To start validating, open another terminal and launch the validator client:
```
bazel run //validator -- \
--witti-testnet \
--keymanager "keystore" \
--keymanageropts='{"passphrase":"${MY_SECRET_PASSWORD}", "path":"${PATH_TO_SECURE_BACKUP}/validators"}' \
--graffiti "Hello Witti"
```

_Note,_ Prysm allows you to set a custom `--graffiti`. :)

That's it. Please create an issue if this does not work. We will figure it out: [github.com/goerli/schlesi/issues/new](https://github.com/goerli/schlesi/issues/new)
