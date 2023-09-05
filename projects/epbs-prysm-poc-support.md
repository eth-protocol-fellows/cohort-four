# ePBS analyses of viable paths forward and design support for an ePBS POC for the Prysm Client
ePBS analysis + implementation support

## Motivation
*What problem is your project is solving? Why is it important and what area of the protocol will be affected?*

Enshrined Proposer-Builder Separation (ePBS) is part of Ethereum's path toward better control over, if not mitigation of, non-user-value-additive MEV capture as well as enabling fully stateless validators whilst decreasing the chances of validator centralisation. Toxic or "bad" MEV is a major contributor of increased L1 transaction fees (especially when there is congestion or contention in MEV strategies) and a source of unfair transacting such as searchers front-running or sandwiching other users. Although the full extent of tactical and strategic MEV on Ethereum is not known, its effects are increasingly being discovered and studied.

Since the [origination](https://notes.ethereum.org/@vbuterin/pbs_censorship_resistance) of the PBS problem was laid out by Vitalik in 2021, there have been a few live proposals for making a healthy transition to ePBS plausible, though none selected yet as the chosen path forward.

## Project description
*What is your proposed solution?*

Potuz and Terence are working on the design and implementation of production-level ePBS code that is compatible with EIP4844 for devnet testing. This includes creating a POC which means designing, spec'ing out, and coding it.

I hope to help with the prototyping by supporting them on design documents adapted to the Prysm CL client.

## Specification

*How will you implement your solutions? Give details and more technical information on the project.*

**Review of ePBS proposals and related literature**
- [Why enshrine Proposer-Builder Separation? A viable path to ePBS](https://ethresear.ch/t/why-enshrine-proposer-builder-separation-a-viable-path-to-epbs/15710) by Mike Neuder and Justin Drake with [MEV burn—a simple design](https://ethresear.ch/t/mev-burn-a-simple-design/15590) which is an add-on by Justin Drake
- [Unbundling PBS: Towards protocol-enforced proposer commitments (PEPC)](https://ethresear.ch/t/unbundling-pbs-towards-protocol-enforced-proposer-commitments-pepc/13879?u=barnabe) by Barnabé Monnot
- [Two-slot PBS](https://ethresear.ch/t/two-slot-proposer-builder-separation/10980) and [PBS with friendly fee market](https://ethresear.ch/t/proposer-block-builder-separation-friendly-fee-market-designs/9725) by Vitalik
- [SUAVE](https://writings.flashbots.net/mevm-suave-centauri-and-beyond) (also [here](https://writings.flashbots.net/the-future-of-mev-is-suave/)) by Flashbots
- [Forward-inclusion](https://notes.ethereum.org/@fradamt/forward-inclusion-lists) / [Proposer Broadcast lists](https://notes.ethereum.org/@fradamt/H1f3PlB5Y) `crlist`;
- [Payload timeliness in ePBS](https://ethresear.ch/t/payload-timeliness-committee-ptc-an-epbs-design/16054)
- For context, paths toward [single-slot finality](https://notes.ethereum.org/@vbuterin/single_slot_finality#), [non-single leader selection](https://ethresear.ch/t/secret-non-single-leader-election/11789), the [stateless client concept](https://ethresear.ch/t/the-stateless-client-concept/172).

**Review Prysm documentation**
- Review current draft [POC](https://github.com/potuz/consensus-specs/pull/1)
- [Terence's specs](https://hackmd.io/@ttsao/ryk-M0Yt2)
- Discord discussion thus far
- General Prysm code and [documentation](https://docs.prylabs.network/docs/contribute/contribution-guidelines)

**Identificaton of open issues**
- Design for Prysm ePBS implementation is currently open
- [blob+payload separation design](https://ethereum-magicians.org/t/uncouple-blobs-from-the-execution-payload/13059)
- Gossiping specs
- More to come as I review the Discord


## Roadmap
*What is your proposed timeline? Outline parts of the project and insight on how much time it will take to execute them.*

**Aug - Phase 1**
- Read and digest relevant literature
- Catch up on the current state of Prysm ePBS POC
- Work with potuz to confirm what I will work on / help with (which will probably take place on one of the weekly calls or over Discord)

**Sep - Oct Phase 2**
- Work on the POC (will update details here or through development updates)

## Possible challenges
*What are the limitations and issues you may need to overcome?*
- The final path toward ePBS is not clear. This means that the specifications will likely change or need to be adaptable. We're currently work of Mike and Justin's proposal.
- I'm not very familiar with the Go programming language and am not a strong developer. I will do my best to write strong pseudo code where needed and focus on the design and specifications.

## Goal of the project
*What does success look like? Describe the end goal of the project, scope, state and impact for the project to be considered finished and successful.*

potuz and Terence actually end up using something I produce!

## Collaborators

### Fellows 
*Are there any fellows working with you on this project?*

Not sure - but probably yes! I see the following in the Discord channel:
Anderson Chen
Bryce
bchain99
Manav Darji

### Mentors
*Which mentors are helping you with the project?*

[potuz](https://github.com/potuz)
[Terence](https://github.com/terencechain)
[Alex Stokes](https://github.com/ralexstokes)

## Resources
*Provide links to repositories, PRs and other resources which constitute the project.*
- [Prysm ePBS POC draft](https://github.com/potuz/consensus-specs/pull/1)
- [Prysm GitHub](https://github.com/prysmaticlabs/prysm/tree/develop)
- [Go documentation](https://go.dev/doc/)
- [Ethereum deneb consensus specs](https://github.com/ethereum/consensus-specs/blob/dev/specs/deneb/beacon-chain.md)
- [MEV Boost specs](https://docs.flashbots.net/flashbots-mev-boost/architecture-overview/specifications)
