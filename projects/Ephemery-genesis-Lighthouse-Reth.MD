# Ephemery Genesis Implementation in Lighthouse and Reth

Implementation of the Ephemery testnet genesis function in a new pair of clients, Lighthouse and Reth.

## Motivation

The Ephemery testnet should mainly serve as a tool to ensure a smooth inclusion of new stakers into the ecosystem. Currently, the only possible testing tool for stakers is the Goerli testnet, but leaving the testnet after performing the needed testing may cause issues in the long term due to a large amount of inactive validators, on top of the issues universal for the current testnets with a long lifespan. Ephemery would make it possible to test stakers' setups without the fear of causing issues after leaving the testnet as a validator and switching to the mainnet. Additionaly, problems like too long sync time due to the large state or insufficient funds are also solved by the periodical resets.

## Project description

This project plays a part in improving the Ephemery testnet user experience, making it as easy to use as other currently operating testnets in various clients. The aim of this project is to implement the genesis function in a new pair of clients, Lighthouse and Reth. Currently, Ephemery is maintained manually and its use requires manual setup by the user. This project should contribute to the automatization of Ephemery in the determined clients, allowing them to generate and connect to a newly created genesis.

## Specification

The project will be implemented according to the [EIP](https://github.com/ethereum/EIPs/blob/04369cb50ee6c1894dec868141e8a32e66dc4f16/EIPS/eip-testnet-draft.md) and the [specification](https://github.com/ephemery-testnet/ephemery-resources/blob/master/specs.md). The specification will be validated and possibly improved based on the new discoveries during the implementation process.

## Roadmap

* **Week 5 - 7**: Exploring the Lighthouse client implementation and figuring out how to include the genesis function implementation. Adding Ephemery option to the implementation, with its own flag.
* **Week 7 - 12**: Implementing the genesis function in the Lighthouse consensus client.
* **Week 13 - 14**: Implementing the required infrastructure in the Reth execution client.
* **Week 15 - 16**: Getting feedback, fixing possible bugs. Researching further concepts (e.g. the reset function).

## Possible challenges

Ephemery is a new concept and will likely require extending the existing infrastructure of the clients. There is no complete implementation of the genesis (and restart) function in a pair of clients for now, therefore the process will depend on extensive research, creative code-writing and discussions with other contributors.

## Goal of the project

### Main goal

* **Lighthouse implementation** - The main goal is to implement the genesis function in a consensus client.
* **Reth implementation** - The final phase of the project should be the implementation of needed infractructure in an execution client, so that the output is a whole working pair of clients.
* **Documentation** - During the implementation, new knowledge, which may be helpful for new users and contributors, will be shared as Ephemery documentation on the official channels, like the GitHub repositories.
* **Validate EIP draft, support EIP inclusion efforts** - The EIP should be presented and demoed at PEEP and ACD to be included in an upgrade. I will support the process in any way possible.
* In conclusion, the clients should be able to start from a new genesis after each reset. The next genesis is derived from the previous one after a set period of time. The reset function is not included in the scope of this project, therefore the user will still need to manually stop and discard the previous genesis.

### Side goals - nice to have
* **Reset function research** - The next course of action should be researching how to implement the restart function. The implementation of this function will likely not be possible in the EPF time slot and will be a subject of possible further research and contributions.

## Collaborators


### Fellows 

There are no other fellows working on the Lighthouse and Reth Ephemery implementation. There is a [related project proposal by Holly](https://github.com/eth-protocol-fellows/cohort-four/blob/master/projects/native-ephemery-genesis.md), who is working on the implementation for a different pair of clients.

### Mentors

Mário Havel ([@taxmeifyoucan](https://github.com/taxmeifyoucan))
pk910 ([@pk910](https://github.com/pk910))

## Resources
[Lighthouse fork](https://github.com/T-ess/lighthouse)
[Lighthouse issue](https://github.com/sigp/lighthouse/issues/4664)
[Reth fork](https://github.com/T-ess/reth)
[Reth issue](https://github.com/paradigmxyz/reth/issues/4340)

* [EIP draft](https://github.com/ethereum/EIPs/blob/04369cb50ee6c1894dec868141e8a32e66dc4f16/EIPS/eip-testnet-draft.md)
* [Ephemeral testnet - Specs](https://github.com/ephemery-testnet/ephemery-resources/blob/master/specs.md)
* [Ephemery Scripts GitHub repository](https://github.com/ephemery-testnet/ephemery-scripts)
* [Ephemery Genesis GitHub repository](https://github.com/ephemery-testnet/ephemery-genesis)
* [Ephemery resources GitHub repository](https://github.com/ephemery-testnet/ephemery-resources)
* https://notes.ethereum.org/@mario-havel/stakers-testnet
* [Ephemery roadmap and tasks](https://github.com/ephemery-testnet/ephemery-resources/issues/1)
