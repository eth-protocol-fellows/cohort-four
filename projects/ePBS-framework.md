# ePBS Viable Paths Forward - Formal Analyses and Assessment Framework

## Motivation
*What problem is your project is solving? Why is it important and what area of the protocol will be affected?*

Enshrined Proposer-Builder Separation (ePBS) is part of Ethereum's path toward better control over, if not mitigation of, toxic MEV capture as well as enabling fully stateless validators. Toxic or "bad" MEV is a major contributor of increased L1 transaction fees and a source of unfair transacting such as searchers front-running other users. Although the full extent of tactical and strategic MEV on Ethereum is not fully known, its effects are increasingly being discovered and studied.

Since the [origination](https://notes.ethereum.org/@vbuterin/pbs_censorship_resistance) of the PBS problem was laid out by Vitalik in 2021, there have been a few live proposals for making a healthy transition to ePBS plausible though none selected yet as the chosen path forward.

## Project description
*What is your proposed solution?*

This project dissects the original PBS problem whilst reviewing in detail the most viable and popular live proposals, which are:
- [Why enshrine Proposer-Builder Separation? A viable path to ePBS](https://ethresear.ch/t/why-enshrine-proposer-builder-separation-a-viable-path-to-epbs/15710) by Mike Neuder and Justin Drake with [MEV burn—a simple design](https://ethresear.ch/t/mev-burn-a-simple-design/15590) which is an add-on by Justin Drake
- [Unbundling PBS: Towards protocol-enforced proposer commitments (PEPC)](https://ethresear.ch/t/unbundling-pbs-towards-protocol-enforced-proposer-commitments-pepc/13879?u=barnabe) by Barnabé Monnot
- [SUAVE](https://writings.flashbots.net/mevm-suave-centauri-and-beyond) (and [here](https://writings.flashbots.net/the-future-of-mev-is-suave/)) by Flashbots

In dissecting the orignal PBS problem we also review the following:
- Challenges with fair transaction sequencing, the ultimate root-cause solution to MEV extraction
- [Forward-inclusion](https://notes.ethereum.org/@fradamt/forward-inclusion-lists) / [Proposer Broadcast lists](https://notes.ethereum.org/@fradamt/H1f3PlB5Y) `crlist`
- [Parallelisation of block construction](https://notes.ethereum.org/@vbuterin/pbs_censorship_resistance), one of the two possible solutions proposed in Vitalik's original post

## Specification
*How will you implement your solutions? Give details and more technical information on the project.*

The following deliverables should ship:
- **Dissection of the above proposals**
    - Draft high level specifications
    - Clarification of what the proposal is and what its implications would be
- **Framework for analyses (its challenges, first principles for constrast/compare)**

## Roadmap
*What is your proposed timeline? Outline parts of the project and insight on how much time it will take to execute them.*

**Fellowship**

**Aug 14-20**
- Read, dissect, and publish analysis with full understanding of both proposals in original PBS problem.
    - [State of research: increasing censorship resistance of transactions under proposer/builder separation (PBS)](https://notes.ethereum.org/@vbuterin/pbs_censorship_resistance)

**Aug 21-Sep 3**
- Read, dissect, and publish analysis of and build out high-level specs for:
    - [Why enshrine Proposer-Builder Separation? A viable path to ePBS](https://ethresear.ch/t/why-enshrine-proposer-builder-separation-a-viable-path-to-epbs/15710) by Mike Neuder and Justin Drake
    - [MEV burn—a simple design (a PBS add-on)](https://ethresear.ch/t/mev-burn-a-simple-design/15590) by Justin Drake

**Sep 4-10**
- Read, dissect, and publish analysis of and build out high-level specs for*:
    - [Unbundling PBS: Towards protocol-enforced proposer commitments (PEPC)](https://ethresear.ch/t/unbundling-pbs-towards-protocol-enforced-proposer-commitments-pepc/13879?u=barnabe) by Barnabé Monnot
    - *Review fellow cohort member's [project](https://hackmd.io/@oLeaCeNDTl-O01HPNj9_sw/r1eZd51g3n) as he is building out the specifications for PEPC.

**Sep 11-17**
- Read, dissect, and publish analysis of:
    - [SUAVE](https://writings.flashbots.net/mevm-suave-centauri-and-beyond) by Flashbots

**Sep 18-Oct 1**
- Understand and spec out what the abandoned paths forward were:
    - [Forward-inclusion](https://notes.ethereum.org/@fradamt/forward-inclusion-lists) / [Proposer Broadcast lists](https://notes.ethereum.org/@fradamt/H1f3PlB5Y) `crlist`
    - [Parallelisation of block construction](https://notes.ethereum.org/@vbuterin/pbs_censorship_resistance), one of the two possible solutions proposed in Vitalik's original post
- Read and publish analysis of challenges in fair transaction sequencing / ordering.

**Oct 2-8**
- Tidy up thoughts and finalise framework for assessing proposals.
- Start on presentation for Dev Connect.

**Oct 9-31**
- Further work on the presentation and concluding thoughts from the research.
- Buffer period for any extra time needed at some point.

**Post-Fellowship**
- Continue research on MEV mitigation especially in context of the Ethereum roadmap. Are there better ways we can move ePBS forward?

## Possible challenges
*What are the limitations and issues you may need to overcome?*
- The current proposals do not currently have specifications around them which makes assessing feasibility difficult.
- The current proposals are live which means they could change during the course of this study.
- The proposals themselves may require direct conversations with the writers for clarification and confirmation, but we only want to do this if there are clearly questions that can't be confirmed from all other resources.

## Goal of the project
*What does success look like? Describe the end goal of the project, scope, state and impact for the project to be considered finished and successful.*

The project's purpose is to build best practices or create food for thought on what qualities the ideal proposal for ePBS would have (with labels such as critical or optional). The framework will also provide rationale on "why" these assessment criteria are important. The formation of the criteria are conclusions that come from formal analyses of proposal risks, implementation feasibility, and costs/benefits. The conclusions should help progress the discussion on selecting the path forward for the Ethereum community.

## Collaborators

### Mentors
*Which mentors are helping you with the project?*

[Alex Stokes](https://github.com/ralexstokes)<br>
[Barnabé Monnot](https://github.com/barnabemonnot)<br>
[Justin Drake](https://github.com/justindrake)<br>
[Mike Neuder](https://github.com/michaelneuder)<br>

### Resources
*Provide links to repositories, PRs and other resources which constitute the project.*
To be updated
