# Verkle Tree Library in Nim

Implementation of verkle tree in Nim, which will be further used to implement the state tree in the Nimbus client, and transition it from a Merkle Patricia Tree to a Verkle Tree.

## Motivation
It can help Ethereum achieve statelessness! The key benefit of the vector commitments used in Verkle is that they allow for much smaller proof sizes (called witnesses). Instead of needing to provide hashes of all "sibling nodes" at each level, as in Merkle Trees, the prover needs only to provide all parent nodes (plus an extra proof, called an optional) along the paths from each leaf node to the root. Since we no longer need to provide all sibling nodes, we can structure Verkle Tries to be much wider than Merkle Trees. All of this allows for much smaller witness sizes. 
Large witnesses are the key problem standing in the way of statelessness. When witnesses (proofs) are small enough, they can be contained within each block. This allows for the verification of any block using only what’s contained within the block itself.

## Project description
Verkle Trees are a type of data structure similar to Merkle Patricia Trees (MPT), which is the data structure used in Ethereum today. While Verkle Trees utilize a tree-like structure similar to MPT, a key difference is each node uses a special type of hash (called a vector commitment) to commit to children nodes. These vector commitments provide several important, long-term benefits, and help pave the way for statelessness in Ethereum.

The proposed solution is to create a Verkle Tree library in Nim that can be seamlessly integrated into the Nimbus client. The library will provide efficient and secure storage of key-value pairs, allowing for optimized state storage and Merkle proof generation. It will be designed to be lightweight, modular, and easy to use, ensuring compatibility with the existing codebase of the Nimbus client. The library will be developed in collaboration with the Nimbus team, and will be thoroughly tested to ensure that it meets the requirements of the client.

## Specification
- For the Elliptic Curve we would be using the [Banderwagon Curve](https://hackmd.io/@6iQDuIePQjyYBqDChYw_jg/BJBNcv9fq), built on top of [Bandersnatch](https://eprint.iacr.org/2021/1152.pdf). The crypto primitives library used would be [Constantine](https://github.com/mratsim/constantine), which is written in Nim. 
- For the commitment scheme we would be using **IPA+Pedersen**, also known as *IPA-Multipoint*, this is well explained in the blog by [Dankrad Feist](https://dankradfeist.de/ethereum/2021/07/27/inner-product-arguments.html).
- For the reference implementation we would be considering the [Rust implementation](https://github.com/crate-crypto/rust-verkle) & [Go implementation](https://github.com/gballet/go-verkle)

## Roadmap

Since a few fellows are working on the same project, we will be dividing the work among ourselves. This is still being chalked out with the Nimbus team. You can see preliminary details [here](https://github.com/status-im/nim-eth-verkle/issues/1)

## Possible challenges
The project may face the following challenges:
1. **Limited Resources**: As the Verkle Tree library in Nim is a new development, there may be limited resources and references available. Extensive research and collaboration with the community will be necessary to overcome this challenge.
2. **Performance Optimization**: Achieving optimal performance while maintaining code readability and simplicity can be challenging. Extensive testing and profiling will be required to identify and address any performance bottlenecks.

## Goal of the project
The goal of this project is to create a Verkle Tree library in Nim & to add to the missing crypto primitives in the Nim ecosystem, so that it can be tested and benchmarked and further used to implement the state tree in the Nimbus client, and transition it from a Merkle Patricia Tree to a Verkle Tree.

## Collaborators

### Fellows
- [Advaita Saha](https://github.com/advaita-saha)
- [Godspower Eze](https://github.com/Godspower-Eze)
- [Naman Garg](https://github.com/namn-grg)
- [Agnish Ghosh](https://github.com/agnxsh)

### Mentors
- [Zahary Karadjov](https://github.com/zah)
- [Ignacio](https://github.com/jsign)

## Resources
- [Nim Verkle Repo](https://github.com/status-im/nim-eth-verkle)
- [Constantine Repo](https://github.com/mratsim/constantine)