# Fuzzing the EVM

## Motivation

For the Ethereum protocol, with its continuous updates and ever-increasing adoption, it is vital to keep it as secure as possible by identifying and addressing any security flaws before they are discovered and exploited by malicious actors. This project aims to enhance the security of the Ethereum protocol by fuzz-testing its various aspects. Fuzzing is a software testing method that has proven essential in other domains; it involves providing invalid, unexpected, or random inputs to a computer program to uncover bugs or other vulnerabilities.

Here's why it is essential in the context of Ethereum:

* **Preventing Financial Loss** - Fuzzing can help identify vulnerabilities that, if exploited, can lead to significant financial losses.
* **Performance Optimization** - Fuzzing can help gain an understanding of the system's constraints, revealing inefficiencies within the protocol that can be optimized.
* **Cost-Efficient Testing** - Fuzzing can be more cost-efficient than manual testing, allowing for broad coverage and the automation of testing, leading to quicker detection and resolution of issues.

It is crucial to note that even though fuzzing is a valuable tool in the security testing arsenal, it is not a silver bullet, and it is not guaranteed to find any or all vulnerabilities.

## Project description

The goal of the project is to create a set of tools and gradually advance them by incorporating various fuzzing techniques and capabilities. These will be used for identifying vulnerabilities in different parts of the protocol, with a focus on the latest protocol changes. The project will start with the execution layer, specifically the EVM, but the design should be configurable and can later be extended to support other parts of the protocol. The main target is to test minority clients (`Reth/Erigon/...`), which may have more issues, as well as majority clients to ensure that they are not vulnerable to the same problems. As part of the effort to improve the security of the Ethereum protocol, the project will aim to contribute back to the clients/specs if any bugs are found and to enhance existing fuzzing tools.

## Specification

Implement a set of CLI tools to test the newer protocol upgrades, that could exploit vulnerabilities in the Ethereum Virtual Machine.

Here's a breakdown of the steps that might be required to implement the solution:
1. Generate a valid corpus, based on existing data from specs, unit tests, real-world data, or newer protocol upgrades as a starting point.
2. Mutate the corpus and generate new inputs that are arbitrary, but still hold the structure as the original inputs to cover deep code paths of the protocol.
3. Report the inputs that cause crashes or other unexpected behavior.
4. Track the code coverage and identify areas that are not covered.

## Roadmap

**Local test setup**

1. Set up a local private network for testing - **~2-4 days**

**CLI implementation & Fuzzing**

1. Use existing fuzzing tools and identify their limitations and aspects of the protocol that are not covered - **~2 weeks**
2. Implement custom CLI tools to fuzz the newer protocol changes and identify critical areas within Ethereum to target - **~4 weeks**
3. Use the custom tools to fuzz test - **~4 weeks**
4. Contribute back to the clients/specs if any bugs are found - **ongoing**

**Improvements - after the EPF end**

1. Analyze issues encountered during fuzzing - **ongoing**
2. Implement enhancements based on findings - **ongoing**

## Possible challenges

* Setting up a proper testing environment that accurately resembles real-world scenarios for different client combinations may be challenging.
* Finding vulnerabilities might be time-consuming and is not guaranteed.

## Goal of the project

The project will be considered successful if, by the end of the EPF, actual bugs are found or contributions to existing fuzzing tools, clients, or specs are made.

## Collaborators

### Fellows 

* [Radosvet M](https://github.com/radkomih)

### Mentors

* [Fredrik Svantes](https://github.com/fredriksvantes)

## Resources

Project repo:
* [fuzzetha](https://github.com/radkomih/fuzzetha)

Existing fuzzing tools:
* [goevmlab](https://github.com/holiman/goevmlab/)
* [FuzzyVM](https://github.com/MariusVanDerWijden/FuzzyVM)
* [txparse](https://github.com/holiman/txparse)