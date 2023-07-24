# zk-wave

## Description <a id="desc"></a>

## Participants <a id="participants"></a>

* Luke Schoen @ltfschoen

## Mentors <a id="mentors"></a>

* [Mentors](../program-guide/mentors.md)
* TBC zkOracle - Suning Yao https://ethresear.ch/t/defining-zkoracle-for-ethereum/15131	

## Scope <a id="scope"></a>

* TBC

## Goals <a id="goals"></a>

* Work on zkOracle open-source and open-protocols.
* Building prototypes of zkOracle using a decentralized p2p networks.
* Improving client architecture to incorporate zkOracle
* Developing and improving low-level EVM mechanics where possible
* Contributing to the public good.
* Improve knowledge in weak areas and share the journey.

## Roadmap <a id="roadmap"></a>

* Common
    * Mentors (see [Mentors](#mentors) 
        * Prepare "well-informed technical & topical" questions for "development" & "research" mentors for their ideas and to unlock doors and remove barriers (see ../program-guide/mentors.md). Note: Not for teaching 
        * Ask questions to mentors in Discord #protocol-fellowship and tag relevant mentors
        * Post questions to https://github.com/eth-protocol-fellows/cohort-four/issues
        * Post research questions and learnings to [Ethereum Research forum](https://ethresear.ch/)
        * Post EIP and technical issues to [Ethereum Magicians forum](https://ethereum-magicians.org/)
    * Dev updates
        * Publish updated development-updates.md with each dev update
        * Post dev update in Discord #protocol-fellowship
    * Standup call
        * Previously working on
        * Next working on
        * Blockers (if any)
    * Office hours (see [EFP Participation Guide](../program-guide/participation-guide.md))

* [ ] 20230701 W0
    * Initial reading. See [Links](#links)
    * Initial group session
    * Learn about chosen problems
    * Form teams
    * Create write up of a topic they are interested in based on input from mentors

    * **TODO** 
        * EFP readings
        * ZK readings
        * Questions
            * Difference between [zkOracle](https://ethresear.ch/t/defining-zkoracle-for-ethereum/15131) and:
                * [Phala Phat contract oracle](https://github.com/Phala-Network/oracle-workshop/blob/master/easy_oracle/lib.rs) 
                * [zkOracle Wiki](https://zkoracleofficial.gitbook.io/zk-oracle-wiki/)

* Note: Start days of the week are shown below
* [ ] 20230707 W0 Dev update & Office hours
    * Deep dive into identified areas
    * Learn and familiarize with previous work and current solutions.
    * Connect with chosen mentors and work towards defining a deliverable project scope of work
    * Write and submit this [project proposal](/projects/project-template.md) on the selected problem(s), suggested solutions, and a roadmap for working on the issue throughout the program.
    * Report presentation to other participants and select mentors to gather final feedback.
* [X] 20230715 W1 Dev update & Standup call & Office hours
    * Contacted Suning Yao who confirmed that zkOracle that was mentioned at ethresear.ch has a solution being developed by @HyperOracle
    * Reviewed the whole zkWasm-C codebase but did not really understand it since I had not yet read the Hyper Oracle documentation https://docs.hyperoracle.io/. I was not able to run it because I could not find the project/ directory, so raised this issue https://github.com/DelphinusLab/zkWasm-C/issues/5, however more recently this week I discovered the project/ directory in a specific commit, so if time permits I will revisit that repository.
    * Read through the Hyper Oracle documentation here https://docs.hyperoracle.io/ and summarised it with hand-written notes to try to understand how it works so when I read more code implementations then hopefully it will make sense.
    * Initial thoughts on issues to contribute to add to the roadmap for working on throughout the program is to create examples, which should help reinforce how it works and help the community, and since they are open issues in the zkGraph repository here https://github.com/hyperoracle/zkgraph/issues that were only opened in the past few weeks, and since it is written in TypeScript it should be an achievable goal. 
* [ ] 20230722 W2 Standup call & Office hours
    * Sick with flu from 20th July until Standup on 25th July so unfit to progress
    * Participated in Encode ZK Bootcamp day 1 on 25th July
* [ ] 20230731 W3 Dev update & Standup call & Office hours & Demo day
    * Execute project roadmap to complete deliverables
* [ ] 20230807 W4 Standup call & Office hours
* [ ] 20230815 W5 Dev update & Standup call & Office hours
* [ ] 20230822 W6 Standup call & Office hours
* [ ] 20230831 W7 Dev update & Standup call & Office hours & Demo day
* [ ] 20230807 W8 Standup call & Office hours
* [ ] 20230915 W9 Dev update & Standup call & Office hours
* [ ] 20230922 W10 Standup call & Office hours
* [ ] 20230930 W11 Dev update & Standup call & Office hours & Demo day
* [ ] 20230907 W12 Standup call & Office hours
* [ ] 20231015 W13 Dev update & Standup call & Office hours
* [ ] 20231022 W14 Standup call & Office hours
* [ ] 20231031 W15 Dev update & Standup call & Office hours & Demo day
    * Project showcase
    * Plan future contributions to ecosystem
* [ ] 20231113 Ethconnect Istanbul

## Progress <a id="progress"></a>

* [zk-wave Repository link](https://github.com/ltfschoen/zk)

## Suggested Solution Options <a id="solution-options"></a>

## Resources / Links <a id="links"></a>

* EFP
    * [Technical resources](../program-guide/README.md)
    * [reading](../program-guide/reading.md)
    * Ethereum Protocol Development Roadmap
        * https://twitter.com/VitalikButerin/status/1466411377107558402/photo/1
            * PoS specs: https://github.com/ethereum/consensus-specs#phase-0
            * Sharding: https://notes.ethereum.org/@vbuterin/data_sharding_roadmap
            * Verkle trees: https://notes.ethereum.org/Yn_mwNa2SeeQHnKsRgekKg
            * Expiry: https://eips.ethereum.org/EIPS/eip-4444 (history) + https://notes.ethereum.org/@vbuterin/state_expiry_eip (state)
            * EVM simplification: https://hackmd.io/@vbuterin/evm_feature_removing
            * EVM obj format: https://eips.ethereum.org/EIPS/eip-3540
            * EVM modular ops: https://notes.ethereum.org/@axic/evm384
            * Account abstraction: https://eips.ethereum.org/EIPS/eip-4337
            * EIP 3074: https://eips.ethereum.org/EIPS/eip-3074
            * Single slot confirmations: https://ethresear.ch/t/a-model-for-cumulative-committee-based-finality/10259
            * Address space extension: https://ethereum-magicians.org/t/thoughts-on-address-space-extension-ase/6779
            * DAS: https://hackmd.io/@vbuterin/das
            * PBS: https://notes.ethereum.org/@vbuterin/pbs_censorship_resistance

    * [Ethereum Yellow paper video](https://www.youtube.com/watch?v=e84V1MxRlYs)
    * [Ethereum VM](https://ethervm.io/)
    * [Ethereum Wiki](https://ethereum.org/en/deprecated-software/#documentation-and-information-sources) 
    * [Ethereum Research forum](https://ethresear.ch/)
    * [Ethereum Magicians forum](https://ethereum-magicians.org/)
    * [Ethereum Project Management](https://github.com/ethereum/pm)
* ZK
    * See README at [https://github.com/ltfschoen/zk](https://github.com/ltfschoen/zk)
* Ethereum
    * Sigma Prime https://lighthouse-book.sigmaprime.io
    * RETH (Ethereum Protocol implementation)
        * https://github.com/paradigmxyz/reth
    * Akuna (old Ethereum implementation)
        * https://github.com/akula-bft/akula
* Other
    * Tooling wishlist - https://github.com/ethpandaops/tooling-wishlist