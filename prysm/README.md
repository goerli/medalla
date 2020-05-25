# Prysm Config for Witti v0.11.3
This document describes how to connect to and participate in the Witti testnet using the Prysm ETH2 client. [github.com/prysmaticlabs/prysm](https://github.com/prysmaticlabs/prysm/)

### Requirements
This requires Bazel, get it here: [bazel.build](https://bazel.build/)

_Note:_ Bazel will manage the build and dependencies, for other options, please refer to the Prysm documentation. [prysmaticlabs.gitbook.io/prysm](https://prysmaticlabs.gitbook.io/prysm/)

To connect to Witti v0.11.3, you would have to compile Prysm from `q9-witti-testnet` branch. See [prysmaticlabs/prysm#5905](https://github.com/prysmaticlabs/prysm/pull/5905)
```
git clone https://github.com/q9f/prysm.git
cd prysm/
git checkout q9-witti-testnet
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
--http-web3provider http://127.0.0.1:8545 \
--web3provider ws://127.0.0.1:8546 \
--min-sync-peers 0 \
--bootstrap-node "enr:-KG4QO6QrRlWQ2Z5ss4XoUsrPvsepRuuogcHyC81gMQr7PJ3IFh41bDnGSl9iN_ijg2EgQeEQDpRPkE4FzD2ecbp6XoChGV0aDKQgGboQQAAARP__________4JpZIJ2NIJpcIQAAAAAiXNlY3AyNTZrMaEDpsGvSN7oM2c04ZT9mrG32TVj-sMhb6HiKc6LMEXYEyiDdGNwgnUwg3VkcIJ1MA"
```

_Note,_ the config assumes you have an ETH1 Goerli node running on localhost with HTTP and WS APIs enabled. If you don't have any ETH1 node locally, just skip the `web3provider` flags and the node will default to the public Prysmatic Labs Goerli endpoint.

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
