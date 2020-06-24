# Ethereum 2.0 Multi-Client Testnets

This repository has become a collection of multiple active and inactive testnets. Please refer to the following specs for details:

* **Altona** v0.12.1 testnet: [altona/README.md](./altona/README.md)
* **Witti** v0.11.3 testnet: [witti/README.md](./witti/README.md)
* Schlesi v0.11.2 testnet: [schlesi/README.md](./.trash/schlesi/README.md) (inactive)
* _Unnamed_ v0.10.1 testnet: [v0-10-1/README.md](./.trash/v0-10-1/README.md) (inactive)
  
[![discord](https://img.shields.io/badge/discord-eth2%23schlesi-9cf)](https://discord.gg/P5TRzdb)
[![gitter](https://img.shields.io/badge/gitter-goerli%2Fschlesi-f6b)](https://gitter.im/goerli/schlesi)

### F.A.Q.
_I'm wondering ..._

##### Why do we need multi-client test-networks?
The first phase of Ethereum 2.0, the phase 0, is the beacon chain. For the first time, a variety of new clients will be working together on a brand new blockchain with a new, unique approach to networking and consensus.

Before such a mainnet can be launched, we need testnets that mimic mainnet conditions as good as possible. This requires us to have stable, long-term, and persistent testnets up and running that are supported by not only one client but multiple clients, ideally, all clients.

The Schlesi testnet was one of many steps in that direction. The Witti testnet is another.

##### What's the difference between Witti and _Onyx_?
The [Onyx Testnet](https://medium.com/prysmatic-labs/introducing-the-onyx-testnet-6dadbd95d873) is a single-client testnet launched by the Prysmatic Labs team to replace _Topaz_. It's entirely comprised of Prysm validators, other clients didn't have releases at genesis yet.

Witti and Schlesi, on the other side, tried to have as many different clients right from the start. The Schlesi genesis contained 50% Lighthouse and 50% Prysm validators. The Witti genesis even featured three clients. It's a multi-client testnet.

##### What's the difference between Witti and _Topaz_?
The [Topaz Testnet](https://medium.com/prysmatic-labs/introducing-topaz-testnet-8e8a4e00a700) is a single-client testnet. Same reasoning as _Onyx_ above.

##### What's the difference between Witti and _Multinet_?
The [ETH 2.0 Multinet](https://github.com/eth2-clients/multinet) is a collection of startup scripts to simulate multi-client testnets with various parameters such as number of validators to run the network with. The multinet is based on a minimal ETH 2.0 specification.

Witti, however, is _not_ a simulation. It's a real persistent end-user testnet based on a slightly modified mainnet configuration. Everyone should be able to add validators and beacon chain nodes.

##### What's the difference between Witti and _Interop_?
The [ETH 2.0 Interop Lock-In](https://blog.ethereum.org/2019/09/19/eth2-interop-in-review/) was a physical meetup of seven client teams working towards interoperability in 2019. This was the first major step towards multi-client testnets, even though the focus of the lock-in was mainly on networking. Other aspects of interoperability were playing minor roles.

For Witti, _all_ aspects are important, as they would be important for a potential mainnet candidate.

##### Why does Witti use the _Mainnet_ configuration?
The ultimate goal of Witti should be proving that the clients are ready to support a potential beacon-chain mainnet. Therefore, it is time to template the testnet as close as possible to mainnet.

##### Why is there no docker file or startup script?
The focus of the testnet is no longer developer but end-user centric. Each user of the beacon chain should be able to manually complete any task, i.e., setting up a validator or synchronizing a beacon chain node. Scripts will be convenient in future to ease this process but for now we need to ensure that nodes, clients, and other tooling is ready to be used sufficiently to complete all tasks required by a beacon chain mainnet.

Additionally, not having a script that does the job for you, ensures that all node implementations and their according tooling are well documented across the different clients.

##### Is _Witti_ an incentivized adversarial network?
No. The Witti testnet is not incentivized. The current goal is to ensure protocol compatibility across major ETH 2.0 client implementations. Participation is free and permissionless, everyone can create validator deposits at [`0x42cc0FcEB02015F145105Cf6f19F90e9BEa76558`](https://goerli.etherscan.io/address/0x42cc0FcEB02015F145105Cf6f19F90e9BEa76558) on the _Goerli_ Ethereum testnet and start validating on Witti.

##### Why do you call it _Witti_?
Witti (Wittenbergplatz) is a subway station in Berlin proposed by MP. It's the first testnet named by a subway station in Berlin that is not located in the district of Kreuzberg were many blockchain companies, including the ETH DEV, have their offices.

##### Why did you call Schlesi _Schlesi_?
Schlesi (Schlesisches Tor) is a subway station in Berlin with proximity to _Goerli_ and _ETH DEV_ offices.

##### What is the _Goerli_ testnet?
Goerli is a cross-client proof-of-authority [Ethereum 1.x testnet](https://github.com/goerli/testnet). It's well supported across all ETH 1.0 clients, tooling, and infrastructure, and will be used to test the ETH 2.0 transition through a deposit contract deployed to Goerli.

### See also
In the news:
- [Coin Telegraph: Realistic Ethereum 2.0 Multi-Client Testnet 'Targeting for June' ](https://cointelegraph.com/news/realistic-ethereum-20-multi-client-testnet-targeting-for-june)
- [Coindesk: Schlesi Testnet Is Latest Step in Long Road Toward Eth 2.0](https://www.coindesk.com/ethereum-schlesi-testnet-eth-2-0)
- [Blockonomi: Ethereum 2.0 Specter Grows with Launch of “Schlesi” Multi-Client Testnet](https://blockonomi.com/ethereum-2-launch-schlesi-multi-client-testnet/)
- [The Block: Ethereum 2.0's Phase 0 multiclient testnets will likely go live in April](https://www.theblockcrypto.com/post/60292/ethereum-2-0s-phase-0-multiclient-testnets-will-likely-go-live-in-april-predicts-buterin)

Resources:
- [Article: Schlesi is Dead, Long Live Witti!](https://medium.com/@SomerEsat/schlesi-is-dead-long-live-witti-151178064c3c)
- [Notes: Longstanding MC-testnet(s)](https://notes.ethereum.org/DLu2WPtDSMOeNlnBth03Dw)
- [Article: How to run your own Beacon Chain](https://dev.to/q9/how-to-run-your-own-beacon-chain-e70)
- [Stack Exchange: What does the beacon chain deposit contract ceremony entail?](https://ethereum.stackexchange.com/questions/80258/what-does-the-beacon-chain-deposit-contract-ceremony-entail)
- [Stack Exchange: How would a chain specification for a beacon chain look like?](https://ethereum.stackexchange.com/questions/80264/how-would-a-chain-specification-for-a-beacon-chain-look-like)

Historical documentation:
- [Analysis: A (DHT) Crawl Through The Witti Testnet 🕷](https://txrx-research.github.io/prkl/testnet-analysis.html)
- [Archived: Schlesi v0.11.2 ETH 2.0 Testnet](./.trash/schlesi/README.md)
- [Gist: Schlesi ETH 2.0 Multi-Client Testnet configuration](https://gist.github.com/q9f/d6eea3ea3356e41bde81864143284ce9)
- [Field notes: Towards a multi-client Ethereum 2.0 testnet](https://hackmd.io/GIwaFeGaQn6q7VYb_n94LA)
- [Call: EF Research & Görli Testnet “Multi-Client Testnet for ETH 2.0”](https://hackmd.io/Nx204wkTSgeGB0UzNXhz9g)

Previous multi-client testnets:
- [Github: eth2-clients/multinet](https://github.com/eth2-clients/multinet)
- [Github: eth2-clients/eth2-testnets](https://github.com/eth2-clients/eth2-testnets)

### Support
This project is supported by the:
* Görli Testnet Initiative - [goerli.net](https://goerli.net/)
* Ecosystem Support Programme - [esp.ethereum.foundation](https://esp.ethereum.foundation/en/)

Thanks :heart:

### License
This is free and unencumbered software released into the public domain. For more information, please refer to [unlicense.org](https://unlicense.org)
