# Lighthouse Config for Schlesi v0.11

This document describes how to connect to and participate in the Schlesi testnet using the Lighthouse ETH2 client. https://github.com/sigp/lighthouse

### Requirements

This requires Rust, of course, get it here: https://rustup.rs/

To connect to Schlesi v0.11, you would have to compile Lighthouse from `master` branch with PR [#1052](https://github.com/sigp/lighthouse/pull/1052) applied.

```
git checkout master
wget https://patch-diff.githubusercontent.com/raw/sigp/lighthouse/pull/1052.patch
git apply 1052.patch
```

Make sure to build in release mode.

```
cargo build --release
```

### Beacon Node

It's assumed you have a local copy of the Schlesi repository.

```
git clone https://github.com/goerli/schlesi.git
cd schlesi/
```

Run a previously compiled beacon node:

```
lighthouse bn --testnet-dir PATH/TO/schlesi/light
```

If you plan to run a validator on Schlesi, enable the Rest API with ` --http`:

```
lighthouse bn --testnet-dir PATH/TO/schlesi/light --http
```

### Validator Deposits

The validator contract is deployed on Goerli testnet address [0xA15554BF93a052669B511ae29EA21f3581677ac5](https://goerli.etherscan.io/address/0xA15554BF93a052669B511ae29EA21f3581677ac5).

Assuming you have a Goerli node running on localhost with RPC enabled on port `8545`, this will create valiadtor keys and send a deposit:

```
lighthouse account validator new \
--testnet-dir --testnet-dir PATH/TO/schlesi/light \
--send-deposits \
--password PATH/TO/password.txt \
--deposit-value 32000000000 random
```

Make sure your `password.txt` contains the password for your first Goerli testnet account (`eth.accounts[0]`) which has sufficient funds (> 32 GöETH).

It's recommended to use a Geth node as ETH1 provider.

### Validator Client

To start validating, open another terminal and launch the validator client:

```
lighthouse vc --testnet-dir PATH/TO/schlesi/light
```

Please create an issue if this does not work. We will figure it out: https://github.com/goerli/schlesi/issues/new
