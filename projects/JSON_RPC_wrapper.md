# Suisu -- Execution REST

That'll do JSON-RPC, that'll do.

Master copy at: https://github.com/tsujp/suisu/blob/master/epf/project_proposal.md

## Motivation

The current JSON RPC API (herein: JRA) suffers from imperfect standardisation and ad-hoc per-execution-node extensions
resulting in difficult to use and tightly coupled applications. If the goal of Ethereum is a distributed and
implementation-agnostic protocol then the current JRA, while making great strides, currently fails to meet this requirement.

Further standardisation improvements to the JRA (e.g. EIP-1474) _could_ alleviate these problems but given the Beacon chain's implementation
of a REST API this represents a good opportunity to address the current Execution JRA's shortfalls with a REST API
specification and reference JRA wrapper implementation. These two components will (propose to) extend the Execution
API protocol.

## Project description

1. A REST API specification for the Execution layer.
2. A reference implementation of (1) by wrapping the current JRA.

## Specification

There are 3 major domains required for the project:

1. Iteration of JRA, and discovery of any Execution-client specific quirks; _leading to..._
2. REST API specification and self-testing against reference implementation; _which requires..._
3. General Execution client infrastructure access.

The nature of the project requires these 3 happen simultaneously and iteratively as the project progresses so careful organisation and synchronisation between these areas of the project is _required_. This can be thought of as a loop with the project timeline comprising of as many loop iterations as possible.

Prior to the main project loop there will be a t-shirt sizing estimate for various areas of the JRA and a rough order of attack for methods to convert to the REST specification.

The general looping process is:

1. Choose subset of JRA to develop REST specification for. Initially this will be the clear-cut easiest until all 3 domains are established at which point ad-hoc from up-front estimate planning.
2. Develop REST specification for (1) and importantly note down any predicted future consequences and/or affected items within the JRA or REST specification.
3. Implement reference API-surface for (2); the chosen stack for this is a VCL configuration for Varnish, and if required (or in-place of) an API written in Zig.
4. Implement tests for (3) using Execution client backend, i.e. calling out to real Execution clients running on both testnets and mainnets (any transactional endpoints will be testnet-only).

1. Initially the specification will be developed in-tandem with the reference implementation (planned VCL configuration for Varnish) as the first JRA methods to enter the REST specification will be the simplest.
2. With the simpler JRA methods specified in REST and wrapped an automatic test suite will be started to confirm the reference implementations ability to meet its own specification. This will include various Execution client backends (from ecosystem providers, testnets etc) to make JRA calls against.

## Roadmap

### T-Shirt sizing

Weeks 1 and 2 involve experimenting with wrapping complexity and which REST endpoints can be implemented, including any changes. This serves to lay out a _rough_ map of what to tackle and in what order.

### Test harness

Week 3 is dedicated to developing a test harness as the primary means of development is iteratively implementing the chosen REST specification and testing that implementation immediately and continuously; thus a test harness is required.

### Loop

For the rest of the project:
1. Choose some part of the REST specification to implement (informed during t-shirt sizing).
2. Implement.
3. Add validation tests to test harness.
4. Go back to (1).

## Possible challenges

- As of this project proposition a comprehensive list of JRA differences per Execution client are not known (to projecet participants). _General_ differences are but _all_ differences are not and this process will require continuous discovery as the specification develops.
- Leaky abstractions and/or abstraction inversion when trying to reconcile Execution client deviations from JRA specification (where there is one).
- Time. This project comprises of a maximal amount of feedback loops; while generally any project wants this property it is required here due to the simultaneous development of a REST API specification, and reference implementation of that specification which itself wraps current imperfect JRA implementations. Predicting all variants and associated solutions ahead of time is not practical beyond a general case so progress comes from iteration however if the landscape is extremely (note: doubted but possible) non-uniform this could cause the reference implementation to take too much time to implement (too many cases to consider for example) precisely _because_ it must wrap existing imperfect APIs.
- Fuzzing may help identify any unknown non-uniformity but project participants have no experience fuzzing and so if/when its need arises any challenges will have to be navigated without the preparation other areas of this project have received.

## Project goals

- Predictable and fully standardised REST API. _Note that this DOES NOT MEAN 100% WRAPPING OF THE JRA; it means that was does exist behaves predictably as per its standard and so is safe to use. Further JRA coverage can be developed over time as needed/wanted_.
- Test suite covering all (reasonably) known cases for the specified and implemented REST API specification.
- Reasonably performant wrapper implementation.
- EIP with REST specification.

## Collaborators

### Fellows 

Potentially @Amit0617.

### Mentors

@lightclient

## Resources

[GitHub repo](https://github.com/tsujp/execution_rest)

#### Etymology

- 수행(하다): (n. (v.)) To carry out a duty or perform (execute) a task.
- 쉬다: (n.) Rest.

Combine and abbreviate both words (without attention to grammar) and romanise for
ease of spelling to yield: 쉬수 (Suisu).
