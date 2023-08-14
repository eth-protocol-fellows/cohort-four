## **Towards Optimal Prover Incentives in ZK-Rollups: A Comprehensive Analysis and Simulation**

## **Motivation**

The project’s main goal is to tackle the challenge of creating effective incentive structures for provers in Layer 2 networks, focusing on zk-rollups. Prover incentives play a vital role in maintaining the network’s security and efficiency. Based on the economic rewards, they shape the behavior of provers. If these incentives are not carefully designed, there’s a risk of provers deviating from the system protocol, which could severely impact the network’s integrity and performance. Therefore, gaining a deep understanding of provers’ economic motivations and optimizing the incentive model is crucial to develop a robust Layer 2 solution.

## **Project description**

The proposed solution is to conduct an in-depth economic analysis of various prover incentives using game theory and cryptoeconomics principles. This analysis will form the foundation of a mathematical model that captures the behavior of rational and irrational provers under various incentive structures, including token burning and block reward sharing.

To validate the theoretical models and gain practical insights, a simulation of the Layer 2 network will be implemented. The simulation will replicate the real-world dynamics of the network, incorporating provers, proposers, and the Layer 1 contract.

## **Specification**

The project will be implemented in two stages:

**1. Economic Modeling:**

- Conduct a comprehensive literature review on game theory, cryptoeconomics, and tokenomics related to rollups.
- Develop a mathematical model of prover incentives, taking into account token burning, block reward sharing, and various attack vectors.
- Perform sensitivity analysis to understand how different parameters impact prover behavior and network security.

**2. Simulation Development:**

- Design and implement an agent-based simulation of the Layer 2 network in Python.
- Define scenarios with varying conditions to test the prover behavior and network performance under different incentive structures.
- Perform data analysis and statistical evaluation of simulation results.

## **Roadmap**

*Literature Review* - August Week 3-4

- Gather and read relevant sources and start documenting your findings and identify gaps in the current research.

*Economic Modeling of Prover Incentives* - September Week 1-2

- Begin to develop mathematical model of prover incentives, based on literature review findings. Document all assumptions and formulations.

*Sensitivity Analysis* - September Week 3-4

- Continue developing mathematical model and start performing sensitivity analysis by altering various parameters.

*Simulation Development* - October Week 1-2

- Finish sensitivity analysis and document how these changes impact overall prover behavior and network security. Begin developing a simulation of the Layer 2 network in Python, incorporating all elements from your mathematical model.

*Scenario Design and Data Analysis* - October Week 3-4

- Run the simulation under various conditions. Collect data and perform an initial analysis.

*Report Writing* - October Week 4

- Based on findings, begin optimizing the incentive structures. Start drafting the final report, and draw preliminary conclusions and recommendations.

## **Possible challenges**

- Understanding cryptoeconomic principles and translating them into mathematical models can be challenging.
- Accurately modeling prover behavior in a complex Layer 2 network may pose technical challenges.
- Designing a simulation that effectively represents real-world dynamics while keeping computation time manageable.
- Optimizing model parameters to balance between network security and efficiency may require complex computational techniques.
- Ensuring the validity and reliability of the data analysis derived from simulation results.

## **Goal of the project**

Success will be a comprehensive research detailing the prover incentives in zk-rollups and a simulation model to validate the theoretical findings. The project would be considered successful when the optimal incentive parameters are identified, and the network achieves a good balance of security and efficiency under various scenarios.

The success of the project will be achieved through the following:

- A well-defined mathematical model representing prover incentives in zk-rollup networks.
- A functional simulation of the network that can replicate real-world dynamics and prover behavior.
- An optimized incentive structure that maximizes network security and efficiency while encouraging honest prover participation.

## **Collaborators**

### **Fellows**

- [Nilufer](https://github.com/niluferokay)
- [Norbert](https://github.com/vadasnorbert)
- [Rachit](https://github.com/rachit77)

### **Mentor**

- Barnabé Monnot

## **Resources**
- [Resources for understanding rollup economics](https://github.com/niluferokay/awesome-rollup-economics)
- [Ethereum Economic Model](https://github.com/CADLabs/ethereum-economic-model)
- [radCAD](https://github.com/CADLabs/radCAD)
- [Mesa](https://mesa.readthedocs.io/en/stable)
