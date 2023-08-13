# Fuzzing the Ethereum network

Create fuzzers for the ethereum network in order to find potential vulnerabilities .

## Motivation

In order to ensure the good running of Ethereum, it is imperative that is remains highly secure. As a large blockchain, Ethereum represents a target for potential hackers. 

The Ethereum network and the differents protocols of the devp2p, plays an essential role in enabling communication between nodes, an essential element for the operation of the protocol. 

Vulnerabilities or errors in this network could cause significant problems. It is therefore crucial to guarantee the maximum security of the network and exchanges between nodes.

## Project description

To increase security, I propose the creation of fuzzers, with the aim of potentially spotting vulnerabilities and bugs present on the Ethereum network and clients implementing the devp2p.

The project was originally proposed by [Fredrik](https://github.com/fredriksvantes).

The fuzzers will allow arbitrary/specific data to be sent to the various ethereum nodes through its network to cause unexpected behavior such as crashes, memory leaks and others...

These behaviors will then be reported in order to be able to correct them and secure the network.

## Specification


The realization of my solution requires sending of messages using the fuzzers that I will develop. The process is broken down into two fundamental steps:
- Connect to the ethereum network and send messages
- Develop different fuzzers and send malicious inputs to the network.


To build the solution I choosed to use the Rust programming language :
Rust is a good solution for the development of fuzzer, he have great performance. Performance is a key for fuzzer, they need to generate and send a great quantity of inputs . Rust have other advantages like a good ecosystem, security of memory...

Then in order to connect to the different protocols that form the devp2p I had the choice between two options:

- implement the devp2p specifications myself in order to connect to the ethereum network
- use and edit an existing implementation of the devp2p.

For time reasons I decided to choose the second option:

I chose to use the reth project, specifically the network module of reth .
Why reth? for several reasons :
- reth is an implementation of ethereum in rust , the same language I chose to use for the development of fuzzers this will allow me
to use a single language.
- reth is fast and very efficient, it will allow me to be able to spam with my fuzzers.
- the documentation of reth, especially on the network part (network crate) is well detailed.

So once I have correctly integrated the devp2p implementation by modifying the network component of reth , I will be able to
communicate through the ethereum network and be able to start integrating my fuzzers.

For the fuzzing, there are a lot of fuzzing techniques, the goal will be to identify the most appropriate to integrate them in priority and then to use the maximum of different techniques in order to have the most results.

For the fuzzing test at first I will start by sending messages on a private network, the nodes will use reth. This will allow me to test the first reactions to fuzzing, and to potentially detect issues on the devp2p or issues that are specific to reth.

Then once I have tested this well I plan to launch my fuzzing directly on a testnet in order to interact with other nodes, which will use other implementations of ethereum. This could make it possible to find vulnerabilities on the devp2p but also other vulns specific to various implementations of ethereum (example: a message crashes a node using geth but the same message does not cause anything on reth).

## Roadmap

Over the remaining 3 months of the epf, here is how I divided the work:

First month :

The first month will be devoted to the implementation of devp2p using reth, research on the specifications of the various devp2p protocols as well as to the development of first fuzzers.
The goal will be to connect to the ethereum network and send messages using fuzzers.

The last two month :

The last two months will be devoted to the study of the results obtained by the fuzzers, in order to determine which other fuzzing techniques could be useful.
And the development of additional fuzzers including more advanced fuzzers.

## Possible challenges

The first challenge will be to have a good understanding of devp2p and the messages exchanged between the nodes.
Then to integrate and modify correctly the network part of reth to send messages.

The second problem I could encounter is finding security vulns via fuzzers, using fuzzers does not necessarily imply the possibility of finding vulns and bugs, it will be up to me to develop good fuzzers and use the appropriate techniques to achieve this.

In order to overcome these problems I intend to invest myself and spend time on the development of this project, I intend to dedicate between 50 and 60 hours per week to it.

## Goal of the project

The goal of the project is to contribute to the security aspect of ethereum by sending malicious messages on the ethereum network
in order to find potential security vulnerabilities or bugs.

The project will be considered successful if by the end of the epf he will have managed to find some.

The end of the epf will not necessarily mark the end of this project, it will always be available and will always be able to receive
contributions.

Personally my goal is to contribute to the security of ethereum, so continuing to contribute might interest me in the future :)

## Collaborators

### Fellows 

- [Mohas](https://github.com/mohasdev) 

### Mentors

- [Fredrik Svantes](https://github.com/fredriksvantes)
- [Georgios Konstantopoulos](https://github.com/gakonst)

## Resources

- [Reth](https://github.com/paradigmxyz/reth)
- [Devp2p Specifications](https://github.com/ethereum/devp2p)
- The project's repo (to be added)