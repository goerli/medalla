# Teku Config for Schlesi v0.11

This document describes how to connect to and participate in the Schlesi testnet using the Teku ETH2 client. https://github.com/PegaSysEng/teku

### Requirements

This requires Java 11+ and Gradle, get it here: https://gradle.org/

To connect to Schlesi v0.11, you would have to compile Teku from `master` branch.

```
git checkout master
./gradlew installDist
```

The binary can be found in `./build/install/teku/bin/`.

### Beacon Node

It's assumed you have a local copy of the Schlesi repository.

```
git clone https://github.com/goerli/schlesi.git
cd schlesi/
```

Run a previously compiled teku node:

```
teku --config-file ./teku/config.yaml --network ./teku/chain.yaml --initial-state ./teku/genesis.ssz
```

_@TODO make this work_

### Validator Client

_@TODO document this_

Please create an issue if this does not work. We will figure it out: https://github.com/goerli/schlesi/issues/new
