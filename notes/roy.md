# Roy's notes
Hi everyone, I am Roy from a Security Research background. I'm interested in the p2p network and client infrastructure in general. 

I am planning to look into detail about the following project and choose one topic to work on during this fellowship. 

- [X] Prysm's Beacon APIs Auditing
- [ ] ~~Fuzzing proposed by Frederik~~
- [ ] ~~Alex Stokes's projects~~

I would like to choose "[Prysm's beacon API audit](https://github.com/eth-protocol-fellows/cohort-four/blob/master/projects/project-ideas.md#auditing-beacon-apis-in-prysm)" project. 

This note is for the purpose to share some basic info I collected and call for collaboration. 

## How I start to study Prysm's Beacon API

Firstly:

- [X] [Phase0 of Core beacon chain consensus spec](https://github.com/ethereum/consensus-specs/blob/dev/specs/phase0/beacon-chain.md)
- [X] [Prysm's Developer Wiki](https://docs.prylabs.network/docs/contribute/contribution-guidelines)
- [X] Understanding the system design and the building/testing tools (Bazel).
- [X] According to project description, there are [EPF's third cohort participants](https://github.com/eth-protocol-fellows/cohort-three/blob/master/projects/prysm-beacon-api-compliant-validator.md) had to contribute some to API parts.

After I did the initial research, I found this system design is quite in my comfortable zone. Although I use more `go test` than `bazel` in my work, I think `bazel` is easy to learn and much easy to keep the building/testing experience consistent.

Also, the e2e testing is quite completed in this project. At the same time, since I did some geth related P2P and API jobs, this project's goal looks quite natural and achievable to me. 

Follow up, I will get my hand dirty and reach out to a mentor to get things to move.
* Try to fix some issue in the issues list
* Filter out related test cases and setup a benchmark baseline. 
* Identify the scope of the project topics and prepare a draft roadmap and specification.
* Reach out to Mentors and Collaborators before diving deep into coding. 

In furture, please find my updates in [development-updates.md](https://github.com/eth-protocol-fellows/cohort-four/blob/master/development-updates.md)
