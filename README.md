# Ethereum 2.0 Multi-Client Testnets
[![discord](https://img.shields.io/badge/discord-eth2%23schlesi-9cf)](https://discord.gg/P5TRzdb)
[![gitter](https://img.shields.io/badge/gitter-goerli%2Fschlesi-f6b)](https://gitter.im/goerli/schlesi)

This repository has become a collection of multiple active and inactive testnets. Please refer to the following specs for details:
* **Zinken** v0.12.3 _dress rehearsal_ testnet:  [zinken/README.md](./zinken/README.md) _(scheduled)_
* Spadina v0.12.3 _dress rehearsal_ testnet:  [spadina/README.md](./spadina/README.md) _(inactive)_
* **Medalla** v0.12.2 _public_ testnet: [medalla/README.md](./medalla/README.md) (**active**)
    ```
    / meh-dah-shah test-net /
    ```
* Altona v0.12.1 dev-testnet: [altona/README.md](./altona/README.md) (active)
* Witti v0.11.3 dev-testnet: [witti/README.md](./witti/README.md) _(inactive)_
* Schlesi v0.11.2 dev-testnet: [schlesi/README.md](./.trash/schlesi/README.md) _(inactive)_
* _Unnamed_ v0.10.1 dev-testnet: [v0-10-1/README.md](./.trash/v0-10-1/README.md) _(inactive)_:

Or read the generalized outline on how to launch your own testnet: [LAUNCH.md](./LAUNCH.md)

### F.A.Q.
_I'm wondering ..._

##### Why do we need multi-client test-networks?
The first phase of Ethereum 2.0, the phase 0, is the beacon chain. For the first time, a variety of new clients will be working together on a brand new blockchain with a new, unique approach to networking and consensus.

Before such a mainnet can be launched, we need testnets that mimic mainnet conditions as good as possible. This requires us to have stable, long-term, and persistent testnets up and running that are supported by not only one client but multiple clients, ideally, all clients.

The Schlesi testnet was one of many steps in that direction. The Witti testnet was another. The Altona testnet is yet another. The Medalla testnet aims to be the final one prior to mainnet launch.

##### Is _Medalla_ the official, public multi-client testnet?
Yes.

##### What's the difference between Altona and _Onyx_?
The [Onyx Testnet](https://medium.com/prysmatic-labs/introducing-the-onyx-testnet-6dadbd95d873) is a single-client testnet launched by the Prysmatic Labs team to replace _Topaz_. It's entirely comprised of Prysm validators, other clients didn't have releases at genesis yet.

Altona, Witti, and Schlesi, on the other side, tried to have as many different clients right from the start. The Schlesi genesis contained 50% Lighthouse and 50% Prysm validators. The Witti genesis even featured three clients. Altona featured four clients. They are multi-client testnets.

##### What's the difference between Altona and _Topaz_?
The [Topaz Testnet](https://medium.com/prysmatic-labs/introducing-topaz-testnet-8e8a4e00a700) is a single-client testnet. Same reasoning as _Onyx_ above.

##### What's the difference between Altona and _Multinet_?
The [ETH 2.0 Multinet](https://github.com/eth2-clients/multinet) is a collection of startup scripts to simulate multi-client testnets with various parameters such as number of validators to run the network with. The multinet is based on a minimal ETH 2.0 specification.

Altona, however, is _not_ a simulation. It's a real persistent end-user testnet based on a slightly modified mainnet configuration. Everyone should be able to add validators and beacon chain nodes.

##### What's the difference between Altona and _Interop_?
The [ETH 2.0 Interop Lock-In](https://blog.ethereum.org/2019/09/19/eth2-interop-in-review/) was a physical meetup of seven client teams working towards interoperability in 2019. This was the first major step towards multi-client testnets, even though the focus of the lock-in was mainly on networking. Other aspects of interoperability were playing minor roles.

For Altona, _all_ aspects are important, as they would be important for a potential mainnet candidate.

##### Why does Altona use the _Mainnet_ configuration?
The ultimate goal of Altona should be proving that the clients are ready to support a potential beacon-chain mainnet. Therefore, it is time to template the testnet as close as possible to mainnet.

##### Why is there no docker file or startup script?
The focus of the testnet is no longer developer but end-user centric. Each user of the beacon chain should be able to manually complete any task, i.e., setting up a validator or synchronizing a beacon chain node. Scripts will be convenient in future to ease this process but for now we need to ensure that nodes, clients, and other tooling is ready to be used sufficiently to complete all tasks required by a beacon chain mainnet.

Additionally, not having a script that does the job for you, ensures that all node implementations and their according tooling are well documented across the different clients.

##### Is _Altona_ an incentivized adversarial network?
No. The Altona testnet is not incentivized. The current goal is to ensure protocol compatibility across major ETH 2.0 client implementations. Participation is free and permissionless, everyone can create validator deposits at [`0x16e82D77882A663454Ef92806b7DeCa1D394810f`](https://goerli.etherscan.io/address/0x16e82D77882A663454Ef92806b7DeCa1D394810f) on the _Goerli_ Ethereum testnet and start validating on Altona.

##### Why do you call it _Medalla_?
Medalla means "medal" and can be seen as a reference to the _Olympic_ testnet that was used to prepare the ETH1 launch. It emphasizes the importance of the network at this stage towards the ETH2 launch. It can also be seen as a hint that Medalla validators will recieve a [proof of attendance "medal"](https://poap.xyz) on the Ethereum network for participation.

##### Why did you call Altona _Altona_?
Altona is a subway station in the city of Hamburg, Germany. It was [proposed on Reddit by u/krokodilmannchen](https://www.reddit.com/r/ethfinance/comments/guf8lr/daily_general_discussion_june_1_2020/fsil2n8/).

##### Why did you call Witti _Witti_?
Witti (Wittenbergplatz) is a subway station in Berlin proposed by MP. It's the first testnet named by a subway station in Berlin that is not located in the district of Kreuzberg were many blockchain companies, including the ETH DEV, have their offices.

##### Why did you call Schlesi _Schlesi_?
Schlesi (Schlesisches Tor) is a subway station in Berlin with proximity to _Goerli_ and _ETH DEV_ offices.

##### What is the _Goerli_ testnet?
Goerli is a cross-client proof-of-authority [Ethereum 1.x testnet](https://github.com/goerli/testnet). It's well supported across all ETH 1.0 clients, tooling, and infrastructure, and will be used to test the ETH 2.0 transition through a deposit contract deployed to Goerli.

### See also
In the news:
- [The Block: Ethereum 2.0 testnet 'Spadina' goes live ahead of the mainnet release](https://www.theblockcrypto.com/linked/79092/ethereum-2-spadina-testnet-live)
- [Cointelegraph: Launch rehearsal for Ethereum 2.0 "90% successful" despite participation issues](https://cointelegraph.com/news/launch-rehearsal-for-ethereum-2-0-90-successful-despite-participation-issues)
- [Coindesk: Ethereum 2.0 Developers Launch Spadina, a Three-Day Practice Testnet](https://www.coindesk.com/spadina-ethereum-2-0-testnet)
- [Cointelegraph: Medalla Testnet Problems "Will Not Delay ETH 2.0" Says Prysmatic Labs](https://cointelegraph.com/news/medalla-testnet-problems-will-not-delay-eth-20-says-prysmatic-labs)
- [Cointelegraph: Ethereum Medalla Testnet Launch Suffers Block Finality Issue](https://cointelegraph.com/news/ethereum-medalla-testnet-launch-suffers-block-finality-issue)
- [Coindesk: Ethereum 2.0 Testnet Medalla Goes Live With 20,000 Validators](https://www.coindesk.com/ethereum-2-0-testnet-medalla-goes-live-with-20000-validators)
- [Cointelegraph: Eth 2.0 Dev Shares Details of Upcoming Community Testnet](https://cointelegraph.com/news/eth-20-dev-shares-details-of-upcoming-community-testnet)
- [Cointelegraph: Ethereum 2.0 Final Testnet Set to Launch on August 4 ](https://cointelegraph.com/news/ethereum-20-final-testnet-set-to-launch-on-august-4)
- [Coindesk: Ethereum 2.0 Developers Announce ‘Final’ Testnet Before Network Launch](https://www.coindesk.com/ethereum-2-0-developers-announce-final-testnet-before-network-launch)
- [Cointelegraph: Latest Eth 2.0 Testnet on Track for June Launch](https://cointelegraph.com/news/latest-eth-20-testnet-on-track-for-june-launch)
- [Cointelegraph: Realistic Ethereum 2.0 Multi-Client Testnet 'Targeting for June' ](https://cointelegraph.com/news/realistic-ethereum-20-multi-client-testnet-targeting-for-june)
- [Coindesk: Schlesi Testnet Is Latest Step in Long Road Toward Eth 2.0](https://www.coindesk.com/ethereum-schlesi-testnet-eth-2-0)
- [Blockonomi: Ethereum 2.0 Specter Grows with Launch of “Schlesi” Multi-Client Testnet](https://blockonomi.com/ethereum-2-launch-schlesi-multi-client-testnet/)
- [The Block: Ethereum 2.0's Phase 0 multiclient testnets will likely go live in April](https://www.theblockcrypto.com/post/60292/ethereum-2-0s-phase-0-multiclient-testnets-will-likely-go-live-in-april-predicts-buterin)

Resources:
- [Video: EDCON 2020 Keynote - Final Road to Ethereum 2.0: Multi-Client Testnets](https://www.youtube.com/watch?v=7yQLN49bb30)
- [Article: Schlesi is Dead, Long Live Witti!](https://medium.com/@SomerEsat/schlesi-is-dead-long-live-witti-151178064c3c)
- [Notes: Longstanding MC-testnet(s)](https://notes.ethereum.org/DLu2WPtDSMOeNlnBth03Dw)
- [Article: How to run your own Beacon Chain](https://dev.to/q9/how-to-run-your-own-beacon-chain-e70)
- [Stack Exchange: What does the beacon chain deposit contract ceremony entail?](https://ethereum.stackexchange.com/questions/80258/what-does-the-beacon-chain-deposit-contract-ceremony-entail)
- [Stack Exchange: How would a chain specification for a beacon chain look like?](https://ethereum.stackexchange.com/questions/80264/how-would-a-chain-specification-for-a-beacon-chain-look-like)

Historical documentation:
- [Analysis: Multi-client benchmark on Altona testnet 2020/07/16](https://github.com/q9f/eth2-bench-2020-07)
- [Analysis: Multi-client benchmark on Witti testnet 2020/06/22](https://github.com/q9f/eth2-bench-2020-06)
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
