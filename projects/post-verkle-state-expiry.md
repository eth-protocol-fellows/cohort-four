# Post-Verkle State Expiry
🧬 Empowering Ethereum’s Eternal Evolution

## Summary
This project introduces a new state expiry scheme that utilizes the Verkle Tree. All inactive values (i.e., account balance, nonce, contract code, slots, etc.) will be expired and can be revived by submitting a Verkle proof.

## Motivation

On Ethereum, the **State** consists of the following:

- Account balances
- Account nonces
- Contract code
- Contract storage

At any given time, nodes need to know the current state to process new blocks and transactions. As more users join the network, more states are created (more accounts and contracts). As the state grows, the storage requirement for a node increases because they need to store the full state.

When a blockchain's state grows significantly, it hinders the network's performance, making it difficult for many people to run nodes, which ultimately leads to centralization. This issue is known as the **State Bloat** problem.

## Project description

My proposed solution is to implement a post-verkle state expiry scheme where only the values in the leaf nodes are expired. Expired values can be revived by submitting a proof.

The approach is rather straightforward compared to other schemes, such as Vitalik's Epoch-based approach. Expiring the intermediate nodes may also be an option, but there are a few concerns. Firstly, it adds a lot of complexity, as the current IPA library doesn't support the feature of obtaining a proof from a subtree. Secondly, expiring off subtree causes a tree rot problem, as described in [Vitalik's article](https://hackmd.io/@vbuterin/state_size_management#Tree-rot).

## Specification

The Verkle tree is a cryptographic data structure similar to the Merkle Patricia Tree (MPT), except that it uses a vector commitment to commit to children nodes instead of regular cryptographic hash. In the Verkle Tree, generating a witness for a particular value is much smaller than an MPT proof. The smaller witness size allows witnesses to be included in blocks without overloading the block size. Hence, this enables a few important roadmaps for Ethereum, such as statelessness and state expiry.

One major change to the state architecture is that all key-value pairs are stored in a single Verkle Tree, instead of the account trie and contract trie being stored separately. This also includes contract code, where the bytecode is segmented into 32 bytes each and stored as key-value pairs.

To dive deeper into the Verkle Tree structure, Verkle tree has 2 types of nodes:

- Inner Nodes: Can contain 256 children, which can either be empty, inner nodes or extension nodes. This is similar to MPT’s branch node.
- Extension Nodes: Can contain 256 values with the same stem but different suffixes

In this state expiry scheme, metadata will be added to the values to indicate if they have been expired or not. The decision for the metadata architecture will be finalized during the design phase.

On the development side, there are a few components that need to be addressed, separated into major and minor parts as follows:

**Major Components**
- Witness format
- Verkle tree modification
- EVM
- Prune
- State Storage

**Minor Components**
- Snap Sync
- RPC

For this project, major components will be prioritized while minor ones can be done if time allows.

## Roadmap

### W6 - W7: Design Phase
During this phase, I aim to complete the design for the major components. This includes understanding the codebase for Verkle implementation in Geth.

### W8 - W15: Coding Phase
The majority of the time will be used for development-related tasks. I aim to complete all of the major components during this phase. This also includes setting up the local development network using the Verkle node.

### W16: Review Phase
During the last week, I'll finalize my project outcomes and prepare for a presentation during DevConnect in Istanbul. I'll also provide an estimation of how much state storage can be saved with this state expiry scheme.

## Possible challenges
**Limited understanding on applied crypto**  
I had no prior experience writing cryptography-related code, so this will definitely be a significant challenge.

**Lack of documentation for Verkle Tree**  
I also foresee myself having a hard time trying to set up a development environment using the Verkle Tree repo, as there aren't many documentations to do so. But I'll treat this as an opportunity to fill up the gap and contribute.

## Goal of the project
At the end of this fellowship program, I should be able to demonstrate a PoC based on the following flow:

- Run a node
- Deploy a simple contract
- Wait for contract to be expired
- Send a transaction to revive state
- Read revived state

Aside from that I should have also prepared a detailed documentation on each design components, as well as estimating how much state storage can be saved.

## Collaborators

### Mentors

- Ignacio
- Guillaume

## Resources
- [Verkle.info](http://verkle.info)
- [awesome-verkle](https://github.com/weiihann/awesome-verkle)
- [BSC State Expiry](https://forum.bnbchain.org/t/bep-idea-state-expiry-on-bnb-chain/646/6?u=0xbundler)