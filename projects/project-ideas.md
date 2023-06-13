# Proposed projects

Here is a list of projects proposed by mentors. Use these project as an inspiration and if you would like to know more about specific project or work on it, contact corresponding mentor.

- [Previous cohorts](#previous-cohorts)
- [Fuzzing](#fuzzing)
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
- [ePBS design and prototyping](#epbs-design-and-prototyping)
- [Separate blobs from payload](#separate-blobs-from-payload)
- [Devops tooling wishlist](#devops-tooling-wishlist)

### Previous cohorts

In previous cohorts, you can find many up to date ideas which haven't been solved yet.

- [Project ideas in the first cohort](https://github.com/ethereum-cdap/cohort-one/issues?q=is%3Aissue+Project+idea)
- [Project ideas in the second cohort](https://github.com/ethereum-cdap/cohort-zero/issues?q=is%3Aopen+is%3Aissue+label%3A%22help+wanted%22)
- [Project ideas in the third cohort](https://github.com/eth-protocol-fellows/cohort-three/blob/master/projects/project-ideas.md), [Projects executed](https://github.com/eth-protocol-fellows/cohort-three/blob/master/projects/)


### Fuzzing

Proposed by Frederik

Create new fuzzers for software in order to find potential vulnerabilities, or improve on existing fuzzing frameworks. Networking in particular is an area where this could see some improvements on, but clients on the execution layer and consensus layer could also benefit from additional fuzzing.
https://github.com/MariusVanDerWijden/tx-fuzz
https://github.com/MariusVanDerWijden/FuzzyVM
https://github.com/holiman/goevmlab/
https://github.com/infosecual/nosy
https://github.com/ethereum/c-kzg-4844/tree/main/fuzz
https://github.com/jtraglia/kzg-fuzz


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

### Prysm
#### Auditing Beacon APIs in Prysm
(By Radosław Kapka)

Currently it's not possible to connect a Prysm validator client (VC) to a non-Prysm beacon node. Before the third cohort started, our VC could interact with the beacon node (BN) only through a Prysm-specific set of gRPC endpoints. EPF's third cohort participants set out on a journey to change this and allow the VC to communicate over HTTP using Beacon APIs. They got very close to making it happen, and it's probably a matter of weeks before we have a working implementation. That being said, there's still a lot to be done before we can safely advise our users to turn the feature on.

When initially implementing Beacon APIs, our primary focus was on correctness rather than efficiency. As a result some endpoints are very unoptimized. They contain expensive loops and don't make use of certain caches. Additionally, server-side handlers are written as gRPC functions, necessitating a middleware layer to convert between HTTP and gRPC. This is very costly. On the contrary, Prysm-specific gRPC endpoints are optimized to make the VC <--> BN communication as fast as possible. We want to eventually deprecate these endpoints in favor of Beacon APIs, but we can't do that if we have to sacrifice too much.

The main idea behind this project is to audit existing Beacon APIs, identify bottlenecks and improvement opportunities, propose and implement optimizations. Ideally all endpoints should be rewritten as HTTP handlers which would remove the middleware layer, but this may be out of scope for this project, unless it gets a lot of popularity and we can split work between multiple participants.

Beacon APIs need you! ;-)

#### ePBS Design and Prototyping
(By Potuz and Terence)

We are planning to ramp up engineering design space for ePBS and are looking for interested cohort fellows that are torn between research and software engineering. Tasks will include review of the current literature on ePBS, prototyping and writing design documents adapted to the Prysm CL client, and writing production level code. The literature consists mostly writeups by the RIG, which has an open problem on precisely this same topic. In this project we are more interested in deploying a working product, that can be tested in distributed devnets and compatible with EIP4844. 

#### Separate Blobs from Payload
(By Kasey, Potuz and Terence) 

This project is about studying the implementation and design space for separation of blobs from the execution payload in Deneb. A rationale for this proposed change can be found [in this Ethereum magician's post](https://ethereum-magicians.org/t/uncouple-blobs-from-the-execution-payload/13059). Tasks include writing design docs for implementation in Prysm, prototyping them, writing (or reviewing) the accompanying consensus layer spec repo pull requests and eventually delivering production code that can be tested on devnets. 

### Devops tooling wishlist

By Pari

https://github.com/ethpandaops/tooling-wishlist

### Portal Network

#### By ogenev

Improve Portal Network interop tests (portal-hive), Portal State Network R&D, Portal DAS network R&D

#### By Mike Ferris

Portal Network Glados: https://github.com/Ethereum/glados

### Lighthouse

#### By Michael Sproul

- Adding and benchmarking new slasher backends. Lighthouse can use either LMDB or MDBX for its slasher backend but we are interested in experimenting with other options like SQLite, Postgres and redb.
- Similar to the slasher backend, we would like to modularise the beacon node database backend. Currently only LevelDB is supported, but it has several issues and is starting to look quite dated. This project would involve abstracting over the backend, and then adding at least one new one (e.g. SQLite).
- Implementing improvements to Lighthouse's attestation packing. We have undertaken previous research on this topic, but have yet to implement all of the ideas we decided upon. See: https://lighthouse-blog.sigmaprime.io/optimising-attestation-packing.html and https://github.com/sigp/lighthouse/issues/3733.

#### By Paul Hauner

- P2P network, consensus optimizations, UX improvements, improved monitoring, database optimization.

### Besu

#### By Justin Florentine 

EIP-7002 if it gets approved. We have a wide variety of potential projects to offer and can tailor it to the candidate. Working on protocol will depend on the protocol roadmap, so likely upcoming projects would be EOF and Verkle Trie adoption.

### Consensus specs

#### By HWW

https://notes.ethereum.org/@hww/consensus-specs-wishlist

### Ethereum Deb Repo

By Mario Havel

Tool for crafting deb packages enabling to run whole Eth infrastracture easily and automatically. 

https://notes.ethereum.org/@MarioHavel/ethdebrepo

### Teku

By Mehdi Aouadi  

There are some interesting open issues in the Teku Github repo: 
- Epics: https://github.com/ConsenSys/teku/issues?q=is%3Aopen+is%3Aissue+label%3AEpic+ 
- Enhancements: https://github.com/ConsenSys/teku/issues?q=is%3Aopen+is%3Aissue+label%3A%22enhancement+%F0%9F%95%B5%EF%B8%8F%E2%80%8D%E2%99%80%EF%B8%8F%22 