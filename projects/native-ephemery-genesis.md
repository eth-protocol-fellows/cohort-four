# Native Ephemery Genesis in Ethereum Clients

MVP: Client-side implementation for Ephemery genesis in Lodestar

Stretch 1: Native chainstate reset in Lodestar

Stretch 2: DAppNode package for ephemery

## Driving forward Ephemery integration

I am writing client-side integrations for the ephemeral testnet and validating the draft EIP as part of the ephemery team.

*Why Ephemery?*

There are multiple benefits for having a short-lived testnet made available directly through existing clients and infrastructure. 

For more information on these benefits, see Mario's write-up, [Testnet for Stakers](https://notes.ethereum.org/@mario-havel/stakers-testnet).

## Contributions to Lodestar + stretch goals

**MVP**: Integrate ephemery network into Lodestar client, including a client-side implementation for generating the ephemery network genesis state from scratch (as opposed to downloading it). Understand and list any constraints / breaking changes.

I will be progressing the existing Lodestar WIP as per the [Ephemery issues list](https://github.com/ephemery-testnet/ephemery-resources/issues/1); specifically:

*Specifications*
- [x] Validate the EIP specs draft - **beginning with the Geth / Lodestar pair**
    - [x] Explore feasibility of implementing it within clients based on clients architecture
    - [x] Identify potential issues, contribute to spec and improve it
- [ ] Finish the draft, get EIP number - **contribute to the EIP draft, support EIP progress and join ACD**
    - [ ] Present at PEPP an EIP
    - [ ] Present at ACD

*Implementations*
Reference implementation of the spec is done in bash. It's in separate repos for the [genesis](https://github.com/ephemery-testnet/ephemery-genesis/blob/master/scripts/build-genesis.sh) and [reset](https://github.com/ephemery-testnet/ephemery-scripts/blob/master/retention.sh) function.
- [x] Validate the reference implementation, explore potential improvements - **ongoing**
- [x] Contribute to existing WIP implementations - **Geth + Lodestar**
- [ ] Create another implementation in a new client pair - **TBC**
- [x] Each client should have it's 'Ephemery lib' or submodule - **to validate**
- [x] Ultimate goal is to have Ephemery network running on reference scripts + all client combos - **Geth + Lodestar**

*Infrastructure*
- [x] Improving deployment methods
    - [ ] Improving the docker setup
    - [ ] Adding new deployment methods, e.g. ansible..
    - [ ] Adding Ephemery to existing deployment tools, e.g. Dappnode, stereum.. - **stretch goal - DAppNode package**
    - [x] Identify and add missing infrastructure (network monitoring, faucets,..) - **to note during the project**
    - [ ] Contribute to auto-refund/deployment mechanisms - **stretch goal - automatic reset**
    - [x] Grow pool of genesis validators - **set up genesis validator of my own**
    - [ ] Create Ephemery website with reset countdown and project overview
    - [x] Improve docs, create tutorials - **ongoing**

Depending on how my main contributions go, there may be scope for additional contributions as follows.

**Stretch 1**: Subject to time / technical constraints, work on natively resetting the ephemery network state in Lodestar. Understand and list any constraints / breaking changes.

**Stretch 2**: Subject to time / technical constraints, create a new DAppNode package for ephemery to be launched to users.

**Ongoing**: Expand work to other client pairs.

## Scope of contributions

My contributions will be made across multiple repositories, covering the following aspects:

**Ephemery documentation**
- additions to ephemery documentation / resources for client-pair setup
- other general documentation relating to running ephemery / troubleshooting issues

**Ephemery specs & EIP**
- validate existing Ephemery specs and propose updates to EIP as necessary
- support wider discussion about Ephemery
- increase online and IRL awareness of ephemeral testnet

**Lodestar repository**
- updates to Lodestar network configs
- ephemery genesis state - as part of a new ephemery package
- ephemery reset - as part of a new ephemery package

**Stretch goals**

- DAppNode package
- Other client updates

## Roadmap

**14 August to 10 September**
- Lodestar fork
- Seek feedback on approach to ephemery genesis generation in Lodestar - i.e. as a separate package
- Submit Draft PR for review
- In parallel, make any useful documentation updates and add my observations on ephemery specs

**11 September to 05 October** 
- Review reset mechanism, plan reset contributions
- In parallel, validate/improve ephemery specs

*Vacation 06-15 October*

**16 October to end**
- Ongoing work on reset mechanism / other stretch work


## Possible challenges

- Different OS may impact configuration options for EL / CL client pairs (especially on mac!)
- Understand CL client prerequisites for implementing genesis and reset natively: there may be other work that is necessary before ephemery can be integrated into a specific client which will impact timings shown on the above roadmap


## Goal of this project

My main goal for the end of the project is to contribute to the Lodestar codebase in order to generate the ephemery genesis. This will enable me to validate the ephemery specs and help to improve/progress the draft EIP.

## Collaborators

### Fellows

Teri and Adedamola are contributing to other aspects of ephemery

### Mentors

Mario Havel, pk910, dapplion @ chainsafe

## Resources

[Lodestar fork](https://github.com/atkinsonholly/lodestar)
[Ephemery open issues](https://github.com/ephemery-testnet/ephemery-resources/issues/1)
[Draft EIP](https://github.com/ethereum/EIPs/blob/04369cb50ee6c1894dec868141e8a32e66dc4f16/EIPS/eip-testnet-draft.md)
