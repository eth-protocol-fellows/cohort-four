# Fuzzing the Dencun protocol changes

## Motivation

For the Ethereum protocol, with its continuous updates and ever-increasing adoption, it is vital to keep it secure. This means identifying and addressing any security flaws before they are discovered and exploited by malicious actors.

Here are the primary reasons why fuzzing is essential in the context of Ethereum:
* It can help identify vulnerabilities that, if exploited, might lead to significant financial losses.
* It can help gain an understanding of the system's constraints, revealing inefficiencies within the protocol that can be optimized.
* It can be more cost-efficient than manual testing, allowing for broad coverage and the automation of testing, leading to quicker detection and resolution of issues.

This project aims to enhance the security of the Ethereum protocol by fuzz testing and improving the tooling to support the upcoming protocol changes, more specifically the [Dencun](https://www.ethereumcatherders.com/dencun/) upgrade.

It is crucial to note that even though fuzzing is a valuable tool in the security testing arsenal, it is not a silver bullet, and it is not guaranteed to find any or all vulnerabilities.

## Project description

The objective of this project is to enhance the existing fuzzers and ensure compatibility with the upcoming [Dencun](https://www.ethereumcatherders.com/dencun/) changes.
[Dencun](https://www.ethereumcatherders.com/dencun/) is a combination of two upgrades including a range of EIPs - Deneb: for the Consensus Layer upgrade, and Cancun, for the Execution Layer upgrade.

* [EIP-4844: Proto-Danksharding](https://eips.ethereum.org/EIPS/eip-4844)
* [EIP-1153: Transient storage opcodes](https://eips.ethereum.org/EIPS/eip-1153)
* [EIP-5656: MCOPY - Memory copying instruction](https://eips.ethereum.org/EIPS/eip-5656)
* [EIP-6780: SELFDESTRUCT only in same transaction](https://eips.ethereum.org/EIPS/eip-6780)
* [EIP-4788: Beacon block root in the EVM](https://eips.ethereum.org/EIPS/eip-4788)
* [EIP-7044: Perpetually Valid Signed Voluntary Exits](https://eips.ethereum.org/EIPS/eip-7044)
* [EIP-6988: Elected block proposer has not been slashed](https://eips.ethereum.org/EIPS/eip-6988)
* [EIP-7045: Increase max attestation inclusion slot](https://eips.ethereum.org/EIPS/eip-7045)

As part of the effort to enhance the tooling, the project will contribute back to the clients and the test suite if any bugs are discovered. By conducting fuzz tests and identifying potential vulnerabilities, the aim is to address edge cases in client implementations and ensure consistent results across them.

## Specification

The upgrade encompasses several EIPs related to the EVM, such as EIP-4844, EIP-1153, EIP-5656, and EIP-6780. The focus of this project is primarily on these changes.

For the testing process, the fuzzing tools I intend to utilize and contribute to are [FuzzyVM](https://github.com/MariusVanDerWijden/FuzzyVM) and [goevmlab](https://github.com/holiman/goevmlab). Both of these tools are written in Go and rely on several major libraries, notably [go-ethereum](https://github.com/ethereum/go-ethereum) and [go-fuzz](https://github.com/dvyukov/go-fuzz)

1. Execute fuzz tests to pinpoint potential limitations in the tools, given that there are not many documented issues.

2. Add support in [FuzzyVM](https://github.com/MariusVanDerWijden/FuzzyVM) for testing the [Dencun](https://www.ethereumcatherders.com/dencun/) changes and respectively the necessary changes in [goevmlab](https://github.com/holiman/goevmlab).

3. [goevmlab](https://github.com/holiman/goevmlab) currently lacks support for the Reth evm. This presents a potential area for enhancement. There are also issues not particularly related to the [Dencun](https://www.ethereumcatherders.com/dencun/) upgrade that can be addressed:
  * https://github.com/holiman/goevmlab/issues/12
  * https://github.com/holiman/goevmlab/issues/4

4. Execute differential fuzz tests against several clients: [geth](https://github.com/ethereum/go-ethereum), [erigon](https://github.com/ledgerwatch/erigon), [nethermind](https://github.com/NethermindEth/nethermind), [besu](https://github.com/hyperledger/besu) and [reth](https://github.com/paradigmxyz/reth) to identify any client inconsistencies.

5. If bugs are discovered, contribute fixes back to the clients.

6. Improve the [tests](https://github.com/ethereum/tests) to cover edge cases, especially if the fuzzing results indicate crashes or other unexpected behaviors.


## Roadmap

Many unknown factors can affect the project's timeline, such as the complexity of the necessary changes, the time taken to familiarize with the existing codebase and the number of bugs discovered. The timeline provided below is a tentative estimate.

**Implementation & Fuzzing**

1. Implement the necessary changes into the existing fuzzing tools - **4 weeks**
2. Conduct fuzz tests and identify limitations of the tools - **4 weeks**
3. Contribute back to the clients and tests if any bugs are discovered - **ongoing**

**After the EPF ends**

1. Implement enhancements based on any issues encountered during the fuzzing process - **ongoing**

## Possible challenges

* Exploring the changes of the upcoming protocol update is time-consuming and requires a deep understanding of the Ethereum protocol.
* The client teams are still working and have [different progress](https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/cancun.md#implementation-progresss) on implementing the changes that are going to be tested.
* The fuzzing tools depend on existing infrastructure that does not fully support the changes. For example, the [state tests](https://github.com/ethereum/tests/tree/develop/GeneralStateTests) format does not reflect the changes yet.
* Finding vulnerabilities might be time-consuming and is not guaranteed.

## Goal of the project

The project will be considered successful if, by the end of the EPF, actual bugs are found or contributions to existing fuzzing tools, clients, or tests are made.

## Collaborators

### Fellows 

* [Radosvet M](https://github.com/radkomih)

### Mentors

* [Fredrik Svantes](https://github.com/fredriksvantes)

## Resources

Project repo
* [fuzzetha](https://github.com/radkomih/fuzzetha)

Fuzzing tools
* [FuzzyVM](https://github.com/MariusVanDerWijden/FuzzyVM)
* [goevmlab](https://github.com/holiman/goevmlab/)

Tests and test tools
* [tests](https://github.com/ethereum/tests)
* [retesteth](https://github.com/ethereum/retesteth)
* [hive](https://github.com/ethereum/hive)

EL specs
* [execution specs](https://github.com/ethereum/execution-specs)

EL clients
* [geth](https://github.com/ethereum/go-ethereum)
* [erigon](https://github.com/ledgerwatch/erigon)
* [nethermind](https://github.com/NethermindEth/nethermind)
* [besu](https://github.com/hyperledger/besu)
* [reth](https://github.com/paradigmxyz/reth)
