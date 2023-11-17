# EIP-X Proposal

Stateless Light Client That Consumes ZKP With Efficient Access To Specific Segments Of The State.

## Motivation

In the dynamic landscape of blockchain technology, addressing the limitations of traditional light clients is paramount for the widespread adoption and efficient functioning of the Ethereum network. Conventionally, light clients have burdened full nodes by incrementally requesting block states, posing challenges to network scalability. The integration of Verkle trees has provided a significant step forward, facilitating smoother transitions for lightweight clients between blocks. However, a lingering concern lies in the assurance of accurate state root confirmation, highlighting the need for further advancements. The inability of light clients to handle zero-knowledge proofs compounds the complexity.

As a response to the urgent need for a super lightweight client that consumes ZKP, our EIP aims to address challenges such as front-running and sandwich attacks.

In the MEV utopia model, we seek specialization across various aspects, including maximum competition and no privileged actors. To achieve the MEV utopia world, we need to enable trustless collaboration and maximize competition in the MEV supply chain. However, this is challenging because parties naturally don't trust each other. Validators want to propose a block with the most value, but we don't want them to necessarily have sophisticated infrastructures, so they source that out to builders. However, if validators can see inside the blocks, they can steal it from builders or front-run users. As a consequence, block builders send their blocks to some trusted validators, for example, large well-known ones, and solo stakers would be unable to receive competitive MEV rewards.

So the takeaway here is that builders need privacy from validators.

In that context, we were working on a cool concept in the form of a light client that consumes ZKP and is so light that it operates in a stateless manner.

## Project Description

Our endeavor, EIP-X, embodies a thoughtful exploration of thin light clients' capabilities as the base of a light client. The first component is a witness generator, a fork of Geth that subscribes to blockchain events. Whenever a new block is generated, it will automatically fetch the most recent block state. This progress entails the extraction of a cryptographic witness, which serves as the foundation for the creation of zero-knowledge proofs (ZKPs). A ZKEVM module will generate the ZK proof of the witness. These ZKPs, integral to our approach, are subsequently disseminated to all participating lightweight client (LC) nodes across the peer-to-peer network of nodes. Therefore, all nodes will have the entire last state with downloading only a succinct ZKP of the witness corresponding to the last block on the chain. In the context of the Portal Network, our approach centers on empowering thin clients to efficiently incorporate ZKPs into their operations. We leverage the Ethereum standard communication protocol Discv5 to propagate the ZKP across the p2p network at once.

In cases where cache-related inconsistencies or failures may surface, participants can confidently resort to the ZK proofs of the latest state. These cryptographic proofs serve as a dependable means to verify the integrity of cached data fragments, reinforcing trust and reliability within the system. This project endeavors to significantly enhance the efficiency, security, and accessibility of blockchain data for stateless light clients, with a product direction being a mobile-friendly light client to significantly increase decentralization and reduce the barrier to being a verifier node with the least resource consumption.

## Goal of the Project

### Important Use-case 1:

Being a stateless Node for Flashbot

**Problem:**
Flashbots' 0 gas price transactions, paying miners via smart contracts, risk a Denial-of-Service (DOS) vector. Miners must simulate transactions to assess profitability, making them vulnerable to spam attacks without cost. This differs from regular Ethereum transactions with inherent fees and node-based mempool filtering.

**Potential Solution with EIP-X:**
Stateless clients, which can consume ZKPs, have the potential to mitigate the problem above.

### Important Use-case 2:

The entire idea of EIP-X has started by proposing a light client that can verify the ZK message type and can propagate a ZKP across the p2p network in one call.

Problem: Let's start by understanding the challenges we aim to overcome: Front running, the act of exploiting advanced knowledge of transactions to gain an unfair advantage, and sandwich attacks, where malicious actors position themselves to profit from others' trades, are persistent threats in our ecosystem.

**Potential Solution with EIP-X:** 
Enter zero-knowledge proofs (ZKPs), a powerful cryptographic tool that allows us to prove the correctness of computations without revealing sensitive information. Our proposal centers around integrating ZKPs into the order-matching process to enhance privacy and security.

The solution begins with a commit-reveal scheme, where users commit to their trades without revealing specifics. What sets us apart is the integration of ZKPs, allowing users to prove the validity of their commitments without exposing critical details.

To mitigate the risk of front running, we introduce time-locked execution. Trades are only revealed and processed after a specified time period, reducing the window of opportunity for malicious actors.

Acknowledging that ZKP generation may take time, we implement batch processing and explore parallelization techniques to optimize the efficiency of ZKP generation, ensuring scalability and speed.

---
## Collaborators

- Sogol Malek
- Mohammadreza Nakhle

## Mentors

- Guillaume Ballet (Lead @Verkle Trie)
- Sina Mahmoudi (Geth Team)
- Portal Team
- Daniel Marcez (protocol eng @Flashbots)
- Cc: Hasu, Strategic lead @Flashbots

## PowerPoint Link

[Link to PowerPoint Presentation](https://docs.google.com/presentation/d/1H-ZUW5vUM5Tm30q5tEC_ZOdJg2cqSVp19bHOzN2LzFE/edit?usp=sharing)

## Github

[Github Repository Link](https://github.com/sogolmalek/EIP-x.git)
