# Witti ETH 2.0 Testnet
![cortex](https://img.shields.io/badge/cortex-n%2Fa-inactive)
![lighthouse](https://img.shields.io/badge/lighthouse-active-success)
![lodestar](https://img.shields.io/badge/lodestar-in--progress-yellow)
![nimbus](https://img.shields.io/badge/nimbus-in--sync-green)
![prysm](https://img.shields.io/badge/prysm-active-success)
![teku](https://img.shields.io/badge/teku-active-success)
![trinity](https://img.shields.io/badge/trinity-n%2Fa-inactive)

Documentation of the Ethereum 2.0 phase-0 beacon-chain multi-client testnet efforts.

[![discord](https://img.shields.io/badge/discord-eth2%23schlesi-9cf)](https://discord.gg/P5TRzdb)
[![gitter](https://img.shields.io/badge/gitter-goerli%2Fschlesi-f6b)](https://gitter.im/goerli/schlesi)

Current ETH 2.0 specification version support:
- [x] v0.11.3 "Witti"
  - Genesis Time: `1590537600` (2020-05-27 00:00:00 +0000 UTC)
  - Fork Digest: `f6775d07`
  - Initial State Root: `0x773c694b47504d789dc768d2356f691866b47833d0d85e02511d7cd339925b17`
  - Genesis Block Root: `0x19aa2deaa02cac9774eb8948a8ead1ebe851ba9590878a10cd5767092e16ba12`
  - Deposit Contract: [`0x42cc0FcEB02015F145105Cf6f19F90e9BEa76558`](https://goerli.etherscan.io/address/0x42cc0FcEB02015F145105Cf6f19F90e9BEa76558) ([Goerli Testnet](https://github.com/goerli/testnet))
  - Chain Explorers:
    - [witti.beaconcha.in](https://witti.beaconcha.in/)
    - [witti.blockaction.io](https://witti.blockaction.io/)
  - Infura API: [witti.infura.io](https://witti.infura.io)
    - **Note:** Requires an Infura account and currently in private beta. [Reach out if interested in access.](https://infura.io/contact)
  - Status Dashboard: [eth2stats.io/witti-testnet](https://eth2stats.io/witti-testnet)

### `v0.11.3` "Witti"
This repository contains the client configuration files and genesis state for the `v0.11.3` Ethereum 2.0 specification multi-client testnet _"Witti v0.11"_ for the following clients:
- [ ] Cortex
- [x] Lighthouse [config: `lighthouse/`](lighthouse/), [docs: `lighthouse/README.md`](lighthouse/README.md)
- [ ] Lodestar _(WIP)_
- [x] Nimbus _(WIP)_ `git checkout devel && make witti`
- [x] Prysm [config: `prysm/`](prysm/), [docs: `prysm/README.md`](prysm/README.md)
- [x] Teku [config: `teku/`](teku/), [docs: `teku/README.md`](teku/README.md)
- [ ] Trinity

Clients will be added one by one once they manage to connect, synchronize, and stay in consensus.

### License
This is free and unencumbered software released into the public domain. For more information, please refer to [unlicense.org](https://unlicense.org)
