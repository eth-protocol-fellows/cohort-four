# The Attestation Aggregation and Packing Optimisation Project for Lighthouse

Optimal Attestation Packing in Lighthouse 

## Motivation

Attestation packing is the process by which Ethereum consensus clients chose the attestations to include in a block. This is a topic that client teams did significant work on even prior to the Merge because the block proposer's rewards are directly affected by how closely the packed attestations match the canonical chain. Currently, Lighthouse implements a greedy strategy for deciding which attestations the proposer includes in the block. This leads to near optimal solutions in many cases, but there are outliers that do not have a known lower bound on quality. For instance, during testing the Lighthouse team and Satalia found an instance where the performance of the greedy strategy was about 60% of the optimal solution. And over the course of an 8 day data collection period the greedy algorithm was about 0.26 ETH lower than the optimal attestation packing reward. Our project seeks to remedy the situation by implementing
an optimal attestation packing algorithm that runs in production at least for stronger machines. 

## Project description

After the great work of Sigma Prime and Satalia during their collaboration on the topic, we propose implementing their solution to maximal clique enumeration for attestation aggregation, as well as an improved maximum coverage algorithm that takes advantage of the structure of the problem.

## Specification

We will implement our solution in two stages:

#### Aggregation
For the aggregation stage we will port Satalia's pure Rust implementation of the Bron-Kerbosch algorithm to the Lighthouse codebase. We will remove the current greedy aggregation steps that occur on insertion into the operation pool. When called upon to construct the block we will use the Bron-Kerbosch algorithm on the set of valid aggregate attestations in the operation pool to create a restricted set of attestaitons that is optimality preserving. Then we will aggregate the unaggregated attestations that can be aggregated to each aggregate in the resulting set. And add aggregate attestations formed by the unaggregated attestations that weren't represented by the aggregated attestations set. Finally, we will use this set as input to the max coverage algorithm for packing.

#### Packing
The packing stage is an instance of the Weighted Maximum Coverage Problem (WMCP), which is known to be NP-hard. To solve this, Satalia's papers present a solution where the problem is framed as a Mixed Integer Problem (MIP). Then, the solution can be computed via two approaches, either by using a well-known, free MIP solver (eg: CBC, SCIP) or a custom solver based on the branch-and-bound algorithm. The former approach is termed by Satalia as the 'decomposition approach', while the latter as the 'enumeration approach'. The papers also suggest a few stragegies to optimise the performance of each. We plan to implement both of these approaches over the course of the project, optimise each to the best of our abilities, and ulitmately choose the one that performs better.
    The final implementation would also allow for the user to choose between the available approaches - the existing greedy implementation and the two new approaches.

## Roadmap

<u>Week 1-2:</u>\
Port the initial algorithms into Lighthouse from SigP and Satalia repo.
__Aggregation__: Implement a first pass. \
__Packing__: Implement a first pass.

<u>Week 3-4:</u>\
__Aggregation__: Set up some nodes to produce blocks every slot to test the validator rewards and performance. Implement changes as necessary. 
__Packing__: Implement the Decompostion Approach by splitting the problem into smaller subproblems (each solvable in exponential time), and then combining the solutions to the subproblems to get the solution to the original problem (in linear time).

<u>Week 5:</u> \
__Aggregation__: Clean up code as much as possible and test some more. Then if the tests are positive, we hopefully merge. And that will end the attestation aggregation section. 
__Packing__: Explore Optimisations to the Decomposition Approach. These include calculating the states of the dynamic programming algorithm in parallel, trying out different MIP solvers (CBC vs SCIP) etc.

<u>Week 6-7:</u> \
__Packing__: Implement the Enumeration Approach by using the branch-and-bound algorithm to enumerate all the possible solutions to the problem.

<u>Week 8-10</u> \
__Packing__: Benchmark the two approaches, identify bottlenecks and optimise the code as much as possible. Then, if the tests are positive, we hopefully merge.

## Possible challenges

The major challenge that presents itself is the performance of the max coverage algorithm, as it is a known NP-hard problem. To write an implementation that performs well enough in a production environment given the small window for attestation packing, will require patience and iteration. We hope to write an implementation that works even for normative devices so we will have to do a lot of testing.

## Goal of the project

Complete success for the project would be an optimal attestation packing implementation that runs in production by default for Lighthouse. A slightly less successful result would be an optimal solution turned on by a cli flag for powerful machines, and a better (but not necessarily optimal) solution to attestation packing for computationally constrained devices.

## Collaborators

[Ankur Dubey](https://github.com/ankurdubey521) and [Geemo Candama](https://github.com/GeemoCandama)

### Fellows 

[Ankur Dubey](https://github.com/ankurdubey521) and [Geemo Candama](https://github.com/GeemoCandama)

### Mentors

[Michael Sproul](https://github.com/michaelsproul) and [Paul Hauner](https://github.com/paulhauner)

## Resources
Presentation: [Optimizing Attestation Aggregation and Packing](https://docs.google.com/presentation/d/1uigrSd6j57fhsTWpcQX2cYnSTgUwWP6z6RLy0UH9xYQ/edit?usp=sharing) \
Aggregation: https://github.com/sigp/lighthouse/pull/4507 \
Packing: https://github.com/sigp/lighthouse/pull/4542 \
Previous Work: \
https://lighthouse-blog.sigmaprime.io/docs/satalia-01-problem-definition.pdf \
https://lighthouse-blog.sigmaprime.io/docs/satalia-02-exact-approaches.pdf \
https://lighthouse-blog.sigmaprime.io/docs/satalia-03-results.pdf \
https://github.com/michaelsproul/optimising-attestation-packing-satalia
