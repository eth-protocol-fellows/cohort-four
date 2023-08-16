

## Motivation

The Ethereum Protocol Fellowship provides aspiring protocol developers like myself a pathway to gaining the experience needed to make meaningful contributions to the core Ethereum protocol. For the EPF I chose to contribute to Lighthouse, an Ethereum consensus client implementation written in Rust.

I started as a Lighthouse open source contributor in April, 2023. I began with simple tasks, making updates to documentation, updating log messages etc. Each contribution I made gave me the confidence and comfort I needed to take on bigger, more complex issues. 

Now as an EPF participant I am tasked with working on a "large" project. However, based on what I've experienced so far, client developers dont just work on individual features. They frequently work on multiple tasks at the same time. Furthermore, client developers provide technical suppport to users and spend time investigating/fixing bugs.

With this in mind, I propose a three-part project. These parts wont be completed in a specific order, but instead will be worked on in parallel.


#### Part 1: The "Big" Project

I'll dig into some infrastructure changes regarding the Lighthouse slasher backend and beacon node. Theres some new database implementations that the Lighthouse team would like to implement and so my work will focus that.

#### Part 2: The "Small" Projects

As I work on the "Big" project, I'd like to continue picking up smaller tasks and issues. This will allow me keep contrubting to Lighthouse while working on a large task. In some respects this emulates the actual work of a core protocol developer which is the whole goal of the EPF!

#### Part 3: Libp2p

I'm really interested in the networking side of Lighthouse. They use rust-libp2p as their peer to peer networking stack. I've decided to make some small contributions to rust-libp2p with the goal of

- Improving its usecase for Lighthouse
- Learning more about libp2p so I can apply what I learn to Lighthouse


## Project description

Each part of the project will be described seperately, but as mentioned before, the work will all be done in parallel.

#### Part 1: The "Big" Project


The slasher backend in Lighthouse currently has support for two databases implementations, LMDB and MDBX. There has been interest from the Lighthouse team to increase the number of database implementations that the slasher backend can support. I will work to add support for three new database implementations: Redb, SQLite, and PostgreSQL. As I add new DB implementations to the slasher backend, I will test them to see if they may be suitable for the beacon node.

The beacon node is at the core of the Ethereum proof-of-stake protocol. It is responsible for running the beacon chain, and uses distributed consensus to agree on blocks both proposed and attested on by validators in the network. Beacon nodes communicate their processed blocks to their peers via a peer-to-peer network, which also manages the lifecycle process of active validator clients.

The beacon node backend uses LevelDB. LevelDB is quite dated and so there will come a time where a new database implementation will be needed. Instead of waiting for that day to come, I will proactively work towards adding at least one new database implementation to the beacon node. In order to add a new database implementation, the beacon node backend must first be modularised.

#### Part 2: The "Small" Projects

From what I've seen in my short time contributing to Lighthouse, Ethereum protocol developers are constantly working on various issues simulataneously. Some of these issues might be large features, while others might be small bug fixes or optimizations. In order to mimic the daily life of a protocol developer I'd like to work on more than just one big issue. My plan is to be a frequent and productive contributor of the Lighthouse codebase. Some things I am currently working on include:


##### Expected withdrawls endpoint

I've added support for the [expected withdrawals endpoint](https://github.com/sigp/lighthouse/pull/4390). This endpoint gets the withdrawals computed from the specified state, that will be included in the block that gets built on the specified state.

##### SSZ block proposal flow support 

According to [benchmarks](https://github.com/ethereum/builder-specs/issues/53) related to encoding and decoding of signed-blinded-beacon-block payloads with SSZ vs JSON

> SSZ seems 40-50x faster
> Considering 20-40ms per coding on average, that's up to 200-300ms JSON latency (or more).
> 
> Sending the data SSZ encoded could reliably shave 200-250ms off each getPayload roundtrip.

The following three pull requests will support SSZ for the full block proposal flow in Lighthouse

- [add ssz support in request body for /beacon/blocks endpoints](https://github.com/sigp/lighthouse/pull/4479)
- [Support SSZ request body for POST /beacon/blinded_blocks endpoints (v1 & v2)](https://github.com/sigp/lighthouse/pull/4504)
- [Add SSZ support to validator block production endpoints](https://github.com/sigp/lighthouse/pull/4534)

##### Small improvements and optimizations

I worked on a small issue that [Improves the readability of transport connection errors](https://github.com/sigp/lighthouse/pull/4540)

I'm working on a task that significantly reduces Lighthouse binary size by Snappy compressing genesis.ssz files

I worked on a small issue that [defaults Content-Type header to json for routes that expect json in the request body](https://github.com/sigp/lighthouse/pull/4575).

My goal is to continue working on smaller issues such as these as I work on my "Big" project.

#### Part 3: rust-libp2p

rust-libp2p is designed as an async, event-based system. This makes it fairly hard to add rich logs in user land because peer information is not always available. This is where tracing comes in.

**Tracing**: A scoped, structured logging and diagnostics system.

Tracing would allow rust-libp2p to offer more detailed logs for users. These "traces" contain more context than traditional logging would. Also it allows users of rust-libp2p to opt in/out of tracing. Opting out of tracing will greatly reduce console noise associated with rust-libp2p. Once tracing is implemented, I will approach the Lighthouse client team about adding tracing support so that they can automatically pick up the improved logs from rust-libp2p. This should improve the Lighthouse developers ability to diagnose and resolve peer to peer network related issues.

The current pull request can be found here:
https://github.com/libp2p/rust-libp2p/pull/4282


## Specification


#### Part 1: The "Big" Project

Implement the following three databases in the slasher backend:

- [ ]  redb
- [ ]  postgres
- [ ]  sqlite

Within each database implementation the following steps will be made:

- [ ] Add new `DatabaseBackend` enum.
- [ ] Create new `xxx_impl.rs` file with types named similarly to other existing backends
- [ ] Add variants to the enums in `interface.rs` for the new backend
- [ ] Get the slasher tests to pass with `DEFAULT_BACKEND` set to the new backend, and `cargo test --release -p slasher`

After the above work is done 

- [ ] Test each implementation to see if its useable within the context of the beacon node. 
- [ ] Choose one implementation to use within the beacon node
- [ ] Modularise the beacon node backend
- [ ] Implement the chose db implementation within the beacon node


#### Part 2: The "Small" Projects

The goals for this portion of my project are a bit more open ended:

- [ ] Attend Consensus/Execution/All Core dev meetings
- [ ] Be a frequent and productive contributor in the Lighthouse codebase

It's hard to create a specification for this portion of the project since its a bit open ended. I hope my explanations in previous sections have given the reader enough context to understand what goals I wish to accomplish here.

#### Part 3: rust-libp2p

I will work on adding tracing to rust-libp2p with the end goal of giving the Lighthouse team cleaner and richer libp2p logs.

- [ ] Add a logging span to the Connection struct, the object that drives all connections in rust-libp2p
- [ ] Within the logging span add the following information: connection id, peer id and address
- [ ] Add tracing to the ping protocol
- [ ] Ensure that the tracing logs for the ping protocol are tidy
- [ ] Do the same for all other protocols in libp2p
- [ ] Once tracing has been added to a stable rust-lip2p version, add tracing functionality within Lighthouse so that it can benefit from the improved logging.


## Roadmap

Note that week 1 indicates the first week of the EPF starting date. Some of the work here has already begun.

#### Part 1: The "Big" Project

##### Week 1-8
Add the three new database implementations to the slasher backend. They should be ready for testing/review by Week 8

##### Week 8-12
Begin modularising the beacon node backend. Continue testing the new slasher backend database implementations. By week 12 we should have decided on which database we will implement for the modularised beacon node backend 

##### Week 12-16
Add a new database implementation to the beacon node backend.

#### Part 2: The "Smaller" Projects

##### Week 1-16

Continue making "small", meaningful contributions to Lighthouse

#### Part 3: rust-libp2p

##### Week 4-6

Add tracing to ping protocol and have those changes finalized by the rust-libp2p team

##### Week 6-12

Add tracing to all other rust-libp2p protocols 


##### Week 12-?

Mention to the lighthouse team that tracing in libp2p should be available "soon" (whenever the rust-libp2p decides to release these changes). Offer to add tracing support in Lighthouse



## Possible challenges

### Scope

I might be trying to take on more than I can "chew" within the timeline of the EPF. As long as I put in the time and effort I believe I can accomplish the tasks laid out in the project proposal. However, unforseen issues could delay/block my progress. It'll be important for me to frequently reevalue my progress so I can narrow my project scope if it becomes necessary in order to accomplish my main tasks.

### Rust

I have about four months of Rust experience. Its a language with a sharp learning curve. Though I've made large strides in terms of my ability to productively write Rust code, I could reach a situation where my lack of certain knowledge in the language could be deterimental to my productivity. I've already had long battles with the Rust "borrow checker". I expect more of those in the future.

### Motivation

I've been putting about 40-50 hours of work weekly on Lighthouse since I began the EPF. This is on top of juggling my current day job. I've frequently had 12+ hour work days and I work weekends. Its been a tough, yet very rewarding experience. I need to keep myself motivated in order to make it to the finish line. It will be important to continually remind myself why I'm working hard. I am not guaranteed to land an Ethereum protocol developer job after the end of EPF, I need to give myself the best chance possible to make that dream a reality.

## Goal of the project

### Practical goals

- Add three new database implementations to the slasher backend
- Modularise the beacon node so new database implementations can be added in a relatively straightforward manner
- Add a new database implementation to the beacon node
- Improve the rust-libp2p developer experience by adding a richer logging experience
- Keep up a steady flow of Lighthouse contributions


### Personal goals

- Have a strong understanding of the Ethereum consensus layer, or at least certain portions of it
- Put myself in a position where I can be hired by a client team or receive additional grants from the Ethereum foundation
- Gain a deep understanding of the libp2p networking stack, especially in the context of how its used in Lighthouse
- Become an expert at Rust
- Build a network of likeminded Ethereum researches/builders


## Collaborators

### Fellows 

- @eserilev

### Mentors

- the Lighthouse team
- the rust-libp2p team

## Resources

WIP
