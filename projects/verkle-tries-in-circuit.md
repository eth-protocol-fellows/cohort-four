# Verkle Tries in-circuit

**this is a draft project-proposal, current goal of this project is to get benchmark of in-circuit pedersen hash and commitment used in verkle tries vs keccak hash used in MPT, overcomplicating things leads nowhere**

VKT - verkle trie
MPT - merkle patricia trie

Purpose of this document is to describe project proposal for creating a verkle trie data structure in-circuit which means execution of the state changes can be efficiently proven in zk circuit (because of the removal of main bottleneck - keccak-sha3)

## Motivation


![](https://hackmd.io/_uploads/Skmxpp8h2.png)

In order to make ethereum became more scalable, decentralized and secure new data structure for storage is proposed: Verkle Trie. More on that here:
https://verkle.info/

 *(not sure if VKT adds more security to Ethereum, i guess MPT is more secure than VKT because of the quantum security of keccak vs ECC, but still we should be good for next 5-10 years (there are no quantum computers yet)) - at least that's my understanding for now*
EDIT:
 *there are "functional commitements" which are post-quantum safe, additively homomorphic but they require some kind of trusted setup, i'm learning if this can be efficient in-circuit, here's the paper: https://eprint.iacr.org/2022/1368.pdf*

*Comment from Lev (https://github.com/Lev-Stambler/CP22-function-commitment) on his work on this functional commitment and his answer:*
- *The problem with this paper is that it forces one to uses boolean fields rather than larger arithmetic ones. This comes at a substantial blow up to the overall circuit, not to mention there is a constant blowup (something like each boolean is represented by ~1_000 bits).*


2 reasons the transition is happening from MPT to VKT is because it will help ethereum reach weak statelessness and help onboard more validators(**more decentralisation**), but also because it is much cheaper and easier to prove verkle trie than merkle trie in circuit for zk rollups(**more scalability**), which means it should be easier to have type 1 zk-evm (because of the removal of keccak and having eliptic curve operations (pedersen commitment + IPA)) - that should be much eaiser to verify in zk-circuit.

I've asked in Ethereum R&D discord "verkle-trie-migration" question if anyone is already working on VKT in-circuit and seems there is no such project, so I think it make sense working on it. Zhang Zhuo (https://github.com/lispc/)  from Scroll team already offered help.


I've got this idea while reading the bandersnatch eliptic curve paper: https://eprint.iacr.org/2021/1152.pdf and doing the small hackathon project.

So the curve is chosen to be friendly for zk-snarks and efficient for scalar multiplication and pedersen commitments should be efficient in-circuit. Goal of this project is to learn about all these things and benchmark against MPT primitives(keccak mainly) in-circuit implementation. For example proving time.

## Project description


High overview of things that we need:
- bandersnatch eliptic curve with GLV endomophism for faster scalar multiplication(GLV probably doesn't make sense to have it in-circuit): https://eprint.iacr.org/2021/1152.pdf
- banderwagon subgroup: https://hackmd.io/@6iQDuIePQjyYBqDChYw_jg/BJ2-L6Nzc
- pedersen commitment + IPA (inner product argument) -- https://dankradfeist.de/ethereum/2021/07/27/inner-product-arguments.html
- verkle trie structure (inner, extension and suffix, leaf nodes) with 256 children and logic for adding, editing and deleting key-values (computing commitments to every parent node up to the root node and final IPA proof): https://notes.ethereum.org/@vbuterin/verkle_tree_eip

Since Ethereum PSE team is working on ZKEVM type 1 using halo2 library, I would like to learn more about this and start writing circuits for VKT. So far I have written small projects like:
https://github.com/dragan2234/fibosquared-halo2

Also, for the first iteration I think we could only have VKT circuit working correctly without integration with zkevm project. Then we would benchmark against MPT circuit. Example of benchmark:
- VKT vs MPT witness calcuation for inserting, deleting and updating 1 value: proving time

Since development of MPT circuit for zkevm project lasted 2 years, this project is not an easy task to do but still shouldn't be that complicated. Any output by the end of the cohort should be useful.

Helpful links:

- Axioms framework for buliding ECC in-circuit: https://github.com/axiom-crypto/halo2-lib#halo2-ecc
- https://verkle.info/
- https://verkle.dev/ -- this website is currently in progress but it should have some 


## Specification

TBD.


## Roadmap

- implement bandersnatch eliptic curve
- implement scalar mul
- implement banderwagon
- implement pedersen commitment
- implement ipa_multiproof
- implement VKT structure

## Possible challenges

- personally beginner with VKT, MPT and halo2-lib

update on challenges:
- so bandersnatch curve is chosen with bls12-381 in mind because base field of bandersnatch == scalar field of bls12-381. Reason for that is to be snark-friendly, but ethereum uses bn254 for precompiles and most of the rollups also use bn254 in the prover for kzg commitments
- there is no rollup using bls12-381, at least from my investigation
- only proof system using bls12-381 that I realized so far is marlin
- I don't know hard is having a fork of proof system like plonk + kzg but with bls12-381 and having halo2 api working over that backend
- Does it maybe make sense having verkle tries on Grumpkin curve which is analog to bandersnatch but for bn254? Aztec uses this curve, maybe there are more differences but they also do pedersen commitments, so should be the same. But i think that's not type 1 compatibility because curve is different and pedersen hashes will be different. But still it would be a good for benchmarking pedersen commitment in-circuit vs keccak in-circuit


update 2 on challenges:
- there is currently no proof system and rollup using bls12-381 curve. Halo2 is the most flexible proof system, and there is a PR waiting to be finalized so bls12-381 could be "easily" merged to proof system using halo2 repos: https://github.com/privacy-scaling-explorations/halo2curves/pull/38

update 3:
- General idea: merging this repo: https://github.com/crate-crypto/rust-verkle to http://github.com/paradigmxyz/reth and then to https://github.com/risc0/zeth
- This seems to be easiest way of having zkEVM type 1 with Verkle Tries and measuring how would that improve performance/proving time
- Project idea: take rust code of keccak and pedersen commitment **specified in VKT** and benchmark it with risc0 technology. Shouldn't be too hard to do this and understand improvement

update 4:
comment from https://github.com/asanso whether banderwagon would be effcient in-circuit: Yes, it would give similar benchamarks as bandersnatch r1cs contraints benchmarks from https://github.com/zhenfeizhang/bandersnatch#examples "Examples" section.

Benchmarks:
bandersnatch:
cs for base var: 5
cs for scalar var: 256
cs for mul : 2869
cs for result var : 27
cs for equality : 20
total constraints : 3177

jubjub:
cs for base var: 21
cs for scalar var: 256
cs for mul : 3325
cs for result var : 21
cs for equality : 2

bandersnatch with the glv:
cs for setup: 16
cs for endomorphism var: 6
cs for scalar decomposition var: 405
cs for msm: 2176
cs for result var : 16
cs for equality : 2
total constraints : 2621


- Maybe it would make sense benchmarking banderwagon like this too


## Goal of the project

- Learn about cryptography and data structure used in verkle tries and writing circuits using halo2 library.
- Benchmark VKT vs MPT in-circuit and make some conclusions about efficency of VKT in-circuit because EVM-compatible L2 solutions will need this.

## Collaborators

### Fellows
There are few people interested in this, and not all of them from the EPF program. I will add everyone here when we kickstart.

### Mentors

- Ignacio Hagopian

## Resources

- Axioms framework for buliding ECC in-circuit: https://github.com/axiom-crypto/halo2-lib#halo2-ecc
- https://learn.0xparc.org/halo2/ - tutorial for writing circuits using halo2 lib
- https://verkle.info/
- https://verkle.dev/ – this website is currently in progress but it should have some useful docs over the time



MORE UPDATES(will clean up the whole file later):

- there is this repo maybe useful since it's bls12-381: https://github.com/ZK-Garage/plonk
- purpose of this project is to get benchmark of in-circuit pedersen hash, overcomplicating things leads nowhere
- How to make kakarot zkevm become type 1 with verkle tries: https://hackmd.io/CmCJxFBkT7u-bIQ9Y7tKyQ