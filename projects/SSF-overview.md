# Project Proposal

## An Overview and Expansion of Research into Single Slot Finality Consensus Mechanisms

### Motivation

The field of Single Slot Finality (SSF) is at a crucial juncture. With the increasing demands on Ethereum, there is a clear need for more efficient and faster consensus mechanisms. SSF offers a solution by aiming for nearly instantaneous transaction verifications, leading to an improved user experience, prevention of reorganizations incentivized by MEV, and the ability to prove liveness, among other advantages.

However, despite its potential, the complete integration of SSF into the mainnet is a medium to long-term objective. Currently, numerous consensus mechanisms and innovations are being explored to achieve SSF, reflecting the active research and development in this domain.

The objective of this project is to present a concise and clear overview of the current state of SSF research. This will involve highlighting significant advancements, potential directions, and making meaningful contributions to advance the ongoing research.

### Project Description

This project will complement my Master's thesis by providing an academic overview of the entire single slot finality consensus mechanism landscape. It will cover existing consensus mechanisms that achieve or are progressing towards SSF, the underlying designs and innovations enabling them, their pros and cons, and their viability as replacements for Ethereum's LMD-GHOST mechanism. Additionally, the project will aim to expand the research space by combining features from different mechanisms to create novel consensus models with varying trade-offs. It will also propose research questions to guide future investigations.

### Specification

Implementation details and technical information for the project:

The proposed solution will be implemented within my Master's Thesis, tentatively titled "A Comprehensive Overview of Blockchain Consensus Mechanisms with a Focus on Single Slot Finality." The paper will follow the structure typical of academic theses, including an introduction to the challenges, a section providing necessary background knowledge to approach SSF, an overview of diverse approaches, mechanisms, and proposals leading towards SSF, and an analysis and discussion segment. The paper will also present attempts to develop new consensus mechanisms with distinct trade-offs by building upon previous work. The conclusion will address open research questions and the future landscape of the field.

The paper will evaluate and analyze various consensus mechanisms, such as:

- RLMD-GHOST
- LMD-GHOST (with multiple modifications)
- Goldfish
- Tendermint
- Algorand
- Momose-Ren
- Malkhi, Momose, Ren
- Sei’s twin-turbo consensus
- SKALE consensus (Asynchronous Binary Byzantine Agreement)

The analysis will cover aspects like time-to-finality, safety and liveness guarantees, node requirements, required synchrony, decentralization level, potential attack vectors, and more.

The project will also consider approaches, designs, and supplementary materials, including:

- Vitalik’s cumulative committee-based finality approach
- Casper CBC
- Casper FFG (combined with a consensus mechanism)
- Longest-chain paradigm
- Sleepy model and its variations
- Availability-finality dilemma
- Graded agreements and dynamic quorums
- Horn (signature aggregation design)

Further modifications and innovations will be explored as the research progresses. Potential ideas include adjusting security guarantees to achieve varying levels of finality at different times and merging design decisions from different protocols.

The written material will be divided as follows: introduction and background information (30%), main overview (50-60%), and proposed designs and research questions (10-20%).

### Roadmap

Proposed timeline and project execution breakdown:

The project consists of three primary stages:

1. Research and synthesis of information
2. Writing process
3. Designing protocol modifications and proposing research questions

Research and writing will be concurrent tasks, span the entire project duration, and are expected to take about 2 months. This estimate is based on approximately 3-4 days for reading each paper and 1-2 days to compile findings, considering a total of 10-15 papers. However, the timeline may extend beyond this duration.

The creative process of designing protocols and formulating research questions will occupy the remaining time in the EPF period, which is roughly a month. If needed, I am prepared to continue this phase until completion.

### Possible Challenges

Anticipated limitations and challenges:

The primary challenge is assessing consensus mechanisms that have not been implemented, leading to reliance on estimations or theoretical values.

Additionally, identifying relevant research questions and integrating design decisions from leading proposals could pose challenges. These questions are expected to be resolved during the research, but they might require time.

### Project Goal

Description of success and project impact:

The ideal outcome is a comprehensive and detailed overview of the entire single slot finality research landscape, along with proposals for new consensus mechanisms that fulfill Ethereum's usability requirements. While the formal academic paper's completion might extend beyond four months, the research phase will conclude within the program duration.

The scope will encompass all pertinent SSF work and aim to serve as a guiding document for the state of SSF as of late 2023.

The project's impact will be threefold:

1. Proposal of new mechanisms for potential SSF implementation on Ethereum
2. Clarification of research status and provision of a resource for both new and experienced contributors to understand single slot finality comprehensively.
3. Identification of open research questions, offering a roadmap for advancing research in the field.

### Collaborators

#### Fellows

N/A

#### Mentors

- Luca Zanolini
- Francesco D’Amato

### Resources

To be determined; this page will be updated as necessary.
