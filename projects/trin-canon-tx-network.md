# Canonical Transaction Index Network Implementation

Giving any device the power to access transaction data
permissionlessly.

## Motivation

Users have only two ways to interact with the Ethereum network:
running a full node or using a centralized service like infura.

Using services like infura beats the whole purpose of Ethereum. We
want to interact with the network without relying on a trusted
provider.

Running a full node has certain "height requirements". You need a big
SSD, a good processor, decent bandwidth, etc. This forces many users
to rely on centralized services.

Lightweight decentralized access to the Ethereum network has been a
long-standing issue. The Portal Network is the best solution proposed
so far. So I want to help build it.

The portal network consists of 5 new decentralized special-purpose
storage networks. These 5 independent networks serve all the data
necessary to interact with the Ethereum protocol:

- History Network (Headers, block bodies, receipts).
- Beacon light client (Beacon chain light protocol data).
- State network (Account and contract storage).
- Canonical txn index (Transaction data).
- Transaction Gossip (Lightweight mempool).

History, Beacon, and State networks are being implemented by the
portal client teams. The spec for the Canonical txn index network is
ready, but nobody is implementing it yet.

Also, documentation for Trin and the portal network in general is not
in the best state. This makes it hard for users to set up their own
light node and for devs to start contributing.

## Project description

This project aims to implement the Canonical Transaction Index Network
in the Trin portal network client while improving existing docs and
creating new docs for the CTI network.

## Specification

There's already a well-defined spec for the [Execution Canonical
Transaction Index
Network](https://github.com/ethereum/portal-network-specs/blob/master/canonical-transaction-index-network.md).

On top of that, my implementation has to be consistent with the other
networks, especially the History network, since it's the closest to
being complete. To do this, I'll take a deep dive into the
[trin-history](https://github.com/ethereum/trin/tree/master/trin-history)
crate.

While working on my project, I'll keep an open eye for opportunities
to improve the existing documentation. My writing will most likely be
published in the [Trin book](https://ethereum.github.io/trin/).

[Reth](https://github.com/paradigmxyz/reth) and
[Foundry](https://github.com/foundry-rs/foundry) are Ethereum projects
written in Rust that are recognized for having excellent
documentation. I'll use them as inspiration for the docs I want to
write for Trin and the Portal Network.

## Roadmap

I'll set my project to be 12 weeks long. The recommended EPF schedule
is to start the project on week 5 of the program and work 11 weeks on
it, but I think I'm ready to start on week 4 and work 12 weeks on it.

- **Learn:** _Weeks one and two_ will be dedicated to learning and
  writing docs about the trin-history crate, the underlying protocols,
  and the CTI network spec.

- **Design:** _Week three_ will be dedicated to writing a design
  document explaining the details of how the CTI network will be
  implemented in the Trin client.

- **Code:** During _weeks four to ten_, I'll code the new network on
  Trin.

- **Test:** In _week eleven_, I'll make sure there's a good set of
  tests for the code I wrote. This includes integration tests on the
  trin repo and compliance with other dev-ops tools like portal hive.

- **Document:** _Week 12_ will be dedicated to filling documentation
  gaps I might have left behind during the project. This includes
  technical documentation about the code I wrote and also user-focused
  docs.

## Possible challenges

- Even though the specs are ready, there could be some edge cases or
  unknown variables I'd have to figure out myself. I consider this a
  challenge because my background is not in research, but this would
  be a great opportunity to get some experience in that area.

- Estimating the time it takes to code something is pretty hard. I
  might run short of time if implementing the network turns out to be
  way more complicated than I thought. For that reason, I left plenty
  of room to code my implementation, and I plan to break down the
  _code_ section of the roadmap into smaller tasks to make it more
  manageable.

## Goal of the project

There are some milestones I'd like to achieve / deliverables I'd like
to show. The further I get in the list, the most complete I'd consider
the project to be.

- [ ] An updated Trin book detailing the implementation of the history
  network.
- [ ] An annotated spec for the Canon tx network.
- [ ] A comprehensive architecture/design document for the Canon tx
  network in Trin (this document should be developer-focused).
- [ ] A working implementation of the Canon tx network.
- [ ] A comprehensive test suite for the newly implemented network.
- [ ] Full devops integration of the newly implemented network.
- [ ] User-focused documentation on the Canon tx network.

At the end of the program, I'll ask myself the following two
questions:

1. Did I deliver a working implementation of the Portal Network's
Canonical Transaction Index network, following guidelines and best
practices, and including comprehensive documentation and testing?

2. If you compare the documentation to the existing docs at the start
of the program, is it easier now to understand the portal network and
use trin? Did you contribute to that improvement?

If I can confidently answer yes to those questions, and all the
deliverables mentioned previously were finished, I'd consider my
project to be successful with all the goals I wanted to achieve.

## Collaborators

### Fellows

[Daniel Ramirez Chiquillo](https://github.com/danielrachi)

### Mentors

[Ognyan Genev](https://github.com/ogenev)

## Resources

- [Trin](https://github.com/ethereum/trin)
- [Trin Book](https://ethereum.github.io/trin/) 
- [Portal Network
  Specs](https://github.com/ethereum/portal-network-specs)
- [Execution Canonical Transaction Index Network
  spec](https://github.com/ethereum/portal-network-specs/blob/master/canonical-transaction-index-network.md)


