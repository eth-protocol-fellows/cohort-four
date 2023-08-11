# Adedamola's notes

## Ephemery - An Ephemeral Test Network for Stakers

### Aims and Objectives

My "raison d'etat" for joining EPF is to understand ethereum core development, which I have always found intriguing. As a newbie, I am keeping my expectations as low as possible. I hope this is something I will grow into and do for a long time as :)

I have shadowed two projects so far:

* Staker testnets (Ephemery) as suggested by Mario [here](https://github.com/AdedamolaXL/cohort-four/blob/master/projects/project-ideas.md#ephemery-testnet) and;
* Cryptoeconomic models by Barnabe,[here](https://github.com/AdedamolaXL/cohort-four/blob/master/projects/project-ideas.md#rig-opened-problems)

I will focus on Ephemery because I found it easily accessible while staying open to developments within RIG.

Ephemery so far to me is a very low-level(?) project, and the prospect of understanding the intricacies involved in staking, validating, consensus and finality processes is exciting, and I anticipate gaining great insights into how Ethereum actually works!

### Introduction

[Ephemery](https://ephemery.dev/) is an ephemeral test network tailored for staking on Ethereum. Ephemery serves this purpose by providing a test environment for validators to gain experience in staking activities. By simulating real-world staking scenarios on a testnet, validators can familiarize themselves with the intricacies of the staking process, without incurring the risks associated with the mainnet. 

Ephemery design is for it to be an automatic reset network. This unique characteristic allows the test network to undergo periodic resets. These resets revert the network to its original genesis state, effectively erasing all transactions and activities that occurred before the reset point.

This design principle offers Ephemery the following advantages:

* Resource Consumption Reduction: Ephemery's design circumvents the accumulation of historical data on-chain, reducing resource consumption. As a result, stakers can participate in various test scenarios without being burdened by excessive storage requirements. This also reduces the bloat on the Ethereum blockchain, effectively helping it to maintain overall health and scalability.

* Enhanced Test Isolation: The automatic reset feature allows each testing iteration to begin from a clean slate. As a result, any potential interference or influence from previous test runs is completely eliminated, ensuring that each validation cycle remains isolated and independent. This helps validators to isolate issues or errors more effectively and streamline the resolution process.

* Consistent Reproducibility: Ephemery reinstates the network to a known state with every reset. This consistency in the test environment enhances reproducibility, enabling validators to repeat their tests under the same initial conditions, and facilitating accurate performance evaluations and comparisons. This ensures Ephemery is scalable and perfectly optimized to handle an increasing number of test iterations.

### Links
1. [Stakers Testnet](https://notes.ethereum.org/@mario-havel/stakers-testnet)
my notes - 
