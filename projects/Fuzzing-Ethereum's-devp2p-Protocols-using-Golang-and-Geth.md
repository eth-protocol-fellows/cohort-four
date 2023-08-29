# Fuzzing Ethereum's devp2p Protocol

(…work in progress, i will be still editing it as time goes on)

### Create fuzzers for the ethereum devp2p protocol using golang in order to find potential vulnerabilities


## Introduction:

The Ethereum Protocol Fellowship provides aspiring protocol developers like myself a pathway to gaining the experience needed to make meaningful contributions to the core Ethereum protocol. For the EPF I chose to contribute to geth, an Ethereum execution client implementation written in go-lang.

The Ethereum network is a vital platform in the world of decentralized applications. However, as a widely-used blockchain, it's a prime target for potential security breaches. The devp2p protocols play a critical role in facilitating communication between Ethereum nodes, making them an important area to focus on to enhance network security. This proposal aims to develop fuzzers using the Go programming language to identify vulnerabilities and potential issues in the Ethereum network's devp2p protocols.

## Motivation:
Securing the Ethereum network is paramount to maintain its integrity and protect against potential attacks. Vulnerabilities or bugs in the devp2p protocols could lead to disruptive issues or even compromise the entire network. By using fuzzers, we can simulate various scenarios, identify unexpected behaviors, and uncover vulnerabilities that might not be apparent through traditional testing.
## Project Scope:
The project's objective is to create a suite of fuzzers using the Go programming language to test the Ethereum network's devp2p protocols. These fuzzers will generate and send randomized or specified payloads to the network to trigger potential vulnerabilities. The Geth client, a widely-used Go implementation of Ethereum, will be used to interact with the devp2p protocols and conduct the fuzzing tests.

## Specification
I am still working on how to implement my solution which will include the details of technical information on the project.

## Challenges:

- Understanding devp2p: Gaining a deep understanding of the devp2p protocols and their interactions will be crucial for effective fuzzing.

- Effective Fuzzing: Designing fuzzers that can generate relevant inputs to expose vulnerabilities will require careful consideration and testing.

## Project Success:
### The project will be deemed successful if, by the end of the proposal period:

- The fuzzers can successfully interact and run on Ethereum and the devp2p protocols.

- The fuzzing process reveals unexpected behaviors, crashes, and potential vulnerabilities in the devp2p protocols even if it doesnt find vulnerabilities, it will also be considered as a sucess.

*The end of the epf will not necessarily mark the end of this project, it will always be available and will always be able to receive
contributions.
Update of the project can be necessary over time to keep the tool working great with network upgrades.*

## Future Prospects:
The developed fuzzers and testing methodologies will remain valuable tools for ongoing security assessments of the Ethereum network. Regular updates and enhancements will be required to adapt to network upgrades and changes in the devp2p protocols.

### Collaborators

#### Fellow: 
* [Adaaku Peter](https://github.com/scarfacedotcom)

#### Mentors:
* [Marius Van Der Wijden](https://github.com/MariusVanDerWijden)
* [Dev Longs](https://github.com/devlongs)

#### Additional Collaborators: 

Non for now, interested in collaborating?? hit me up here: [Adaaku Peter](https://www.twitter.com/scarfacedotsol)

### Resources
- [Geth](https://github.com/ethereum/go-ethereum)
[Devp2p Specifications] (https://github.com/ethereum/devp2p)
The project's repo (to be added)

* [Devp2p Specification](https://github.com/ethereum/devp2p)
* [Official Go implementation of the Ethereum protocol](https://github.com/ethereum/go-ethereum)
* https://github.com/MariusVanDerWijden/FuzzyVM
* https://github.com/MariusVanDerWijden/tx-fuzz
* https://github.com/MariusVanDerWijden/merge-fuzz
#### Martin from geth team
* https://github.com/holiman/txparse
* https://github.com/holiman/goevmlab/tree/master
* The project’s repo (to be added)

## Conclusion:
By harnessing the power of fuzzing and using Golang to develop fuzzers that interact with Geth's devp2p protocols, this project aims to bolster the security of the Ethereum network. Identifying vulnerabilities through targeted fuzzing will enable the Ethereum community to proactively address potential threats, ensuring the robustness and longevity of the Ethereum ecosystem.
