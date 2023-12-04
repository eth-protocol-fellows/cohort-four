# ePBS (enshrined proposer builder separation) implementation with inclusion list

Implementing a proof of concept for ePBS with inclusion list support in both consensus and execution layers to enshrine block building and make ethereum more censorship resistant.

## Motivation

*What problem is your project is solving? Why is it important and what area of the protocol will be affected?*


Currently, in Ethereum, the [PBS (proposer builder seperation)](https://ethresear.ch/t/proposer-block-builder-separation-friendly-fee-market-designs/9725) is seen in out of protocol systems like flashbots where the existing validators outsource block building to external entities. These external entities are sophisticated actors who can capture MEV and produce a block with much higher value (or juice) as compared to validators running on normal hardware. This design relies on a very small set of trusted entities called Relays which are responsible for proposer builder communication. At present, more than 90% of blocks in the network are broadcasted by 10 active relays. This introduces centralized risks and also makes the network more vulnerable to censorship.

As a result, [this](https://ethresear.ch/t/why-enshrine-proposer-builder-separation-a-viable-path-to-epbs/15710) post advocates for having an in-protocol (enshrined) implementation of PBS as it can make the whole process more decentralized, censorship resistant and trustless. Moreover, having the block building process in-protocol makes the builders more accountable for their actions and makes the process more transparent.

Enshrined Proposer-Builder Separation (ePBS) is part of Ethereum's path toward better control over, if not mitigation of, non-user-value-additive MEV capture as well as enabling fully stateless validators whilst decreasing the chances of validator centralisation. Toxic or "bad" MEV is a major contributor of increased L1 transaction fees (especially when there is congestion or contention in MEV strategies) and a source of unfair transacting such as searchers front-running or sandwiching other users. Although the full extent of tactical and strategic MEV on Ethereum is not known, its effects are increasingly being discovered and studied.

## Project description

*What is your proposed solution?*

As enshrining PBS is a complex problem and multiple designs have been proposed for the same, the goal is to implement a PoC for the PTC (Payload Timliness Committee) design along with inclusion list in the Prysm consensus client and geth execution client.

## Specification

*How will you implement your solutions? Give details and more technical information on the project.*

There are quite a few research articles available for ePBS and as mentioned above, multiple designs have been proposed. The project involves reviewing existing proposals and literature. Potuz and Terrence from the Prysm team have been involved in the discussions and have voted to go with the [PTC (Payload Timliness Committee) design](https://ethresear.ch/t/payload-timeliness-committee-ptc-an-epbs-design/16054). It is an updated design of another design initial proposed by Vitalik called [Two-slot PBS](https://ethresear.ch/t/two-slot-proposer-builder-separation/10980).

This requires changes in both the consensus as well as the execution layer. Potuz and Terrence have been working on the consensus specs and the plan is to fully understand them, review them and implement them in the Prysm consensus client. For execution layer, the specs (and an EIP) will be written at a later stage (and I hopefully plan to contribute to writing that as well) and the chosen client is Geth. The plan is to break down the whole implementation into different components and iteratively build out the required feature. Moreover, with ePBS, an inclusion list design proposed [here](https://ethresear.ch/t/no-free-lunch-a-new-inclusion-list-design/16389) will also be implemented for preventing censorship as both of them are complementary to each other. 

The fellows involved in this project will be initially involved in discussing about the implementation plan post reviewing the specs proposed. Initially, we'll get involved in general contributions and then modules to implement/modify will be divided internally.

The end goal is to build a working PoC with following features:
1. Builders as highly staked validators sending bids for bulding the next block without revealing the transactions. The validator of the respective slot can choose a bid and propose the beacon block. After a round of voting on the blinded beacon block, builder reveals the payload (i.e. list of transactions) which will be voted upon by the PTC committee.
2. Proposers of current slot can send a list of transactions which they want to get included by the next block's builder to avoid censorship. This will be tackled in a different way to avoid free DA problem as mentioned in the post above.

## Roadmap

*What is your proposed timeline? Outline parts of the project and insight on how much time it will take to execute them.*

**Week 1-3** Spend time on learning more about PBS and ePBS desigs. Read and review the specs thoroughly (and if possible contiribute to it) and figure out the implementation plans. Take part in discussions about the design choices with mentors and other fellows.

**Week 4-10**: Divide the modules to be implemented and start with iterative development on CL and EL. Plan the implementation in a way where each module (or a group of them) can be tested (via unit tests for now) in isolation. Based on the progress, plan the deployment of the PoC on a devnet.

**Week 11-12**: Document the project and continue with the testing plans.

## Possible challenges

*What are the limitations and issues you may need to overcome?*
1. ePBS is still being actively researched upon and as mentioned above there are multiple designs available. The community haven't finalised as of now, which design will be suitable more and hence there's a possibility that it might change in the future.
2. It's a huge project and even with multiple people working on it it might take more time then expected to complete it. If not testing, we hope to complete the PoC implementation by the end of the fellowship. I would be happy to continue working on it after the fellowship as well.
3. At this point, I see that there are lot of implementation unknows and a lot are expected as we proceed (at least according to me). It will challenging to tackle them and also work with a huge codebase of Prysm and Geth.

## Goal of the project

*What does success look like? Describe the end goal of the project, scope, state and impact for the project to be considered finished and successful.*

The end goal of the project is to review the existing literature, specs and have a working implementation of ePBS PTC design with inclusion list on a devnet. Here is the rough list of things which we expect to complete (as a group):

1. PoC implementation in Prysm (CL) and Geth (EL).
2. Testing plan for the PoC (included unit tests as well as devnet testing)
3. Documentation of the project

## Collaborators

### Fellows 

*Are there any fellows working with you on this project?*

As it's a huge project, multiple people will be working on it.
- [Manav Darji](https://github.com/manav2401)
- [Anshal Shukla](https://github.com/anshalshukla)
- [Chirag Mehta](https://github.com/Chirag018)
- [Ella](https://github.com/0xfmoi)
- [NC](https://github.com/naviechan) (An external participant)

### Mentors

*Which mentors are helping you with the project?*

- [Potuz](https://github.com/potuz/)
- [Terrence](https://github.com/terencechain/)
- [Marius](https://github.com/MariusVanDerWijden/)

## Resources

*Provide links to repositories, PRs and other resources which constitute the project.*

Resources required for implementation
- [PTC design](https://ethresear.ch/t/payload-timeliness-committee-ptc-an-epbs-design/16054)
- [IL design](https://ethresear.ch/t/no-free-lunch-a-new-inclusion-list-design/16389)
- [Consensus specs (beacon chain, fork choice)](https://github.com/potuz/consensus-specs/pull/1)
- [Consensus specs (builder, validator, p2p)](https://github.com/terencechain/consensus-specs/pull/1)
- [Engine API specs](https://github.com/naviechan/execution-apis/pull/1)

Implementation / PR links
- [IL implementation in geth](https://github.com/manav2401/go-ethereum/pull/1)
- [Execution (engine API) specs](https://github.com/manav2401/execution-apis/pull/1)
