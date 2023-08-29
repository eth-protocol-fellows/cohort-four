#Sogol's notes
## Introduction

Hi :) My name is Sogol Malek and i am the fellow at cohort 4, working on EIP-x.

 

## Motivation of EIP-x 

Light clients struggle to efficiently access and validate data on the mainnet due to challenges in obtaining concise witness proofs. Verkle trees help lightweight clients transition between blocks but can't prove new state accuracy. Stateless clients lack state data for actions beyond transitioning. The Portal Network doesn't fully address these issues. Our solution adds a stateless verifier LC on the Portal Network with a cache to store important state fragments. We distribute the latest state using zero-knowledge proofs and propose a chase mechanism for efficient data retrieval. This addresses challenges in accessing state data for tasks like gas estimation and enhances lightweight client efficiency.

To bring this vision to fruition, we propose the incorporation of two pivotal elements: a state provider that leverages the capabilities of Helios light clients, delivering zk proofs of the most recent state to all LC nodes, and a cache mechanism catering specifically to stateless light clients on the Portal Network, thereby optimizing their operations. Furthermore, this initiative strives to empower Verkle trees, enabling them to access and validate the mainnet state despite the scarcity of succinct witness proofs.

The synergy between these two components is noteworthy. Should inconsistencies or failures arise within the cache, participants can resort to the ZK proofs of the latest state, effectively validating the integrity of cached fragments.



## Weekly Updates
##update week 1: 
For a quick overview of the key points, I invite you to peruse my detailed post at: https://ethresear.ch/t/proposing-new-entity-for-stateless-account-abstraction-trustless-state-provider-allowing-txs-to-enter-alt-mempool-without-holding-the-whole-state/16128). 

Furthermore, I've taken the initiative to outline the idea for this entity by creating the first issue on Github. You can explore this in-depth concept at: https://github.com/sogolmalek/EIP-x/issues/1. 

##update week2: 
 I had the opportunity to connect with my fellow participants and continued my dedicated efforts on the development of my Stateless Light client initiative. As part of this journey, I took the time to enhance my understanding of the Stateless Light client and discovered an exceptionally insightful article authored by Guillaume. You can explore this article here: [Verkle Tries Overview](https://efdn.notion.site/efdn/Verkle-Tries-Overview-fc7a2ada8fc1474c9358d402c0367e8a), which happens to be directly relevant to my ongoing work.

This discovery prompted me to embark on a deep dive into research, resulting in the consolidation of my thoughts and ideas. I've documented my findings in a comprehensive post that you can access here: [Enhancing Stateless Witness Generation for Efficient Verification in Ethereum](https://ethresear.ch/t/enhancing-stateless-witness-generation-for-efficient-verification-in-ethereum/16194?u=sogolmalek). In the week ahead, I am excited to continue validating and refining these concepts. With any luck, I hope to make significant strides in the development of various components.
##Week3: 
Anticipating the days ahead, I'm excited to announce my upcoming technical meetings, especially with the remarkable individuals at Reth. These sessions are crucial as they will allow me to pose important questions and gain the necessary insights to further prepare for the challenges of the coming week.

Continuing my commitment to thorough investigation and consultation, I'm pleased to share that I've made significant strides in the development of components for my inaugural issue: [Link to my GitHub issue](https://github.com/sogolmalek/EIP-x/issues/1). I've also taken the initiative to provide a comprehensive implementation report as a comment, enriching the collaborative spirit of the community effort.
##week4: 
I had the opportunity to connect with my fellow participants and continued my dedicated efforts on the development of my Stateless Light client initiative. As part of this journey, I took the time to enhance my understanding of the Stateless Light client and discovered an exceptionally insightful article authored by Guillaume. You can explore this article here: [Verkle Tries Overview](https://efdn.notion.site/efdn/Verkle-Tries-Overview-fc7a2ada8fc1474c9358d402c0367e8a), which happens to be directly relevant to my ongoing work.

This discovery prompted me to embark on a deep dive into research, resulting in the consolidation of my thoughts and ideas. I've documented my findings in a comprehensive post that you can access here: [Enhancing Stateless Witness Generation for Efficient Verification in Ethereum](https://ethresear.ch/t/enhancing-stateless-witness-generation-for-efficient-verification-in-ethereum/16194?u=sogolmalek). In the week ahead, I am excited to continue validating and refining these concepts. With any luck, I hope to make significant strides in the development of various components.

##week5:
I'm excited to provide you with some noteworthy updates from this week's endeavors. I've made substantial progress in implementing various components of the state provider entity, which you can explore in detail here: [EIP-x Client-Rust Repository](https://github.com/sogolmalek/EIP-x/tree/main/Client-Rust). To enhance clarity, I've included comments alongside the code and introduced new issues that outline what's been accomplished and the tasks that lie ahead. You can find these issues comprehensively documented here: [EIP-x GitHub Issues](https://github.com/sogolmalek/EIP-x/issues).

Building upon the invaluable feedback I received for the second part of my proposal, I've dedicated time to expanding my work. To foster collaboration and refinement, I'm in the process of arranging discussions with mentors. Their insights, approvals, and evolution suggestions are pivotal in shaping the trajectory of my project.

Fresh off the press, I've just published a detailed post that you can access here: [Towards a Stateless Account Abstraction: Expanding My Proposal](https://ethresear.ch/t/towards-a-stateless-account-abstraction-expanding-my-proposal-for-efficient-witness-verification-and-state-provider-entities/16299?u=sogolmalek). This post delves into the ongoing evolution of my proposal and provides insights into its direction.

