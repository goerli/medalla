# Teku Config for Witti v0.11.3
This document describes how to connect to and participate in the Witti testnet using the Teku ETH2 client. [github.com/PegaSysEng/teku](https://github.com/PegaSysEng/teku)

### Requirements
This requires Java 11+ and Gradle, get it here: https://gradle.org/

To connect to Witti v0.11.3, you would have to compile Teku from `master` branch.
```
git clone https://github.com/PegaSysEng/teku.git
cd teku/
git checkout master
```

Use Gradle to compile Teku.
```
./gradlew installDist
```

_Note,_ the binary can be found in `./build/install/teku/bin/`.

### Beacon Node
It's assumed you have a local copy of the Witti repository.
```
git clone https://github.com/goerli/witti.git
cd witti/
```

Run a previously compiled Teku node by pointing it to the Witti config.
```
teku \
--config-file="${PATH_TO_WITTI}/teku/config.yaml" \
--network="${PATH_TO_WITTI}/teku/chain.yaml"
```

### Validator Client
Teku allows you to generate keypairs and make deposits directly to the ETH1 provider.
```
teku validator generate \
--network="${PATH_TO_WITTI}/teku/chain.yaml" \
--eth1-endpoint="http://127.0.0.1:8545" \
--eth1-deposit-contract-address="0x42cc0FcEB02015F145105Cf6f19F90e9BEa76558" \
--eth1-keystore-file="${PATH_TO_SECURE_BACKUP}/goerli/keystore/UTC--2020-00-00T00-00-00.000000000Z--0000000000000000000000000000000000000000" \
--eth1-keystore-password-file="${PATH_TO_SECURE_BACKUP}/password.txt" \
--keys-output-path="${PATH_TO_SECURE_BACKUP}/teku/witti/keystore" \
--encrypted-keystore-validator-password-file="${PATH_TO_SECURE_BACKUP}/password.txt" \
--encrypted-keystore-withdrawal-password-file="${PATH_TO_SECURE_BACKUP}/password.txt" \
--number-of-validators=1
```

Teku comes with beacon node and validator client in one. To activate the generated validators, just add them to the `config.yaml` and restart Teku.
```
teku \
--config-file="${PATH_TO_WITTI}/teku/config.yaml" \
--network="${PATH_TO_WITTI}/teku/chain.yaml"
```

Taht's it. Please create an issue if this does not work. We will figure it out: https://github.com/goerli/schlesi/issues/new

See also: https://docs.google.com/document/d/1BP6B5muGjLGXVD1EOtorvlSBVzb5XR4OsYwBSTjiiDU/edit
