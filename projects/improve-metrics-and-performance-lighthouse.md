# Improving Lighthouse metrics / performance

## Motivation

The Ethereum Protocol Fellowship provides an invaluable experience for both learning and contributing to the Ethereum ecosystem. 
Over the past year, I've ventured into the world of blockchain and found myself increasingly captivated by its intricacies.

As a passionate advocate for decentralized technologies, I've had the privilege of engaging with various blockchain protocols through personal
and professional projects, with Ethereum shining as the most mature and compelling among them. 
This sentiment has only grown stronger as I've dedicated more of my time to understanding Ethereum, tackling numerous technical challenges along the way.

I have grown fond of understanding the mechanisms of how the Ethereum clients behave and interact within the network. 
Coupled this with the fact that I am enjoying writing more and more Rust code and contributing as a core developer to the Ethereum ecosystem 
is what motivates me. I also do believe that core developers face some of the most complex technical challenges and I want to be part of it.

In the past, I've closely collaborated on addressing performance issues and latency concerns on some Ethereum nodes. 
In terms of client diversity, it's evident that Rust is poised for increased adoption due to its reputation as one of the most efficient and dependable programming languages available.

Combining my interests in solving performance issues, writing Rust code and the Ethereum ecosystem as a whole, I am excited to be part of the Ethereum Protocol Fellowship and contribute to the Lighthouse client.

## Project Description

As part of trying to improve Lighthouse metric and performance, I will work on several topics including:

1. **Expose the Missed block metrics within the monitored pool of validators**
    - More and more users are interested in having more metrics directly exposed in the CL, especially metrics that can give them more insight about their (pool of) validators and how well they perform. Alerting can easily be added then.
    - They are several areas that we need to consider here (Paul Hauner described in 4 phases [here](https://github.com/sigp/lighthouse/issues/3414)):
        - How do we detect a missed block (a.k.a. a "skipped slot")?
        - How do we know who the proposer was for the skipped slot?
        - How to reduce false-positives.
        - De-bouncing alerts.
      
2. Scheduler analysis
    - Lighthouse has a scheduler called the [BeaconProcessor](https://github.com/sigp/lighthouse/tree/unstable/beacon_node/beacon_processor) which it uses for queuing and quality-of-service.
    - Adding some Prometheus metrics whether it is in a form of a pie-chart style metrics showing which tasks are taking how much percentage of total running time or/and a chart showing the average time per task within time. 

3. Simulated staking performance metrics
    - Adding functionality to Lighthouse to "pretend" to create attestations and retrospectively assess their performance.
    - This would give a lot more datapoints (e.g., a consistent 32 per epoch, rather than 1 per epoch with a single validator) and assist in making qualitative judgements about Beacon Node performance.
    - This would also be able to - in combination of adding metric to the BeaconProcessor - to see potential performance issues or bottleneck and even highlight areas for optimisation and allow the team to more easily play with optimisation (trying different Rust dispatch modes) as well as spotting potential performance issues.

## Roadmap

Weeks 1-3: Implementing Missed block metrics

Weeks 2-4: Implement some metrics in the tasks being scheduled by the [BeaconProcessor](https://github.com/sigp/lighthouse/tree/unstable/beacon_node/beacon_processor)

Weeks 5-10: Implement a simple version of a simulator

weeks 11-12: Testing/Debug the implementation of the above

## Possible challenges

- I am getting more and more familiar with Rust but it’s not my day-to-day language even though I have used another functional language such as Scala. I understand pretty well the Rust concepts but I also know that the borrow checker can be a bit of challenge sometimes and slow me down. Hard learning curve that is.
- Lighthouse code base is not that much a small project and understanding all the aspects of it can take a bit of time.
- I have a good understanding of the first two tasks but I am need a little more research regarding the last project called “Simulated staking performance metric” and how long it would take to complete.

## Goal of the project

The project would be considered when more metrics will be exposed in LH.

Adding the missed blocks for a pool of validators is a good first step to get myself more familiar with the architecture of LH and consists of a first decent challenge as there’s few technical requirements to take into account (eg. understand more components of the code base more information need to be queried from different components of the code (cache, state, etc) making sure that the performance are acceptable.

Then I will be moving to add more metrics in the different tasks scheduled by the `[BeaconProcessor](https://github.com/sigp/lighthouse/tree/unstable/beacon_node/beacon_processor)` which would allow the devs to have a better visibility of the different processing time of each task at runtime.

Then creating a workflow that would allow the devs to simulate different kind of scenarios challenging the performance of their client and allowing them to more easily improve certain part of the code.

## Collaborators

### Mentors
- [Paul Hauner](https://github.com/paulhauner)
- [Michael Sproul](https://github.com/michaelsproul)

## Resources
https://github.com/sigp/lighthouse  
https://github.com/sigp/lighthouse/issues/3414  
https://github.com/sigp/lighthouse/tree/unstable/beacon_node/beacon_processor  