# Project Proposal

Become a core contributor for [Reth](https://github.com/paradigmxyz/reth), a new Ethereum execution client written in Rust!

Here you can find my full project proposal (work-in-progress): [Reth Contributor](https://alessandromazza.notion.site/Project-Proposal-dac64b916b254652a1d2a742865245d9?pvs=4)

## DEPRECATION WARNING
The following document is deprecated and may no longer be relevant or accurate. Please use the link above for my up-to-date proposal!

## Motivation

Client diversity is one of the most important features of Ethereum as it helps to further decentralise the network. Right now there are already several implementations for the Ethereum protocol, divided in consensus and execution clients, as you can see from the image below.

![client_diversity](https://ethereum.org/static/247bd1fc708353287dbbca4f26b68716/7831d/client-diversity.png)

Reth is an execution client and it’s the first one written in the Rust language, another good thing since it creates diversity also on the programming languages used for Ethereum clients. It aims to be very fast (Rust language is known for its speed and reliability) and optimised in order to be able to satisfy different users:

- big companies who need power and speed, have lots of money to invest in machines and infrastructures.
- normal users who just want to run their own node with a normal computer.

I am really excited to contribute to such a significant software project. Working on it lets me study and gain deep knowledge of various aspects of the Ethereum protocol.

## Project description

My project for this EPF is divided into two parts:

1. Create an implementation of [EIP-7212](https://eips.ethereum.org/EIPS/eip-7212) for Reth. This EIP aims to introduce a precompile for elliptic curve operations on the ”*sepc256r1*” curve, which is different from the ”*sepc256k1*” used on Ethereum (and Bitcoin) for signatures verification.
2. Solve a lot of smaller issues on the Reth repo, covering various aspects of the protocol and of an Ethereum node.

## Specification

### EIP-7212

As of `FORK_TIMESTAMP` in the integrated EVM chain, add precompiled contract `P256VERIFY` for signature verifications in the “*secp256r1*” elliptic curve at address `PRECOMPILED_ADDRESS` in `0x19`.

// **TODO**: I have to study further this EIP and start planning a more concrete specification and documentation of it.

### Smaller Issues

I want to take lots of issues in the Reth official repository and contribute to it. Here you can find the full list of my contributions: [Commits · paradigmxyz/reth](https://github.com/paradigmxyz/reth/commits?author=alessandromazza98)

## Roadmap

### EIP-7212

```mermaid
gantt
    dateFormat  YYYY-MM-DD
    title Project Roadmap

    section Study
    EIP-7212 + REVM      :a1, 2023-08-28, 2w

    section Implementation
    Implement + Feedback         :a2, 2023-09-11, 7w

    section Final Review
    Complete Review + Presentation                  :a3, 2023-10-30, 2w
```

### Smaller Issues

Each issue has its own mini-roadmap associated to it.

## Possible challenges

- Understand very well EIP-7212 and especially Revm, which is the EVM implementation used by Reth. Also EIP-7212 is still in review and could have breaking changes so I have to keep updated on that. EIP. It shouldn’t be an hard problem but this is for sure the first challenge I will have to overcome.
- Reth repo is very active and issues are sniped very fast so it’s not super easy to be able to work on every open issue.
- Reth is a huge project (since it is a full Ethereum execution client) and it’s not easy to learn all its aspects and functionalities. This could be a problem to solve some very hard issues.

## Goal of the project

### EIP-7212

I want to have at least a draft implementation of EIP-7212 for Reth. Something that can be not perfectly optimised yet but that works properly.

### Smaller Issues

It’s not very easy to predict a clear goal for solving smaller issues since they are all different and can take more or less time, but my general idea is to solve an average of at least one issue per week (2 weeks if it’s a bigger and longer one).

It’s also important to note that often you need to wait some time for reviews so my plan is to usually work on several issues at the same time so that I can switch between them when I receive some feedback or reviews.

## Collaborators

### Fellows

[Alessandro Mazza](https://github.com/alessandromazza98)

### Mentors

[Georgios Konstantopoulos](https://github.com/gakonst)

## Resources

1. [Reth repo](https://github.com/paradigmxyz/reth)
2. [EIP-7212](https://eips.ethereum.org/EIPS/eip-7212)
3. [EIP-7212 discussion](https://ethereum-magicians.org/t/eip-7212-precompiled-for-secp256r1-curve-support/14789)
