# Altona ETH 2.0 Testnet
![cortex](https://img.shields.io/badge/cortex-n%2Fa-inactive)
![lighthouse](https://img.shields.io/badge/lighthouse-active-success)
![lodestar](https://img.shields.io/badge/lodestar-in--progress-yellow)
![nimbus](https://img.shields.io/badge/nimbus-active-success)
![prysm](https://img.shields.io/badge/prysm-active-success)
![teku](https://img.shields.io/badge/teku-active-success)
![trinity](https://img.shields.io/badge/trinity-in--progress-yellow)

This repository contains the client configuration files and genesis state for the `v0.12.1` Ethereum 2.0 specification multi-client testnet _"Altona v0.12"_ for the following clients:
- Genesis Time: _estimated Monday June/29 ~12:30 UTC_
- Fork Digest:
- Initial State Root:
- Genesis Block Root:
- Deposit Contract: `0x16e82D77882A663454Ef92806b7DeCa1D394810f`
- Chain Explorers: [altona.beaconcha.in](https://altona.beaconcha.in/)
- Status Dashboard: [eth2stats.io/altona-testnet](https://eth2stats.io/altona-testnet)

Client support:
- [ ] Cortex
- [x] **Lighthouse** (Genesis): defaults to Altona [#1295](https://github.com/sigp/lighthouse/pull/1295), just run `lighthouse bn` or refer to the [latest documentation](https://lighthouse-book.sigmaprime.io/).
- [ ] Lodestar
- [x] **Nimbus** (Genesis): checkout the `devel` branch, and run `make altona`.
- [x] **Prysm** (Genesis): comes with an Altona config [#6380](https://github.com/prysmaticlabs/prysm/pull/6380), just run `beacon-chain --altona` or refer to the [latest documentation](https://docs.prylabs.network/docs/getting-started/).
- [x] **Teku** (Genesis): defaults to Altona [#2223](https://github.com/PegaSysEng/teku/pull/2223), just run `teku` or refer to the [latest documentation](https://docs.teku.pegasys.tech/en/latest/).
- [ ] Trinity

### License
This is free and unencumbered software released into the public domain. For more information, please refer to [unlicense.org](https://unlicense.org)
