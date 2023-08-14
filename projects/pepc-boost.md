# PEPC-Boost

This document contains a project proposal to implement a POC of PEPC-Boost.  

## Motivation

Proposer-builder separation is a model which has been implemented out of protocol in Ethereum using a trusted MEV Relay. The essence of the model is that the proposer of the block can defer block building activities to an external builder. We can re-phrase this as a commitment to say that "the builder has a commitment to the proposer to produce a block whose value is more than the block which they can produce locally".
Currently, there are designs which aim to enshrine proposal builder seperation in protocol to eliminate the trusted relay and use the ethereum chain for trust. PEPC and PEPC-Boost is one such proposed design which is in its very early phases.
Continuing from the above "commitment", We look at PEPC. PEPC or Protocol-Enforced-Proposer-Commitment, is essentially a generalization of the proposer builder seperation where we allow the proposer to enter into any such commitment with the builder. Some example commitments could be:
1. Full Block Auction which is the current PBS
2. Partial Block Auction where the proposer suggests some transactions to be included in the block. 
3. Parallel Block Auctions where multiple builders suggest transactions to one block.

PEPC-Boost is a proposed out-of-protocol implementation of PEPC. The goal is to implement it in the current MeV Boost architecture.

## Project description

We want to implement a POC of PEPC-Boost which is a proposed out-of-protocol implementation of PEPC. Since PEPC and PEPC-Boost are very new research areas, this project could also involve a bit of research work alongside engineering work.

## Specification

A basic specification for PEPC-Boost has been described by Barnabe Monnot in [PEPC FAQ](https://efdn.notion.site/PEPC-FAQ-0787ba2f77e14efba771ff2d903d67e4#a2d2d17abe90414e88d667ad10d91afe).
The key idea is that we split a block into 2 parts, the TOB(Top of the block) and ROB(Rest of the block). We modify the relay spec to let the builders to bid seperately on the TOB and ROB.

The plan will be to iteratively build out the features of PEPC-Boost. We want to build the following features in a step by step manner(inspired by Barnabe's article):
1. For the first version, we just allow only 1 tx in the TOB bid and rest of the other txs in the ROB bid. To prevent state interference, we can make sure that the TOB bids only happen for a specific tx (eg: ETH/USDC swaps on Uniswap v3) and the rest of the txs are in the ROB bid. ROB builders can build knowing that they shouldn't not include txs from arbitrageurs who would do a DEX trade at a block.
2. If we are able to successfully achieve this, the next step would be to extend the TOB bid to include more txs. We can generalize it for more txs but the correct way would be to make sure that more liquidty pool swaps are included. We need to ensure that we have reserved tx slots for each LP to minimize state interference.

The next steps following this are more research oriented and much more deeper:
1. The next step would be to how we can utilize this separation of blockspace in TOB and ROB to implement inclusion lists. At this stage, we will have to think how we can implement inclusion lists as a proposer commitment. We will need to define the structure of a proposer commitment.
2. Post that, we can think about parallel block auctions amongst N builders by furthur splitting the TOB and ROB block furthur into N parts using the proposer commitment model which can specify the number of builders to use.


The Tech stack we will be using for PEPC-Boost implementation is:
1. [Flashbots MeV Relay](https://github.com/flashbots/mev-boost-relay) as the relay we will be modifying to implement PEPC-Boost relay
2. Using [Prysm](https://github.com/prysmaticlabs/prysm) as the consensus layer
3. Using [Geth](https://github.com/ethereum/go-ethereum) as the execution layer
4. [Flashbots Builder](https://github.com/flashbots/builder) as the base for the builder implementation 
5. I will setup my own devnet in my personal AWS account where I will deploy PEPC-Boost

## Roadmap

**Week 1-3:**
Spend time on learning more about PEPC, PBS and ethereum in general while designing iteration 1 and 2 of PEPC-Boost. I aim to have a design and specification ready by the end of this phase. I also aim to have feedback from mentors on the design and specification
During this phase, I will also work on spinning up my own devnet which I will require for my testing.

**Week 4-11:**
Implement the specification for iteration 1 and 2 of PEPC boost and deploy them to devnet. Try getting some feedback on it. On the side, if there is enough bandwidth, try to start working on implementing iteration 3 and 4 as well.

**Week 12:**
Document the project thoroughly. If iteration 1 and 2 go well, then try deploying it Goerli testnet.

## Possible challenges

Some challenges are listed below: 

1. PEPC-Boost and PEPC are very new ideas that are currently in the research phase. PEPC-Boost has been proposed less than 2-3 weeks ago. There is bound to be a lot of unknowns which will have to be answered on the way. This project will be touching both research and engineering. There might be difficulties during implementation because it touches a lot of parts like the CL, EL, Engine API, Builder API and relays. This may result in the project taking a longer time then estimated. Although, For iteration 1 and 2, we will mostly be touching only the relayer and builder spec. For iteration 3 and 4, we will have to get to the consensus and execution layer spec.
2. It will also be a challenge to design for PEPC-Boost with optimistic relaying since we might require a third actor like an assembler to assemble transactions from various builders which might increase latencies of the relayer.
3. Working on iterations 3 and 4 will be particularly challenging. Parallel block building with multiple builders can make state interference high and will be challenging to solve it. Coming with a general proposer commitment model will also be challenging. 

## Goal of the project
The end goal is to explore designs for the implementation of PEPC-Boost iteratively and implement them in devnet.

The required deliverables will be:
1. A MIRO design board highlighting the overall architecture of PEPC-Boost, along with the design for each iteration as specified in the Specification section.
2. A specification document highlighting changes to Builder API, Engine API, Consensus Layer specs and Execution Layer specs for each iteration. Althought, For iteration 1 and 2, we will mostly be touching only the relayer and builder spec. For iteration 3 and 4, we will have to get to the consensus and execution layer spec.
3. Deployment of PEPC-Boost to a local devnet with the implementation of the first 2 iterations.
4. Documentation on PEPC-Boost
5. Articles on learnings, thoughts and ideas related to PEPC and PEPC-Boost. 

Deliverables which would be nice to have:
1. Deploy iterations 1 and 2 to Goerli testnet.
2. Being able to implement designs for iteration 3, 4 and deploy to devnet.

Another goal is to read and document learnings in hackmd articles, design boards and so forth.

## Collaborators

### Fellows 
[Bharath V](https://github.com/bharath-123)

### Mentors

[Barnabe Monnot](https://github.com/barnabemonnot) 
[Terrence Tsao](https://github.com/terencechain)
[Mike Neuder](https://github.com/michaelneuder)

## Resources

[PEPC FAQs](https://efdn.notion.site/PEPC-FAQ-0787ba2f77e14efba771ff2d903d67e4#a2d2d17abe90414e88d667ad10d91afe)
[PEPC Original Proposal](https://ethresear.ch/t/unbundling-pbs-towards-protocol-enforced-proposer-commitments-pepc/13879?u=barnabe)
[Studying Ethereum Censorship](https://hackmd.io/@oLeaCeNDTl-O01HPNj9_sw/B1-3hBojh)
