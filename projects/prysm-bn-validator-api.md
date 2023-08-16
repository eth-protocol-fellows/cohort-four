# Prsym Beacon Node - Validator API

Implementing the standard Ethereum Beacon API for validator clients in the Prysm beacon node

## Motivation

In production, the Prysm beacon node exposes a GRPC API for consumption by the Prysm validator.

As a result of the standard Ethereum [spec](https://ethereum.github.io/beacon-APIs/#/Validator), this implementation is incompatible with other validator clients.

Implementing the standard API will allow different validators to be run with the Prysm beacon node, furthering client diversity.

## Project description

An HTTP implementation of the Beacon API for validators currently exists in the Prysm beacon node.

However this is a wrapper over a GRPC implementation, exposed using a fork of grpc-gateway. This is not ideal for several reasons, outlined in more detail in [prysm/#11580](https://github.com/prysmaticlabs/prysm/issues/11580).

It also requires auditing & benchmarking to ensure optimal performance.

## Specification

A specification that actively tracks this project is available on [prysm/#12635](https://github.com/prysmaticlabs/prysm/issues/12635).

Beyond this, technical details for the various endpoints are out of the scope of this document.

## Roadmap

As of August 15, HTTP handlers have been implemented for 6 of the 27 endpoints.

The majority of this work has been contributed by the Prysm team, while I am currently working on my second endpoint.
Other fellows have also expressed interest in contributing to the project, so the exact timeline will vary according to these factors.

I am aiming towards implementing 1-3 endpoints a week, so this should be within scope for the 13 weeks until Devconnect.


## Possible challenges

Completing this project is largely a matter of time, as opposed to difficult technical challenges.
The plan outlined here may see delays depending on my understanding of the consensus layer and its implementation in Prysm, and the time it takes to introduce potential architectural changes to implement the API spec optimally.

## Goal of the project

All beacon node API endpoints consumed by the Prysm validator (listed in [prysm/#12635](https://github.com/prysmaticlabs/prysm/issues/12635)) should be served by HTTP handlers, and any GRPC related code (middleware, handlers) should be removed from this execution path.

Optimistically, I would aim to run a combination of the Prysm beacon node and a different validator client (e.g. Lighthouse) in production at Devconnect.

## Collaborators

### Fellows 

[Anukul Sangwan](https://github.com/anukul)

### Mentors

[Radosław Kapka](https://github.com/rkapka)

with code reviews and support from different members of the Prysm team

## Resources

- [Proposed project idea](https://github.com/eth-protocol-fellows/cohort-four/blob/master/projects/project-ideas.md#auditing-beacon-apis-in-prysm)
- https://github.com/prysmaticlabs/prysm/issues/11580
- https://github.com/prysmaticlabs/prysm/issues/12635
- https://github.com/prysmaticlabs/prysm/issues/12682
- https://hackmd.io/X9Epjx7ARMOXES0fye3ZRw
