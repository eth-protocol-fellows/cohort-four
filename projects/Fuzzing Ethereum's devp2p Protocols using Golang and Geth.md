# Fuzzing Ethereum's devp2p Protocol

(…work in progress, i will be still editing it as time goes on)

### Create fuzzers for the ethereum devp2p protocol using golang in order to find potential vulnerabilities


## Introduction:

The Ethereum Protocol Fellowship provides aspiring protocol developers like myself a pathway to gaining the experience needed to make meaningful contributions to the core Ethereum protocol. For the EPF I chose to contribute to geth, an Ethereum execution client implementation written in go-lang.

The Ethereum network is a vital platform in the world of decentralized applications. However, as a widely-used blockchain, it's a prime target for potential security breaches. The devp2p protocols play a critical role in facilitating communication between Ethereum nodes, making them an important area to focus on to enhance network security. This proposal aims to develop fuzzers using the Go programming language to identify vulnerabilities and potential issues in the Ethereum network's devp2p protocols.

## Motivation:
Securing the Ethereum network is paramount to maintain its integrity and protect against potential attacks. Vulnerabilities or bugs in the devp2p protocols could lead to disruptive issues or even compromise the entire network. By using fuzzers, we can simulate various scenarios, identify unexpected behaviors, and uncover vulnerabilities that might not be apparent through traditional testing.

The project was originally proposed by [Fredrik](https://github.com/eth-protocol-fellows/cohort-four/blob/master/projects/project-ideas.md#fuzzing).

and he listed out different fuzzers made by Ethereum contributors, this include the following:

https://github.com/MariusVanDerWijden/tx-fuzz

https://github.com/MariusVanDerWijden/FuzzyVM

https://github.com/holiman/goevmlab/

https://github.com/infosecual/nosy

https://github.com/ethereum/c-kzg-4844/tree/main/fuzz

https://github.com/jtraglia/kzg-fuzz

https://github.com/sigp/beacon-fuzz

https://github.com/infosecual/wormtongue

## Project Scope:
The project's objective is to create a suite of fuzzers using the Go programming language to test the Ethereum network's devp2p protocols. These fuzzers will generate and send randomized or specified payloads to the network to trigger potential vulnerabilities. The Geth client, a widely-used Go implementation of Ethereum, will be used to interact with the devp2p protocols and conduct the fuzzing tests.

## Specification

### Solution Realization
The successful execution of my solution involves two fundamental stages, each integral to the process:

1. Network Connection and Message Transmission: The implementation entails establishing a connection with the Ethereum network and sending various types of messages.

2. Fuzzer Development and Message Injection: The creation of distinct fuzzers, each designed to send potentially malicious inputs to the Ethereum network, forms the core of the project.

### Choice of Programming Language

For the project, I opted for the Go programming language due to its favorable attributes. Go boasts exceptional performance, a critical factor for fuzzers that need to generate and transmit a high volume of inputs. Additionally, Go's ecosystem, memory security features, and user-friendly learning curve make it a fitting choice.

### Interaction with devp2p Protocols

In order for me to interact with the devp2p protocols, i will be Utilizing and modifying an existing devp2p implementation for seamless integration.


My choice landed on,  [Geth](https://github.com/ethereum/go-ethereum), the Official Go implementation of the Ethereum protocol a noteworthy implementation of Ethereum in Go. Several compelling reasons support this choice:

- Geth aligns with the Go language I've chosen for fuzzer development, promoting language uniformity.
- Its speed and efficiency promise optimal performance, crucial for the successful execution of fuzzers.
- Geth benefits from well-documented resources that simplify the integration process.
- Geth enjoys recognition within the Ethereum community, offering invaluable resources and projects for support.

Integration will involve customizing the Geth source code to incorporate devp2p interactions, thereby enabling communication through the Ethereum network and enabling integration with my fuzzers.

### Fuzzing Strategies

The fuzzing phase encompasses diverse strategies, with the objective of identifying the most suitable techniques. Prioritizing these techniques will be essential, followed by the incorporation of multiple approaches to maximize results.

### Testing Environments

The initial phase of fuzzing will transpire within a controlled environment: a private network. 

This controlled setting facilitates rigorous testing of the response to fuzzing and potential identification of devp2p issues, as well as node-specific concerns.

With a well-tested private network phase, the project advances to the subsequent stage:

The transition to public testnets, where my fuzzers will interact with various nodes employing distinct Ethereum implementations.

## Project Roadmap
### Phase 1: Project Setup and Preparation
Duration: 2 weeks

1. ### Project Familiarization:

    - Deeply understand Ethereum's devp2p protocols and their interactions.
    - Review existing fuzzing techniques and frameworks.
2. ### Environment Setup:

    - Set up the development environment with Go programming tools and dependencies.

### Phase 2: Integration with Geth and Initial Fuzzer Development
Duration: 4 weeks

1. ### Geth Integration:

    - Analyze Geth's source code and identify key areas for devp2p protocol integration.
    - Modify Geth's source code to establish communication through devp2p protocols.
2. ### Basic Fuzzer Development:

    - Implement a basic fuzzer that sends random payloads as messages.
    - Ensure the basic fuzzer successfully connects to the Ethereum network and interacts with nodes.

### Phase 3: Advanced Fuzzer Development and Initial Testing
Duration: 6 weeks

1. ### Fuzzer Enhancements:

    - Develop multiple fuzzers, each focusing on specific parts of the devp2p protocols.
    - Implement payload generation techniques, including valid and malformed inputs.
2. ### Fuzzer Integration with Geth:

    - Integrate advanced fuzzers with the modified Geth implementation.
    - Enable the fuzzers to send custom messages to the Ethereum network.
3. ### Private Network Testing:

    - Set up a private Ethereum network for controlled testing.
    - Run fuzzers against the private network to identify initial issues, crashes, or vulnerabilities.
### Phase 4: Public Testnet Fuzzing and Analysis
Duration: 8 weeks

1. ### Public Testnet Setup:

    - Configure connections to public Ethereum testnets.
    - Ensure proper synchronization with existing nodes on the testnet.
1. ### Fuzzer Deployment on Public Testnet:

    - Deploy fuzzers on the public testnet to interact with other nodes.
    - Monitor and analyze the behavior of nodes in response to fuzzed inputs.
1. ### Behavior Analysis and Issue Detection:

    - Develop mechanisms to capture and analyze the behavior of the Ethereum nodes during fuzzing.
    - Identify unexpected behaviors, crashes, and potential vulnerabilities.
### Phase 5: Reporting and Documentation
Duration: 3 weeks

1. ### Vulnerability Reporting:

    - Document any vulnerabilities or unexpected behaviors uncovered during the fuzzing process.
    - Include details about triggering inputs, potential impacts, and mitigation strategies.
1. ### Fuzzer Documentation:

    - Create comprehensive documentation for each fuzzer, including setup instructions and usage guidelines.
    - Document the integration process with the modified Geth implementation.
### Phase 6: Future-Proofing and Project Conclusion
Duration: 2 weeks

1. ### Adaptability and Maintenance:

    - Ensure that the fuzzers and testing framework are adaptable to changes in devp2p protocols and Geth updates.
    - Plan for ongoing maintenance and updates to keep the fuzzers effective.
1. ### Community Engagement:

    - Share project outcomes, findings, and documentation with the Ethereum community.
    - Encourage contributions and collaboration to enhance and extend the fuzzers.
1. ###  Final Project Evaluation:

    - Review project objectives against achieved results.
    - Ensure that the project's goals have been met and that the developed fuzzers contribute to Ethereum's security.

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