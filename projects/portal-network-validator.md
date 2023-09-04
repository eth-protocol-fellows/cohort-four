# Portal Network Validator

Enabling validators to run a light client instead of an execution layer client.

## Motivation

Before the EPF, I was contributing to [Lighthouse](https://github.com/sigp/lighthouse/). There was an instance where I wanted to benchmark some changes to the beacon API, and I needed to run Lighthouse locally to do so. This was troubling because I didn't have an SSD big enough to run an execution layer client alongside Lighthouse. 

I had to [rely on an internal Sigma Prime endpoint](https://github.com/sigp/lighthouse/pull/3753#issuecomment-1409835389) to access an EL node.

And that's the **problem**: *If we want to run a consensus client, we also need the resources to run an execution client alongside*. I was fortunate to get access to the sigp node, but running something locally would've been better.

Solving this would greatly help _stakers who want to run their validators on a resource-constrained device_. It would help other users, like CL contributors, as I learned some months ago, but focusing on stakers gives me a better direction.

## Project Description

I will research how to _enable validators to run a [portal](https://github.com/ethereum/portal-network-specs) client instead of an execution layer client on their setup_.

## Specification

Some issues might be raised about the security and trust assumptions of this setup. I don't think this is something to be concerned about, Portal data is fully validated. However, something worth pointing out is that this setup would be highly experimental, and probably won't reach production level quality for months or even years. This is something that has to be extensively warned in the documentation that comes out of the project.

My project's output will consist of:

- **Research Documents**: Where I give detailed technical explanations of what I find.
- **Prototypes**: Where I implement the features I find feasible during research.

There are two areas I could focus my _research_ on:

- Enabling validators to propose blocks.
- Enabling validators to attest to blocks.

Both options provide significant challenges:

When _enabling validators to propose blocks_, the CL client needs to get an `ExecutionPayload`. Two approaches can be taken here: a) The portal client builds the block, or b) Someone else builds the block and the portal client validates it and broadcasts it (think about MEV-boost or any other form of PBS).

When _enabling validators to attest to blocks_, things get trickier. To attest to a block, a normal validator would have to execute all transactions in that block... using its EL node. For my project, this can probably be achieved by using some [Reth](https://github.com/paradigmxyz/reth) modules as libraries, but further investigation is needed.

To keep my project tightly scoped, I'll focus on figuring out how to enable validators to _propose empty blocks built externally_. Other features like attesting, building blocks, processing non-empty blocks, and serving beacon API data will be left for later.

The _prototypes_ will be contributions to [Trin](https://github.com/ethereum/trin). I'll keep a tracking issue on the Trin GitHub repository.

## Roadmap

This research has a lot of ramifications, and I expect to adjust my course as I dive deeper into it. This makes it hard to define a stable roadmap, but I think I'll have to follow these steps:

- **Stage 1: Get Blocks**
    - Understand how MEV infrastructure and other forms of PBS send blocks to validators. (I'll focus on Flashbots' MEV-Boost.)
    - Research how can a Portal Client receive blocks from that infrastructure, and code a prototype allowing Trin to do so.
  
- **Stage 2: Engine API**
    - Research what Engine API endpoints are necessary for proposing blocks.
    - Research how to serve the Engine API data using the blocks received in the previous stage.
    - Prototype the relevant Engine API endpoints on Trin.

- **Stage 3: Testing**
    - Research what testing infrastructure is relevant for my prototype. (e.g. Portal hive, Glados, testnets, etc.)
    - Implement all relevant tests.

- **Stage 4: Bonus**
    - Allowing validators to propose empty blocks is my main goal. But there are other things I want to do if I have enough time / after the EPF:
        - Research how to execute transactions from a portal client using Reth modules (to enable attestations).
        - Implement the remaining Engine API endpoints in Trin.
        - Research how to serve Beacon API data from a Portal client + CL client setup.
        - Research how to switch to non-empty blocks.

I aim to complete steps one to three in weeks eight to sixteen of the EPF. I expect to spend the same amount of time on each step, so, three weeks each.

## Possible Challenges

- My main limitation is time. This leaves me at risk of not finishing the project in time if I encounter a delay in any of the proposed stages.

## Goal of the Project

There are three main scenarios where I would consider my project to be successful:

- **Research-only scenario**: My research concludes that the engine API data can't be served from the portal network at its current stage. I write articles explaining why this is the case and what we need to serve it. Those articles woudl help future contributors who want to work on this problem (including myself).
- **Optimal scenario**: I build a working prototype that allows Trin to connect to a CL client. The prototype is well tested and has extensive documentation / good research articles that make it easy for future contributors (including myself) to keep working towards solving the problem.
- **Optimist scenario**: I do everything on the optimal scenario and do significant research on the "bonus" stage of the roadmap.

## Collaborators

### Fellows

- [Daniel Ramirez Chiquillo](https://github.com/danielrachi)

### Mentors

- [Ognyan Genev](https://github.com/ogenev)
- [Piper Merriam](https://github.com/pipermerriam)

Other members of the Trin team have also provided feedback and guidance (but they are not listed as EPF mentors):

- [Jason Carver](https://github.com/carver)
- [Nick Gheorghita](https://github.com/njgheorghita)

## Resources
