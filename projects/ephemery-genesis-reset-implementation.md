EPF4: PROJECT PROPOSAL

## Implementing Ephemery's Reset Mechanism

*Automatic reset implementation of the Ephemery testnet for client setups, starting with lodestar, then geth..*

## Motivation
The [goerli supply mess](https://ethereum-magicians.org/t/testnet-workgroup-paths-out-of-the-goerli-supply-mess/11453/33) has made test tokens hard to come by. It is hamstringing validators and developers' efforts to use the testnet adequately. It has also festered a growing tendency to hoard test tokens, creating token scarcity and price increases on an otherwise free token. Ephemery testnet is a unique solution aiming at solving these problems. 

It's being built based on the principle that **testnets can be ephemera**l, and if testnets are ephemeral, tokens are abundant and transient, and under these conditions, it will never be hoarded because ***" it makes no sense to keep that which will be taken away after each reset"***. Ephemeral testnets have a short lifespan, and create a new genesis state after each reset, effectively discarding every transaction that occurs prior to it.

Ephemery is billed to be an automatic reset testnet, Automatically resetting at intervals, currently, this is [one week](https://github.com/ephemery-testnet/ephemery-genesis/releases). This means that any data or history on the testnet will be wiped out periodically, making it start fresh again. 

Currently, this is implemented as external tooling for clients, wherefore, resetting the testnet requires stopping the client and then removing the chaindata manually. Ideally, clients should be able to automatically reset themselves once the ephemery network has progressed to a new genesis state. 

Holly, a fellow also working on Ephemery, is currently implementing the [genesis function](https://github.com/eth-protocol-fellows/cohort-four/blob/master/projects/native-ephemery-genesis.md) on Lodestar. This will offer partial client support for running the current instance of the Ephemery network. An automatic reset implementation that complements this, will ensure full client support!

This is the next phase of ephemery and it's what I will be working on for my project. The immediate benefit of this is that: it will provide a more efficient testing environment for developers & validators making it easier to validate, and experiment with [Ephemery](https://ephemery.dev/).

## Project description
The scope of this project will be focussed on: 

1. Automatic Reset Implementation: Develop and integrate the `Automatic Reset` feature into the Lodestar Ethereum client. The first step in achieving this is to understand Lodestar's architecture; vis-a-vis network handling & use of consensus specs. Then use that to implement the following process in code: 

    * Database Cleanup
    * Update client configurations
    * Restart client (Lodestar)
    * Sync with new genesis (Ephemery)
    * Update network parameters like network ids, peers, etc
    * Update monitoring tools like grafana
    * Restart staking & validation

2. Genesis State Management: Developing programming logic that defines a clear process for managing the genesis state during resets as outlined in the [specifications](https://github.com/ephemery-testnet/ephemery-resources/blob/master/specs.md). This will include how clients handle:
    * the deletion or archiving of chaindata;
    * and generating a new genesis state with updated parameters.

- I will be collaborating with Holly directly on this part of the project.

3. Validation and Testing: Thoroughly validate the implementation to ensure its compatibility with the Ephemery testnet's specifications. Conduct extensive testing to identify and resolve any potential issues.

4. Documentation and User Support: Create comprehensive documentation for validators and developers, explaining how to interact with the Ephemery testnet and leverage the Automatic Reset feature.



**Stretch 01:** Implement safety checks to prevent accidental resets, by adding an optional flag with a tag like `--require-manual-reset`

**Stretch 02:** Add another optional flag `--archive chaindata` for genesis management.

**Stretch 03:** Extend the implementation to other clients, starting with an execution client like geth. This will enable a broader user base to benefit from the Ephemery testnet.

## Specification
The original specifications for this project can be found [here](https://github.com/ephemery-testnet/ephemery-resources/blob/master/specs.md). A WIP version based on my understanding, which I plan to update as I progress is also [here](https://github.com/AdedamolaXL/ephemery-resources/blob/master/specs.md).

## Roadmap
* September 14 - 30: Review lodestar codebase.
* Oct 3 - 13: Develop the code for the reset mechanism.
* Oct 14 - 29: Modify lodestar code.
* Nov 1 - Nov 13: Validate and test.
* Nov 14 - Nov 28: Provide documentation for the reset mechanism for lodestar.
* *Beyond*: Extend the reset mechanism functionality to other clients.

## Possible Challenges
There is no comparable logic in any client yet, *"Something that deletes a chain has not been needed yet and one needs to be super careful that this function never ever triggers for mainnet or another testnet"*

## Goal of the project
The goal of this project is to implement the Automatic Reset functionality for the Ephemery testnet, initially focusing on the Lodestar client and subsequently on the Geth client. Ensuring that the client can seamlessly handle periodic resets of the Ephemery testnet. To also ensure that this reset does not trigger a reset on other testnets and even the mainnet!

## Collaborators
Holly

## Mentors
Mario havel, pk910, chris hobcroft.

## Resources
* [Mario's original notes on Ephemery](https://notes.ethereum.org/@mario-havel/stakers-testnet)
* [Ephemery testnet repo](https://github.com/ephemery-testnet)
* [EIP Draft](https://github.com/ethereum/EIPs/blob/04369cb50ee6c1894dec868141e8a32e66dc4f16/EIPS/eip-testnet-draft.md)
* [Ephemery website](https://ephemery.dev/)
* [pk910 WIP on Lodestar](https://github.com/pk910/lodestar)
* [Teri's docs on Ephemery](https://hackmd.io/@teri-b)
* [Holly's docs on Ephemery](https://hackmd.io/@HOL)
