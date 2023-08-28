# Optimism Sequencer Support for ERC 4337 Bundlers
Extension and Implementation of `eth_sendRawTransactionConditional()`

## Summary
The project focuses on enhancing the RPC API for Optimism sequencer support for ERC 4337 bundlers. Unlike other Layer 2 solutions like Arbitrum and Polygon, which only perform checks in the mempool, Optimism performs validation checks both in the mempool and during transaction execution. The project also aims to design a robust reputation or Sybil resistance system, potentially inspired by Flashbots' scoring system.

## Motivation
ERC 4337 introduces a new account permission design and allows bundlers to perform more advanced transactions, similar to existing protocols like the cow protocol or Uniswap X. The project aims to fill the gap in specialized RPCs that assist bundlers in making effective operational decisions, thereby minimizing unnecessary gas consumption. Real-world use-cases from EIP-4337 underscore the need for such specialized tools, especially for bundlers who are not block builders themselves. The completion of this project could significantly reduce losses due to slot collisions and promote more orderly UserOperations across the network.

## Project Description
The project aims to establish best practices for `eth_sendRawTransactionConditional()`. It will include the addition of new error codes and messages tailored for specific scenarios. A comprehensive testing strategy will be employed, involving local Geth test files, Hive, and bundler integration tests.

## Specification
Based on [this GitHub repository](https://github.com/tynes/go-ethereum/tree/eip4337), the project will add comprehensive error handling and complete preliminary tests with bundlers. The Sybil resistance system will be designed after a thorough exploration of the architectures of mainstream Layer 2 solutions like Optimism, Polygon, and Arbitrum. 

### Sybil Resistance System
The design of the Sybil resistance system is still under consideration and will be finalized after exploring the architectures of mainstream Layer 2 solutions. The system may be modeled after Flashbots' scoring system, aiming to provide a robust mechanism against Sybil attacks.

## Roadmap
- **W6 - W10: Design Phase**: The focus will be on understanding current reputation and Sybil resistance systems, as well as the architecture of mainstream Layer 2 solutions. Periodic summaries will be made for each Layer 2 architecture studied.
- **W11 - W15: Coding Phase**: The emphasis will be on coding the previously designed solutions and completing corresponding test cases.
- **W16: Review Phase**: The project will be completed, documentation reviewed, and if possible, the work will be showcased on DevConnect.

## Possible Challenges
The project may face challenges such as time-consuming research and potential limitations due to its aim for maximum compatibility. The solution may exist as a standalone project, similar to Flashbots, rather than being directly applicable to the mainnet's execute layer.

## Goal of the Project
The ultimate goal is to design a universally applicable `eth_sendRawTransactionConditional()` that can be used on both the mainnet and most Layer 2 solutions.

## Collaborators
### Mentors
- Mark
- Yoav

## Resources
1. [GitHub Repository](https://github.com/ethereum/go-ethereum/compare/master...tynes:go-ethereum:eip4337)
2. [EIP-4337](https://eips.ethereum.org/EIPS/eip-4337?ref=blog.oplabs.co)
3. [API-Specification](https://hackmd.io/Jx1B9GLiQ-eltQe7L0FwzQ)
4. [Blog Post](https://blog.oplabs.co/erc-4337-and-account-abstraction/)
