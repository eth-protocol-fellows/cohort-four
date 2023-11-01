# EPF Project Proposal - chirag-bgh

## Project: reth based relay

A relay for the mev-boost network built on top of reth execution client.

## Motivation

Apart from implementation diversity, performance improvements building on top of reth gives ability to extend on reth while receiving upstream changes. Traditionally, forks of geth (such as flashbot’s builder) would fork out a couple day’s worth of engineering time just to merge in upstream changes from Geth. With reth that is completely eliminated.

## Specification

`mev-relay-rs`  

A relay performs two high-level functions: supports the `mev-boost` auction for proposers and `mev-boost` auction for builders

#### Auction for proposers

This half of the design corresponds to implementing the [builder-specs](https://github.com/ethereum/builder-specs) APIs.

##### Components:

- Validator registrations
- Beacon Block Processor
- Auctioneer

#### Auction for builder

This half of the design corresponds to implementing the [relay-specs](https://flashbots.github.io/relay-specs/) APIs.

##### Components: 
- Proposer scheduler
- Builder registry
- Builder submissions manager
- Payload Validator 
    - eth_validatePayload
    - EOB payment verification


### Payload validator 

Bids recieved from buidlers must be validated before forwarding it to the proposer. This is performed using reth as the local EL client. For this a custom API endpoint `eth_validatePayload` is installed to serve the block validaiton and proposer payment verification.

### Future work: 
- Support optimistic relay

### Fellows 

- [chirag-bgh](https://github.com/chirag-bgh)

### Mentors

- [Alex Stokes](https://github.com/ralexstokes)

### Resources

[mev-rs](https://github.com/ralexstokes/mev-rs)\
[reth-based-relay issue description](https://github.com/ralexstokes/mev-rs/issues/129)
