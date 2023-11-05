
##EIP-x 
 Stateless LC That Consumes ZKP 


## Motivation
In the dynamic landscape of blockchain technology, addressing the limitations of traditional light clients is paramount for the widespread adoption and efficient functioning of the Ethereum network. Conventionally, light clients have burdened full nodes by incrementally requesting block state, posing challenges to network scalability. The integration of Verkle trees has provided a significant step forward, facilitating smoother transitions for lightweight clients between blocks. However, a lingering concern lies in the assurance of accurate state root confirmation, highlighting the need for further advancements. The inability of light clients to handle zero-knowledge proofs compounds the complexity. Moreover, portal nodes, a crucial bridge in this ecosystem, face the challenge of effectively prioritizing essential information for streamlined and swift stateless light client operations. Overcoming these obstacles is central to empowering light clients and optimizing the Ethereum network for a seamless and inclusive decentralized future.

# Project Description
Project Description:

Our endeavor,EIP-x, embodies a thoughtful exploration of Helios light clients' capabilities to transform the way we access and validate blockchain data. At its core, the State Provider entity operates as a conduit to access the most recent block state of a block in a manner that fosters trust without reliance on intermediaries. This process entails the extraction of a cryptographic witness, which in turn serves as the foundation for the creation of zero-knowledge proofs (ZKPs). These ZKPs, integral to our approach, are subsequently disseminated to all participating lightweight client (LC) nodes across the network.

In the context of the Portal Network, Our approach centers on empowering Trin clients to efficiently incorporate ZKPs into their operations, coupled with the implementation of a dedicated cache mechanism. This cache mechanism offers the flexibility to select portions of proofs that align with individual requirements, thereby optimizing the overall performance.

The collaboration between the State Provider and stateless LC consuming zkp within the Portal Network establishes a dynamic partnership, fostering robust data validation. In cases where cache-related inconsistencies or failures may surface, participants can confidently resort to the ZK proofs of the latest state. These cryptographic proofs serve as a dependable means to verify the integrity of cached data fragments, reinforcing trust and reliability within the system. The State Provider project endeavors to significantly enhance the efficiency, security, and accessibility of blockchain data for stateless light clients, contributing to the ongoing evolution of decentralized technologies.

## Roadmap
POC of the eniter EIP-X 
testing 
evovling the implement5ation to improve the capabilites 


## Goal of the project

##Important Use-case1: 
Being stateless Node for Flashbot
Problem: 
Flashbots' 0 gas price transactions, paying miners via smart contracts, risk a Denial-of-Service (DOS) vector. Miners must simulate transactions to assess profitability, making them vulnerable to spam attacks without cost. This differs from regular Ethereum transactions with inherent fees and node-based mempool filtering.

Potential Solution with EIP-X: Stateless clients, which can consume  zkps, have the potential to mitigate the problem above

1. Efficient Profitability Validation: They enable miners to determine transaction profitability using zkps, reducing resource consumption.Since zkps can verify transaction validity without executing them, miners can filter out spammy transactions more effectively, as they can identify them without the need for costly simulation.

2. Protection from Spam:Stateless nodes can defend against spam by verifying transaction validity without execution, enhancing spam filtering.

3. Privacy and Permissionlessness: They maintain privacy by validating transactions without revealing sensitive data and achieve permissionlessness in Flashbots transactions.

##Important Use-case 2: 
Being stateless Relayer for Flashbot

Problem: 
In the Flashbot ecosystem, the absence of costs for failed bids allows for potential network spam via invalid bundles, leading to denial of service (DoS) threats. Malicious actors can send miners invalid bundles, causing wasted computational resources. Relayers are crucial for DoS mitigation. Flashbots' mev-relay addresses this, but trust-based concerns exist. 


Solution: 
stateless light client with ZKPs to efficiently verify bundle validity and payment status, preventing invalid bundles from reaching miners and enhancing network security. Our EIP-x can solve Flashbot in three ways:

1- according to the flow, relayer consumes the Ethereum state(what we provide is a fir here, zkp of last block state) 
2- we can provide a zk of payment proof by bundlers if they have payed to the  miner : 1- it will reduce resource usage to compute if bundler has paid 
3-preventing Relayers to have full access to the contents of all bundles and could easily reorder or steal or censor them!



## Collaborators
Sogol Malek,
Luke Schoen, 
Samuel Dare, 
### Fellows 
Sogol Malek (EPF)
Luke Schoen (EPF)

### Mentors

Guilluame Ballet(Verkle)
Sina Mahmoodi(Geth)
Daniel Marzec (Flashbot)

## Resources
https://github.com/sogolmalek/EIP-x
https://docs.google.com/presentation/d/1ExNviOulPM8bsnMS-EuvFbH8hLpWNltiqaxjm2jSZd0/edit?usp=sharing
https://ethresear.ch/t/making-flashbot-relay-stateless-with-eip-x/16788
https://docs.google.com/document/d/1M1N1jVZTmrD3kfznQhfOVttXVdsM6sS3G_CDz2NFbH8/edit?usp=drive_link

