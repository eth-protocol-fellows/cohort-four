# Project Template

ETK: Ethereum Object Format (EOF) implementation and more...

## Motivation

The current on-chain EVM bytecode lacks a defined structure, resulting in repetitive JUMPDEST analyses at runtime, thus introducing overhead and stalling feature evolution. 

The EOF, as described by the relevant EIPs, offers a structured and extensible container for the EVM, validated at deploy time, eliminating the need for runtime validation. By doing so, it provides clear separation between code and data. This distinction is crucial for on-chain code validators, like those in layer-2 scaling solutions (e.g., Optimism), allowing for easier implementation, improved reliability, and potential gas savings.

The [EVM Toolkit](https://github.com/quilt/etk) (or ETK) is a collection of tools for creating and analyzing smart contract programs on the Ethereum Virtual Machine. So far it consists of an assembler (eas) and a disassembler (disease). 

The assembler converts human-readable mnemonics (ex. sload, push2) into the raw bytes the EVM interpreter expects and provides some facilities like labels and macros to write highly efficient code in a simple way.

The disassembler does the opposite, converting raw bytes into human-readable mnemonics allowing users to analyze code produced for the EVM in a much more user-friendly language.

Although still in an experimental stage, ETK aims not only to be an assembly language for the EVM, but also an analysis tool (including a tool based on the Z3 theorem proving engine for analyzing EVM bytecode) for advanced users. Keeping its implementation up to date is fundamental if we want to increase its user base and improve the security of the code deployed on the ethereum network.

## Project description

This project aims to implement the Ethereum Object Format (EOF) specification within the ETK language. 
Through our implementation of EOF in ETK, we're advancing the practical application of this specification, fostering more efficient development, heightened security, and ensuring ETK's alignment with the evolving Ethereum landscape.

## Specification

Based on the [“Mega EOF Endgame” Specification](https://notes.ethereum.org/@ipsilon/mega-eof-specification) designed by the Ipsilon team, the EOF format is composed of the following EIPs:

### Ethereum Improvement Proposals (EIPs) Summary:

1. **[EIP-3540](https://eips.ethereum.org/EIPS/eip-3540)**: **EOF - EVM Object Format v1**
   - Introduces a new contract code format for the Ethereum Virtual Machine (EVM) called EVM Object Format (EOF).

2. **[EIP-3670](https://eips.ethereum.org/EIPS/eip-3670)**: **EOF - Code Validation**
   - Focuses on pre-execution code validation.

3. **[EIP-4200](https://eips.ethereum.org/EIPS/eip-4200)**: **EOF - Static relative jumps**
   - Proposes static relative jumps as a new mechanism for code execution.

4. **[EIP-4750](https://eips.ethereum.org/EIPS/eip-4750)**: **EOF - Functions**
   - Introduces the concept of functions within the EOF format.

5. **[EIP-5450](https://eips.ethereum.org/EIPS/eip-5450)**: **EOF - Stack Validation**
   - Addresses stack validation during code execution.

6. **[EIP-6206](https://eips.ethereum.org/EIPS/eip-6206)**: **EOF - JUMPF instruction**
   - Introduces a new instruction for conditional jumps.

7. **[EIP-7480](https://github.com/ethereum/EIPs/pull/7480)**: **EOF - Data section access instructions**
   - Proposes instructions for accessing the data section within the EOF format.

8. **[EIP-663](https://eips.ethereum.org/EIPS/eip-663)**: **Unlimited SWAP and DUP instructions**
   - Proposes the removal of limitations on SWAP and DUP instructions.

9. **[EIP-7069](https://eips.ethereum.org/EIPS/eip-7069)**: **Revamped CALL instructions**
   - Proposes a revision to the CALL instructions.

The document also mentions other proposed changes that do not yet have an assigned EIP, such as contract creation and restrictions on code and gas introspection.

## Roadmap

The first week or week and a half will be devoted to re-reading each of the EIPs that make up the EOF specification and putting together a technical document that specifies the necessary changes, particularities of each EIP and possible problems that may arise in their respective implementations.

Regarding the implementation per se, while it is difficult to predict how long the implementations of each of the EIPs will take (some are trivial and others require a significant amount of work), I estimate that on average, about one week per EIP will be needed (including implementation, extensive individual testing and integration testing). At least in the case of ETK, which is an assembly language and its structure is relatively close to the final program bytecode.

## Possible challenges

- The EOF specification is still in draft status, so it is possible that some changes will be made to it during the development of the project. 
- A bug in a compiler can be a big problem (and it is even worse when the deployed code is immutable). Extensive testing is needed.
- As the spec moves forward day by day, there is not yet a 100% finalized reference implementation in any language to take as a reference.

## Goal of the project

The main goal of this project can be divided into two categories:

- General objectives: To have the first 100% working implementation of EOF in an EVM language.

- Personal objectives: Learn more about compilers/Rust

## Collaborators

### Mentors

[Andrei Maiboroda](https://github.com/gumb0)

## Resources

- [“Mega EOF Endgame” Specification](https://notes.ethereum.org/@ipsilon/mega-eof-specification)
- [EIP-3540: EOF - EVM Object Format v1](https://eips.ethereum.org/EIPS/eip-3540)
- [EIP-3670: EOF - Code Validation](https://eips.ethereum.org/EIPS/eip-3670)
- [EIP-4200: EOF - Static relative jumps](https://eips.ethereum.org/EIPS/eip-4200)
- [EIP-4750: EOF - Functions](https://eips.ethereum.org/EIPS/eip-4750)
- [EIP-5450: EOF - Stack Validation](https://eips.ethereum.org/EIPS/eip-5450)
- [EIP-6206: EOF - JUMPF instruction](https://eips.ethereum.org/EIPS/eip-6206)
- [EIP-663: Unlimited SWAP and DUP instructions](https://eips.ethereum.org/EIPS/eip-663)
- [EIP-7069: Revamped CALL instructions (does not require EOF)](https://eips.ethereum.org/EIPS/eip-7069)
- [ETK](https://github.com/quilt/etk)

## More...

- If all goes well, it is possible that the EOF implementation in the ETK language will be solved in less time than the duration of the EPF. In that case, this same knowledge could easily be extended to other languages.

- Although we have not yet had an in-depth discussion, there is a possibility to collaborate also with the Fe language development team which seems to be in a more research stage regarding the language design (In case this collaboration is fruitful, a new project proposal will be uploaded and linked here).
