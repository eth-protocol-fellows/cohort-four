# Computational Cost Analysis of Poseidon Hash as an EVM Precompile

## Motivation

Ethereum precompile contracts are constructed into the EVM and executed on the client side for high efficiency. Usually a precompile status is reserved for subrutines that are considered of high importance and usage. Currently there are exactly nine precompiled contracts:
1. 	`ecRecover` (ECDSA public key recovery function),
2. 	`SHA2-256` (hash functon),
3. 	`RIPEMD-160` (hash function),
4. 	`identity` (identity function),
5. 	`modexp` (modular exponentiation),
6. 	`ecAdd` (point addition on the elliptic curve `alt_bn128`),
7. 	`ecMul` (scalar multiplication on the elliptic curve `alt_bn128`),
9. 	`ecPairing` (bilinear function on groups over the elliptic curve `alt_bn128`),
10. `blake2f` (compression function `F` in the `BLAKE2` hash algorithm).

From the above list we can see that there are two hash functions, namely `SHA2-256` and `RIPEMD-160`, plus the compression function `blake2f` which is used in the hash function `BLAKE2`. Therefore, we have three precompiled contracts that are used just for hashing. Clearly, having a set of good hash functions is important.

[EIP-5988](https://eips.ethereum.org/EIPS/eip-5988) is a recent EIP that proposes to add the hash function Poseidon as a precompiled contract. Poseidon is a relatively new hash function based on a [sponge construction](https://keccak.team/files/CSF-0.1.pdf) that uses a permutation constructed following a [Hades strategy](https://eprint.iacr.org/2019/1107). Previous research ([Grassi et al. 2021](https://eprint.iacr.org/2019/458.pdf)) showed that Poseidon reduces considerably the size of arithmetic circuits, and hence, the number of R1CS constraints, which allows for improvement on the prover side of zero-knowledge protocols. Also, Poseidon was proven to be compatible with all major zero-knowledge protocols like zkSNARKs, zkSTARKs, bulletproofs, and others. Therefore, a proposal for adding Poseidon as a precompile can help accelerate current zk-Rollups solutions of L2s and many other potential applications of zero-knowledge proof systems.

## Project Description

[EIP-5988](https://eips.ethereum.org/EIPS/eip-5988) still needs more justification before being considered for implementation. Some issues that need to be resolved are for example what parameters to include, how to define the round constants, and which MDS matrices to use; see discussions in the [ethereum-magicians](https://ethereum-magicians.org/t/eip-5988-add-poseidon-hash-function-precompile/11772) forum.

One important issue is the computational cost of determining the round constants which directly affects the efficiency of any implementation of the hash function. It can be expensive for a precompile contract to compute round constants on demand, and choosing one set of round constants can favor some applications and be detrimental to others.

In order to have a better understanding of the computational costs involved in any implementation of Poseidon as a precompile, this project proposes to design and implement benchmark tests of running Poseidon for different values of round constants, security levels and S-boxes.

In the past, when [EIP-152](https://eips.ethereum.org/EIPS/eip-152) was being discussed for example, benchmarks tests for the execution time of the `blake2f` precompile were made, which helped to assert the computational costs and to estimate a gas cost of the precompile.

Therefore, the main proposal of this project is to code and execute benchmark tests for the Poseidon hash function and see how it compares against other precompiled hash functions. This could help to make an argument in favor of adding Poseidon as a precompile. Furthermore, in order to have a point of reference for the gas costs, this project will also implement a smart contract in Solidity using the specs of [EIP-5988](https://eips.ethereum.org/EIPS/eip-5988).

## Goal of the Project

In order to make an informed decision on [EIP-5988](https://eips.ethereum.org/EIPS/eip-5988), the main goal of this project is to add experimental evidence on the computational costs of running Poseidon as a precompiled contract. This will allow to make estimates on the execution times on the client side and to have a reference document for future discussions related to [EIP-5988](https://eips.ethereum.org/EIPS/eip-5988).

## Specification

In order to achieve the goal mentioned above, and to have concrete results ready by the end of the EPF program, this project proposes the following steps.

1. Make an implementation in Rust of Poseidon. This implementation will follow the specs of [EIP-5988](https://eips.ethereum.org/EIPS/eip-5988).
2. Compare the Rust implementation of Poseidon against the precompiled contracts `SHA2-256` and `RIPEMD-160` using their implementation in the [`revm`](https://github.com/bluealloy/revm). This comparison will also include different parameters for Poseidon.
3. Make an implementation in Solidity of Poseidon in order to have an estimate of the gas costs concerning smart contracts.
4. Write a technical report sumarizing the results obtained from the benchmarks. This will also include a proposal for a gas cost of the precompile.

It is also important to note that similar steps were done during discussions around [EIP-152](https://eips.ethereum.org/EIPS/eip-152) for the `blake2f` precompile.

The language Rust was chosen in order to make fair comparisons against current implementations of `SHA2-256` and `RIPEMD-160`. Since this project considers Poseidon as a precompile, it is required to compare it against an implementation in a language that is currently used by an EVM, for example `revm`. That way, the implementations of `SHA2-256` and `RIPEMD-160` from the EVM can be reused in the benchmarking tests. Using a different language that is not currently used by a client will require an new implementation of the precompiles, which could result in delays to the project. Furthermore, since [EIP-5988](https://eips.ethereum.org/EIPS/eip-5988) has a potential to be included into the protocol, any benchmark has to be performed against concrete precompiles that are currently being used.





## Roadmap

The proposed methodology of the previous section will be executed following the schedule presented below.

![](https://hackmd.io/_uploads/S1vqxlu32.png)


## Possible Challenges

The main challenge on the execution of the project is the Rust implementation of Poseidon. Having to learn Rust for this project and lack of experience with the language can potentially delay the tasks of the project. Also, the Solidity contract will require some especial algorithms for arithmetic over large prime fields.

## Collaborators

### Fellows

[Marcos Villagra](https://sites.google.com/view/marcosvillagra/)

### Mentors

Ignacio
Kev

## Resources

1. Grassi, L., Khovratovich, D., Rechberger, C., Roy, A., & Schofnegger, M. (2021). Poseidon: A new hash function for Zero-Knowledge proof systems. In 30th USENIX Security Symposium (USENIX Security 21) (pp. 519-535). [[link](https://eprint.iacr.org/2019/458.pdf)]
2. Grassi, L., Khovratovich, D., & Schofnegger, M. (2023). Poseidon2: A Faster Version of the Poseidon Hash Function. Cryptology ePrint Archive. [[link](https://eprint.iacr.org/2023/323.pdf)]
3. https://www.poseidon-hash.info/
4. Abdelhamid Bakhta, Eli Ben Sasson, Avihu Levy, David Levit Gurevich, "EIP-5988: Add Poseidon hash function precompile [DRAFT]," Ethereum Improvement Proposals, no. 5988, November 2022. [Online serial]. Available: https://eips.ethereum.org/EIPS/eip-5988.
5. Bertoni, G., Daemen, J., Peeters, M. & Van Assche, G. (2011). Cryptographic sponge functions. [[link](https://keccak.team/files/CSF-0.1.pdf)]
6. Grassi, L., Lüftenegger, R., Rechberger, C., Rotaru, D., & Schofnegger, M. (2020). On a generalization of substitution-permutation networks: The HADES design strategy. In Advances in Cryptology–EUROCRYPT 2020: 39th Annual International Conference on the Theory and Applications of Cryptographic Techniques, Zagreb, Croatia, May 10–14, 2020, Proceedings, Part II 30 (pp. 674-704). Springer International Publishing. [[link](https://eprint.iacr.org/2019/1107)]
