# Project 

Stateless Account abstraction that scales Ethereum 

## Motivation

Stateless Account Abstraction (SAA) proposes to tackle several key problems within the Ethereum network, presenting potential solutions and improvements.
1. Scalability: The current Ethereum network faces scalability challenges due to the inclusion of full state information in every transaction. This approach restricts the number of transactions that can be processed within a given time, resulting in network congestion and higher fees. SAA aims to improve scalability by separating the execution context from the state information, enabling parallel processing of transactions and increasing transaction throughput.

2. Storage Requirements: Storing the complete state of every account on the blockchain consumes significant storage resources. As the Ethereum network grows, the storage demands become increasingly burdensome. SAA proposes a more efficient storage model by shifting the responsibility of providing the execution context to the transaction sender or external storage networks. This reduces the on-chain storage requirements, making the network more scalable and cost-effective.

3. Cost Efficiency: The current design of Ethereum can be costly for users, as each transaction must include the full state information. This approach results in higher gas fees, making it less feasible for users to interact with smart contracts. SAA introduces stateless transactions, which are lighter in terms of storage requirements and gas costs. By reducing the overhead associated with transaction execution, SAA aims to make Ethereum more cost-efficient for users and developers.

4. Developer Experience: The current stateful account model in Ethereum poses challenges for developers, as they need to consider the state information of accounts while designing and executing transactions. This complexity can hinder the development process and introduce potential security risks. SAA simplifies the development process by decoupling the execution context from the transaction, enabling developers to focus on transaction logic without being concerned about the full state information of accounts.

5. Network Interoperability: With the introduction of SAA, Ethereum can potentially improve its interoperability with external systems and blockchains. By utilizing decentralized storage networks for retrieving execution contexts, Ethereum can leverage existing infrastructure and protocols. This opens up possibilities for cross-chain communication and integration with other blockchain networks, promoting a more interconnected and vibrant ecosystem.


## Project description
Stateless Account Abstraction is proposed as a solution to tackle these problems by decoupling the on-chain state from verification and execution.  

## Specification

Enhancing Stateless Account Abstraction in Ethereum: Introducing Xtreamly, the revolutionary proposal for stateless account abstraction without altering the consensus-layer protocol.

Stateless AA, separates state from validation and execution logic. In such a scenario, users may not need to provide explicit state information to participate in an altrnative mempool. Instead, their transactions could be verified based on other criteria, such as cryptographic proofs and witness. To handle the state for transactions in the mempool without relying on explicit state information, a lightweight proxy smart contract can be integrated with an ASVC (aggregatable subvector commitment) scheme for more efficient, succinct and  cheaper.. 
It receives the user's transaction, along with any required cryptographic proofs or witnesses, and submits it to the network for validation and execution. Instead of storing the entire state, It receives the user's transaction, along with any required cryptographic proofs or witnesses, and submits it to the network for validation and execution.The proxy smart contract itself does not contain the complete state information but only holds the necessary data to facilitate the transaction. Once the transaction is validated by the network, the proxy smart contract can update its internal state or interact with other contracts accordingly.

By combining cryptographic proofs, witnesses, and the lightweight proxy smart contract, the system can verify transactions in the mempool without relying on explicit state information from users, improving efficiency and scalability. Once the transaction is validated by the network, the proxy smart contract can update its internal state or interact with other contracts accordingly.

By using a lightweight proxy smart contract in this manner, the burden of maintaining and providing explicit state information is shifted away from the user, making participation in the mempool more accessible. It also allows for a more efficient and scalable validation process, as the network can focus on verifying the transaction based on the provided criteria rather than processing the entire state for each transaction.

##Unique Goals of Stateless Account Abstraction 

Atomic Swap between multiple parties
Network abstraction
Gas abstraction
Signature abstraction
Scalability
Reduced storage requirements
Simplified network synchronization
Allows Batching transactions


## Roadmap

What is your proposed timeline? Outline parts of the project and insight on how much time it will take to execute them.

## Possible challenges

Challenge 1: Storing and Verifying Contract State in a Stateless Setting
moving funds and the execution of contract code of smart contracts in a stateless setting,  depends on the accurate and up-to-date contract state.
Challenge 2: Responsibility for Storing Contract State:
determining who should be responsible for storing the contract state becomes crucial because any client being able to submit transactions triggering contract executions,So we need to ensure the availability and integrity of the contract state.
Challenge 3: Avoiding Inclusion of Large Contract State in Transactions
Including the entire contract state within each transaction poses a scalability issue. Some contract states can be excessively large, leading to bloated transactions, increased storage costs, and slower transaction processing times. 


## Goal of the project

What does success look like? Describe the end goal of the project, scope, state and impact for the project to be considered finished and successful.

## Collaborators

### Fellows 

Are there any fellows working with you on this project? 

### Mentors

Which mentors are helping you with the project? 

## Resources
https://github.com/sogolmalek/EIP-x
https://docs.google.com/presentation/d/1ExNviOulPM8bsnMS-EuvFbH8hLpWNltiqaxjm2jSZd0/edit?usp=sharing
https://ethresear.ch/t/proposing-stateless-light-client-as-the-foundation-for-stateless-account-abstraction/15901?u=sogolmalek&trk=feed_main-feed-card_feed-article-content
