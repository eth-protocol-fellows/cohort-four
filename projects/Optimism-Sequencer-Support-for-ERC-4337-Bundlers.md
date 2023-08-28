# Optimism Sequencer Support for ERC 4337 Bundlers
Extension and Implementation of `eth_sendRawTransactionConditional()`

## Summary
Assisting in the completion and testing of the RPC API for Optimism sequencer support for ERC 4337 bundlers, along with designing a robust reputation or Sybil resistance system.

## Motivation
ERC 4337 offers a new account permission design and allows bundlers to perform more advanced transactions, akin to the current cow protocol or Uniswap X. However, there is a lack of RPCs to assist bundlers in making effective operation judgments to avoid unnecessary gas consumption. `eth_sendRawTransactionConditional()` serves as a good tool for this purpose.

## Project Description
The project aims to assist in the best practices for `eth_sendRawTransactionConditional()`, including comprehensive error handling, test cases, and a Sybil resistance system.

## Specification
Based on [this GitHub repository](https://github.com/tynes/go-ethereum/tree/eip4337), attempt to add comprehensive error handling and complete preliminary tests with bundlers. Finally, design a Sybil resistance system, referencing the underlying designs of Optimism, Polygon, Arb, and other Layer 2 solutions.

## Roadmap
- **W6 - W10: Design Phase**: Understand current reputation/Sybil resistance systems and how current Layer 2 solutions complete rollups.
- **W11 - W15: Coding Phase**: Focus on coding the previously designed solutions and complete corresponding test cases.
- **W16: Review Phase**: Complete the project, review documentation, and possibly showcase the work on DevConnect.

## Possible Challenges
Time-consuming research on various Layer 2 solutions and existing reputation systems. Design may not cover all use-cases due to time constraints.

## Goal of the Project
To design `eth_sendRawTransactionConditional()` that can be used on the mainnet and most Layer 2 solutions.

## Collaborators
### Mentors
- Mark
- Yoav

## Resources
1. [GitHub Repository](https://github.com/ethereum/go-ethereum/compare/master...tynes:go-ethereum:eip4337)
2. [EIP-4337](https://eips.ethereum.org/EIPS/eip-4337?ref=blog.oplabs.co)
3. [API-Specification](https://hackmd.io/Jx1B9GLiQ-eltQe7L0FwzQ)
4. [Blog Post](https://blog.oplabs.co/erc-4337-and-account-abstraction/)
