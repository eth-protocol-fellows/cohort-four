# Proposed projects

Here is a list of projects proposed by mentors. Use these project as an inspiration and if you would like to know more about specific project or work on it, contact corresponding mentor. 

- [Previous cohorts](#previous-cohorts)
- [Security system based on machine learning](#security-system-based-on-machine-learning)
- [Alex Stokes](#alex-stokes)
- [RIG Opened Problems](#rig-opened-problems)
- [P2P protocol tests](#p2p-protocol-tests)
- [Improving hive for End-to-End Testing](#improving-hive-for-end-to-end-testing)
- [Ephemery testnet](#ephemery-testnet)
- [API for ETH supply](#api-for-calculating-eth-supply)
- [By Yoav Weiss](#by-yoav-weiss)
- [By Dapplion](#by-dapplion-lodestar)
- [Browser tooling](#browser-tooling)
- [By Tomasz Stanczak](#by-tomasz-stanczak-nethermind)
- [By Zahary Karadjov](#by-zahary-nimbus)
- [Auditing Beacon API](#auditing-beacon-apis-in-prysm)
- [Devops tooling wishlist](#devops-tooling-wishlist)

### Previous cohorts

In previous cohorts, you can find many up to date ideas which haven't been solved yet. 

- [Project ideas in the first cohort](https://github.com/ethereum-cdap/cohort-one/issues?q=is%3Aissue+Project+idea)
- [Project ideas in the second cohort](https://github.com/ethereum-cdap/cohort-zero/issues?q=is%3Aopen+is%3Aissue+label%3A%22help+wanted%22)
- [Project ideas in the third cohort](https://github.com/eth-protocol-fellows/cohort-three/blob/master/projects/project-ideas.md), [Projects executed](https://github.com/eth-protocol-fellows/cohort-three/blob/master/projects/) 


### Security system based on machine learning

Proposed by Frederik

Applying machine learning on for example the network protocol (or it could be on other areas too such as on-chain data) to create outliers and enable early warning systems for issues that start occurring is something I feel would be valuable. This could perhaps be a custom built system, or based off on elastic stack or similar existing solution.

There could also be more static data being shown such as validator performance, conflicting chains, etc.

### Alex Stokes

`ralexstokes/{beacon-api-client, ssz-rs, ethereum-consensus, mev-rs` on github

`ethereum/consensus-specs`, `ethereum/builder-specs`

### RIG Opened Problems

By Barnabé Monnot

Explore Robus Incentives Group Opened Problems https://efdn.notion.site/ROPs-RIG-Open-Problems-c11382c213f949a4b89927ef4e962adf

### Improving hive for End-to-End Testing

Proposed by Mario Vega

[Hive](https://github.com/ethereum/hive) can evolve into more sophisticated tool for e2e testing which allows to run the Consensus and Execution clients as they would be run by the end users. 

### Ephemery testnet 

By Mario Havel

Contribute to integration of public ephemeral testnet. Research and feedback the spec, create implementations in clients and/or client testing, end user tooling, e.g. dappnode, nicenode, stereum. Check the [specs](https://github.com/ethereum/EIPs/blob/04369cb50ee6c1894dec868141e8a32e66dc4f16/EIPS/eip-testnet-draft.md) and [network details](https://github.com/ephemery-testnet/ephemery-resources). 

### API for calculating ETH supply

By Tim Beiko

An API endpoint that calculates the current supply of ETH. Create basic specification and implementation which should get merged in at least one EL<>CL combo and maybe even the API specs. Ideally, works on multiple clients and you can compare the output.

### By Yoav Weiss

#### Optimism sequencer support for ERC 4337 bundlers

Modify the Optimism (Bedrock) sequencer to add a new RPC for ERC-4337 (account abstraction) bundlers. The new RPC will enable submitting a transaction with certain conditions, and the sequencer will guarantee that the transaction will only be sequenced if these conditions are met. The RPC will be designed to mitigate DoS against the sequencer, require only minimal work from the sequencer, and throttle callers with poor inclusion ratio.

#### ERC-4337 tooling support

Research about tooling support, identify the missing pieces and add ERC-4337 (account abstraction) support to popular dev tools like Hardhat, Foundry, etc.

### By Dapplion (Lodestar)

For cryptographers, help solve practical challenges with SSLE.
For consensus researchers, explore fork-choice implementation of https://ethresear.ch/t/secret-non-single-leader-election/11789.

### Browser tooling

By Cayman Nava (Lodestar)

Simple webapps that may become useful, eg: https://enr-viewer.com/

### By Tomasz Stanczak (Nethermind)

IL-EVM (superoptimized EVM in C#)
GPT-RPC
Paprika - new C# DB optimized for Merkle Tries and Keccaks

### By Zahary (Nimbus)

* Create a single Nimbus binary combining our consensus and execution clients.
* Create a Verkle tree library in Nim.
* Introduce out of order and speculative execution in the Nimbus asynchronous EVM to speed up transaction execution when the Ethereum state data must be fetch dynamically from the Portal network.
* Implement a novel snap sync protocol for the beacon chain.
* Implement a novel distributed validator setup in the Nimbus beacon node, reducing the risk of validator downtime.
* Implement a stateless mode for the Nimbus execution client.
* Implement a management GUI/WebUI for Nimbus.
* Implement a novel append-only database for the Nimbus beacon node.
* Implement instant one-shot syncing based on the zero-knowledge proofs from the DendrETH project.

### Auditing Beacon APIs in Prysm

By Radek

### Devops tooling wishlist

By Pari 

https://github.com/ethpandaops/tooling-wishlist
