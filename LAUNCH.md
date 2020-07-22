# Launch an ETH2 multi-client testnet/mainnet

All of the moving parts that need to come together to successfully launch an ETH2 network.

_Examples are italic, here: [Medalla](https://github.com/goerli/medalla)._

### 1. Preparation

The following steps are crucial to design and plan the testnet.

1. Design the **scope**, i.e., dev-net, public testnet, attack-net, incentivized network, etc. pp.
    * _official public testnet_
1. Optionally, give it a **name**. This is only necessary for long-term, public or mid-term, semi-public networks. Long names should come with a short handle for the client's config.
    * _Medalla, or `medalla`_
1. Define the **version** of the specification, e.g., `v0.12.2` or `v0.11.3`, so that all clients can agree on running the same specification. Make sure the specification has tests and a release in the official spec repository.
    * _`v0.12.2`_
    * _[eth2.0-specs#1955](https://github.com/ethereum/eth2.0-specs/pull/1955) (release pending)_
1. Pick a **chain specification**. In most cases, you want to use a `mainnet/phase0` config. But there are also potentially needs for `minimal` or `phase1` configs.
    * _[`configs/mainnet/phase0.yaml`](https://github.com/ethereum/eth2.0-specs/blob/dev/configs/mainnet/phase0.yaml)_
1. Deploy the **deposit contract**. Either use the official Solidity contract, the Vyper contract, or any customly augmented contract that contains features for testing purposes, i.e., withdrawal functions or validator whitelisting. Make sure to verify it on block explorers for public testnets.
    * _Solidity contract [`deposit_contract.sol`](https://github.com/axic/eth2-deposit-contract/blob/master/deposit_contract.sol)_
    * _formally verified exact byte code [`deposit_contract.json`](https://github.com/axic/eth2-deposit-contract/blob/master/deposit_contract.json)_
    * _Solidty `v0.6.8`, optimized: `yes`, runs: `5000000`_
    * _deployed to address [0x07b39F4fDE4A38bACe212b546dAc87C58DfE3fDC](https://goerli.etherscan.io/address/0x07b39f4fde4a38bace212b546dac87c58dfe3fdc)_
    * _verified on Etherscan [address/0x07b3..3fdc#code](https://goerli.etherscan.io/address/0x07b39f4fde4a38bace212b546dac87c58dfe3fdc#code)_
1. Define a **minimum genesis time**. You don't want to launch the network prior to that timestamp. Only required for coordinated launches, otherwise just use the default and launch right away.
    * _Gregorian: August 4th, 2020, 1pm UTC_
    * _Unix: `1596546000`_
1. Optionally, choose a custom **genesis fork version**, or modify any other parameters as per your needs, e.g., number of genesis validators or deposit amounts.
    * _Genesis fork version: `0x00000001`_
1. Add the chosen **parameters** to the chain specification. The selected chain configuration requires to be updated with everything defined above.
    * _for Medalla: [gist/q9f/941b2621214d05ef8759abde30e4f9ef](https://gist.github.com/q9f/941b2621214d05ef8759abde30e4f9ef)_
      ```
      MIN_GENESIS_TIME: 1596546000
      DEPOSIT_CONTRACT_ADDRESS: 0x07b39F4fDE4A38bACe212b546dAc87C58DfE3fDC
      GENESIS_FORK_VERSION: 0x00000001
      ```
1. That's it, that's the testnet.

### 2. Implementation

The following steps are necessary to implement, deploy, and prepare the launch of the testnet. It assumes launching a public or semi-public testnet that requires some coordination. Private or short-term dev-nets could proceed directly to the launch section.

1. **Publish** the configuration in an accessable location, e.g., Github, Gist, Pad, Hackmd, etc.
    * _[hackmd/tFQjQzZ6R9OKKwK0lh9OsA](https://hackmd.io/tFQjQzZ6R9OKKwK0lh9OsA)_
    * _[gist/q9f/941b2621214d05ef8759abde30e4f9ef](https://gist.github.com/q9f/941b2621214d05ef8759abde30e4f9ef)_
    * _[github/goerli/medalla](https://github.com/goerli/medalla)_
1. Communicate the scope and chain configuration early with the **client teams**. They can then decide to bake in the configuration and even, depending on scope and spec version, make it the default testnet.
    * _Lighthouse [github/sigp/lighthouse](https://github.com/sigp/lighthouse)_
    * _Prysm [github/prysmaticlabs/prysm](https://github.com/prysmaticlabs/prysm)_
    * _Teku [github/PegaSysEng/teku](https://github.com/PegaSysEng/teku)_
    * _Nimbus [github/status-im/nim-beacon-chain](https://github.com/status-im/nim-beacon-chain)_
    * _Lodestar [github/ChainSafe/lodestar](https://github.com/ChainSafe/lodestar)_
    * _Trinity [github/ethereum/trinity](https://github.com/ethereum/trinity)_
    * _Cortex [github/NethermindEth/cortex](https://github.com/NethermindEth/cortex)_
1. Bootnodes: This is always our chicken-and-egg item on that bullet list. Do we provide bootnodes first that we can add to the clients or do we implement the config in the clients before setting up bootnodes? Whatever you do first, please **publish the bootnode**'s ENR and/or Multi-Address to Github/Gist/Pads, so other clients can access this resource. It's recommended that each client provides at least one bootnode.
1. Clients: **Implement** the specification and bootnodes. Consider giving it internally a meaningful name (_`medalla`_), maybe log the spec version (_`v0-12-2`_), and provide command-line flags for users to be able to connect to the network (_`--medalla` or `--medalla-testnet`_). Depending on the scope, also consider making it default or just an additional network.
1. Communicate the planned launch and the scope of the network with other **service providers** that are potentially interested in the network. Tell them about the name, scope, config, and planned launch date.
    1. _Block explorers:_
        * _EtherScan/BeaconScan [beaconscan.com](https://beaconscan.com/)_
        * _Bitfly/BeaconChain [beaconcha.in](https://beaconcha.in/)_
        * _BlockAction [blockaction.io](https://blockaction.io/)_
    1. _Network monitors:_
        * _ETH2Stats [eth2stats.io](https://eth2stats.io/)_
    1. _Staking pools:_
        * _Rocket Pool [rocketpool.net](https://www.rocketpool.net/)_
    1. _Miscellaneous:_
        * _Proof of Attendance [poap.xyz](https://www.poap.xyz/)_

### 3. Launch

The following steps are necessary to launch a network. For the sake of completeness, it assumes a launch of a public, coordinated testnet.

1. Configure and provide a **launchpad**. Users that want to validate on the network should be provided with a user interface helping to make validator deposits and get set up completely.
    * _Ethereum Foundation's Launchpad [github/ethereum/eth2.0-deposit](https://github.com/ethereum/eth2.0-deposit)_
    * _Prysmatic Labs' Testnet Site [github/prysmaticlabs/prysm-testnet-site](https://github.com/prysmaticlabs/prysm-testnet-site)_
1. For testnets, **provide faucets** that allow users to redeem enough testnet tokens to be able to make around one to five validator deposits, e.g., for _Goerli_.
    * _DappNode Faucet `206.25 ETH/9 days` [goerli-faucet.dappnode.net](https://goerli-faucet.dappnode.net/)_
    * _Mudit's Faucet `87.50 ETH/9 days` [faucet.goerli.mudit.blog](https://faucet.goerli.mudit.blog/)_
    * _Serverless Faucet `32.50 ETH/day` [github/PhilippLgh/serverless-faucet](https://github.com/PhilippLgh/serverless-faucet)_
    * _Prylabs Faucet `32.50 ETH/request` [prylabs.net/participate](https://prylabs.net/participate)_
    * _Metamask Faucet `1.00 ETH/request` [faucet.metamask.io](https://faucet.metamask.io/)_
    * _Status Faucet `0.10 ETH/request` [faucet-goerli.status.im/faucet-info](https://faucet-goerli.status.im/faucet-info)_
    * _Slockit Faucet `0.05 ETH/request` [goerli-faucet.slock.it](https://goerli-faucet.slock.it/)_
    * _More: WallEth, Avado, StakeWise, ..._
1. Make sure everything above is **properly documented**, especially custom command-line flags, instructions how to run a beacon node or a validator, how to use the launchpad with a certain client, etc. pp.
1. Client teams should prepare properly tagged **releases and binaries** if desired to ease running the nodes on the new network.
3. Provide **genesis validators**. Key stakeholders and client teams might want to run validators at genesis for various reasons. Make sure to get in deposits before the minimum genesis validator count is met.
4. **Announce** the launch if you want a broad audience, either "officially" through the Ethereum Foundation blog or through the client teams communication channels (discord, blogs, etc.).
5. **Monitor** the launch. Lean back and check validator deposits, some might be invalid due to outdated tooling or bugs that should be squashed immediately once isolated.
6. **Launch**. This is most likely happening automatically once minimum validator deposits are met and the minimum genesis time passed. It's worth comparing the computed genesis time, the fork digest, initial state and block root across the clients. Make sure they match.

That's it. Now proceed to Phase 1. :smile: 
