Fuzzing the Ethereum network (devp2p)

Create fuzzers for the devp2p protocols in order to find potential vulnerabilities.

## Motivation

In order to ensure the good running of Ethereum, it is imperative that it remain highly secure. As a large blockchain, Ethereum represents a target for potential hackers.

The Ethereum network and the different protocols of the devp2p play an essential role in enabling communication between nodes, which is an essential element for the operation of the protocol.

Vulnerabilities or errors in this network could cause significant problems. It is therefore crucial to guarantee the maximum security of the network and exchanges between nodes.

To avoid that, ethereum contributors have developed a lot of tools, including fuzzers.

Fuzzer programs are programs that provide invalid, unexpected, or random data as inputs to a computer program. The program is then monitored for exceptions such as crashes, failing built-in code assertions, or potential memory leaks.

Here is a list (thanks to [Fredrik](https://github.com/fredriksvantes)) of different fuzzers made by Ethereum contributors:

https://github.com/MariusVanDerWijden/tx-fuzz

https://github.com/MariusVanDerWijden/FuzzyVM

https://github.com/holiman/goevmlab/

https://github.com/infosecual/nosy

https://github.com/ethereum/c-kzg-4844/tree/main/fuzz

https://github.com/jtraglia/kzg-fuzz

https://github.com/sigp/beacon-fuzz

https://github.com/infosecual/wormtongue

One thing we can notice is that there is no (I didn't find any) fuzzer interacting with the devp2p using an execution client and only one interacting with the devp2p using prysm.


## Project description

To increase security, I propose the creation of fuzzers, with the aim of potentially spotting vulnerabilities and bugs present on the Ethereum network and clients implementing the devp2p.

The project was originally proposed by [Fredrik](https://github.com/eth-protocol-fellows/cohort-four/blob/master/projects/project-ideas.md#fuzzing).

Fuzzers can build and send random or specified payloads over devp2p. The goal is to find potential triggers for DoS vectors and crashes. The fuzzers will run on a private network and testnet to not disturb the operation of ethereum.
Doing this can help with:
- Testing network upgrades
- Testing the devp2p implementations of clients
- cause unexpected behavior such as crashes, memory leaks, and others.


These behaviors will then be reported in order to be able to correct them and secure the network.




## Specification


The realization of my solution requires the sending of messages using the fuzzers that I will develop. The process is broken down into two fundamental steps:
Connect to the Ethereum network and send messages.
Develop different fuzzers and send malicious inputs to the network.


To build the solution, I chose to use the Go programming language.
Go is a good solution for the development of fuzzer, he has great performance. Performance is a key for fuzzers : they need to generate and send a great quantity of inputs. Go has other advantages like a good ecosystem, security of memory, easy learning...

Then, in order to connect to the different protocols that form the devp2p, I had to choose between two options:

- implement the devp2p specifications myself in order to connect to the Ethereum network.
- use and edit an existing implementation of devp2p.

For time reasons, I decided to choose the second option:

I chose to use the Geth project.
Why geth? for several reasons:
- Geth is an implementation of ethereum in Go, the same language I chose to use for the development of fuzzers. This will allow me to use a single language.
- Geth is fast and very efficient; it will allow me to spam with my fuzzers.
- The documentation for Geth is well detailed.
- Geth is appreciated by the Ethereum community and has many tools and projects that can help me with this project.

So once I have correctly integrated the devp2p implementation by modifying the geth source code to send custom messages, I will be able to communicate through the Ethereum network and be able to start integrating my fuzzers.

For the fuzzing, there are a lot of fuzzing techniques; the goal will be to identify the most appropriate, integrate them in priority, and then use the maximum number of different techniques in order to have the most results.

For the fuzzing test I will send messages on a private network. This will allow me to test the  reactions to fuzzing and potentially detect issues on the devp2p or issues that are specific to the nodes (example: a message crashes a node using geth but the same message does not cause anything on reth).


## Roadmap

Over the remaining 3 months of the EPF, here is how I divided the work:

First month:

The first month will be devoted to the development of a custom geth node to interact with the devp2p, research on the specifications of the various devp2p protocols, and the development of the first fuzzers.
The goal will be to connect to the ethereum network and send messages using fuzzers.

The last two months:

The last two months will be devoted to the study of the results obtained by the fuzzers in order to determine which other fuzzing techniques could be useful.
And the development of additional fuzzers, including more advanced fuzzers.

## Possible challenges

The first challenge will be to have a good understanding of devp2p and the messages exchanged between the nodes.
Then, integrate and modify correctly the network part of Geth to send malicious messages.

The second problem I could encounter is finding security vulns via fuzzers. Using fuzzers does not necessarily imply the possibility of finding vulns and bugs; it will be up to me to develop good fuzzers and use the appropriate techniques to achieve this.

In order to overcome these problems, I intend to invest myself and spend time on the development of this project. I intend to dedicate between 50 and 60 hours per week to it.

## Goal of the Project

The goal of the project is to contribute to the security aspect of Ethereum by sending malicious messages on the Ethereum network.
in order to find potential security vulnerabilities or bugs and to test if the devp2p and networks updates are correclty implemented by nodes.

The project will be considered successful if, by the end of the EPF, the tool is working and can run fuzzing on network upgrades.


The end of the EPF will not necessarily mark the end of this project; it will always be available and will always be able to receive contributions. 
An update to the project can be necessary over time to keep the tool working great with network upgrades.

Personally, my goal is to contribute to the security of ethereum, so continuing to contribute might interest me in the future.

## Collaborators

### Fellows 

- [Mohas](https://github.com/mohasdev) 

### Mentors

- [Fredrik Svantes](https://github.com/fredriksvantes)
- [Marius van der Wijden](https://github.com/MariusVanDerWijden)


## Resources

- [D4C (project repo)](https://github.com/mohasdev/D4C)
- [Geth](https://github.com/ethereum/go-ethereum)
- [Devp2p Specifications](https://github.com/ethereum/devp2p)