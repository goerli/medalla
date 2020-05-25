# Lighthouse Config for Witti v0.11.3
This document describes how to connect to and participate in the Witti testnet using the Lighthouse ETH2 client. [github.com/sigp/lighthouse](https://github.com/sigp/lighthouse)

### Requirements
This requires Rust, of course, get it here: [rustup.rs](https://rustup.rs/)

To connect to Witti v0.11.3, you would have to compile Lighthouse from `master` branch.
```
git clone https://github.com/sigp/lighthouse.git
cd lighthouse/
git checkout master
```

Make sure to build in release mode.
```
cargo build --release
```

### Beacon Node
Get the Witti v0.11.3 testnet repository.
```
git clone https://github.com/goerli/witti.git
cd witti/
```

Run a beacon chain node by pointing it to the Witti testnet configuration directory.
```
lighthouse bn \
--testnet-dir ${PATH_TO_WITTI}/lighthouse
```

If you plan to run a validator on Schlesi, enable the Rest API with ` --http` and provide an `--eth1-endpoint`.
```
lighthouse bn --http \
--testnet-dir ${PATH_TO_WITTI}/lighthouse \
--eth1-endpoint http://127.0.0.1:8545
```

### Validator Deposits
Firstly, you have to create a new HD-Wallet. Let's call it `witti`.
```
lighthouse account_manager wallet create \
--name "witti" \
--passphrase-file ${PATH_TO_SECURE_BACKUP}/password.txt \
--testnet-dir ${PATH_TO_WITTI}/lighthouse \
--mnemonic-output-path ${PATH_TO_SECURE_BACKUP}/mnemonic.txt
```

After initializing the wallet and backing up the passphrase, we can create validator keypairs.
```
lighthouse account_manager validator create \
--at-most 1 \
--testnet-dir {PATH_TO_WITTI}/lighthouse \
--wallet-name "witti" \
--wallet-passphrase {MY_SECURE_BACKUP}/password.txt
```

The validator contract is deployed on Goerli testnet address [`0x42cc0FcEB02015F145105Cf6f19F90e9BEa76558`](https://goerli.etherscan.io/address/0x42cc0FcEB02015F145105Cf6f19F90e9BEa76558).

Assuming you have a Goerli node running with an IPC endpoint exposed and the sender address unlocked. This will send the deposit from your account `04f67c6fa446486d8da0a3534566bdc75ef67004`.
```
lighthouse account_manager validator deposit \
--eth1-ipc ${PATH_TO_GOERLI}/geth.ipc \
--from-address 04f67c6fa446486d8da0a3534566bdc75ef67004 \
--testnet-dir ${PATH_TO_WITTI}/lighthouse \
--validator all
```

It's recommended to use a Geth node as ETH1 provider.

### Validator Client
To start validating, open another terminal and launch the validator client:

```
lighthouse vc \
--testnet-dir ${PATH_TO_WITTI}/lighthouse
```

That's it. Please create an issue if this does not work. We will figure it out: [github.com/goerli/schlesi/issues/new](https://github.com/goerli/schlesi/issues/new)
