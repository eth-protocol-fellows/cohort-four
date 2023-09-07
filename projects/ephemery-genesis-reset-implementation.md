EPF4: PROJECT PROPOSAL

## Implementing Ephemery's Reset Mechanism

*Automatic reset implementation of the Ephemery testnet for client setups, starting with lodestar, then geth..*

## Motivation
The [goerli supply mess](https://ethereum-magicians.org/t/testnet-workgroup-paths-out-of-the-goerli-supply-mess/11453/33) has made test tokens hard to come by. It is hamstringing validator and developers efforts to use the testnet adequately. It has also festered a growing tendency to hoard test tokens, creating token scarcity and price increase on an otherwise free token. Ephemery testnet is a unique solution aiming at solving these problems. 

It's being built based on the principle that **testnets can be ephemera**l, and if testnet are ephemeral, tokens are abundant and transient, and under these conditions it will never be hoarded because ***"it makes no sense to keep that which will be taken away after each reset"***. Ephemeral testnets have a short life-span, and create a new genesis state after each reset, effectively discarding every transaction that occured prior to it.

Ephemery is billed to be an automatic reset testnet, Automatically resetting at intervals, currently, this is [one week](https://github.com/ephemery-testnet/ephemery-genesis/releases). This means that any data or history on the testnet will be wiped out periodically, making it start fresh again. 

At the moment, the automatic reset has not yet been implemented. Clients are currently stopped and then the chaindata, removed manually before the new genesis is initialized. **Ideally the clients should be able to automatically reset themselves once the ephemery network has progressed to a new genesis state.** 

This is the next phase on ephemery and it's what i will be working on for my project. The immediate benefit of this is that: it will provide a more efficient testing environment for developers & validators making it easier to validate, experiment with [Ephemery](https://ephemery.dev/).


## Project description
The scope of this project will be focussed on: 

1. Lodestar Implementation: Developing and integrating the `Automatic Reset` feature into the Lodestar Ethereum client. Ensuring that the client can seamlessly handle periodic resets of the Ephemery testnet.

2. Genesis State Management: Developing programming logic that defines a clear process for managing the genesis state during resets as outlined in the [specifications](https://github.com/ephemery-testnet/ephemery-resources/blob/master/specs.md). This will include how clients handle:
    * the deletion or archiving of chaindata;
    * and generating a new genesis state with updated parameters.

3. Safety Checks: Implement safety checks to prevent accidental resets. This will be achieved by integrating confirmation dialogs or command-line flags that prompt the user for confirmation before reset.

4. Validation and Testing: Thoroughly validate the implementation to ensure its compatibility with the Ephemery testnet's specifications. Conduct extensive testing to identify and resolve any potential issues.

5. Documentation and User Support: Create a comprehensive documentation for validators and developers, explaining how to interact with the Ephemery testnet and leverage the Automatic Reset feature.

**Stretch:** Extend the implementation to other clients, starting with an execution client like geth, this will enable a broader user base to benefit from the Ephemery testnet.

## Specification
The original specifications for this project can be found [here](https://github.com/ephemery-testnet/ephemery-resources/blob/master/specs.md). A WIP version based on my understanding, that i plan to update as i progress is also [here](https://github.com/AdedamolaXL/ephemery-resources/blob/master/specs.md).

## Roadmap
* September 14 - 30: Review lodestar codebase.
* Oct 3 - 13: Develop the code for the reset mechanism.
* Oct 14 - 29: Modify lodestar code.
* Nov 1 - Nov 13: Validate and test.
* Nov 14 - Nov 28: Provide documentation for the reset mechanism for lodestar.
* *Beyond*: Extend the reset mechanism functionality to other clients.

## Possible Challenges
There is no comparable logic in any client yet, *"something that deletes a chain has not been needed yet and one needs to be super careful that this function never ever triggers for mainnet or another testnet"*

## Goal of the project
The goal of this project is to implement the Automatic Reset functionality for the Ephemery testnet, initially focusing on the Lodestar client and subsequently on the Geth client. 
To also ensure that this reset does not trigger a reset on other testnets and even the mainnet!

## Collaborators


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
