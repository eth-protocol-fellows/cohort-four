# Beacon Chain Attestation Simulator in Lighthouse

Implementing and adding the attestation simulator metric for attestation reward analysis in the Lighthouse consensus client 

## Motivation

Attestation rewards make up a significant chunk of a validator's rewards, accounting for, on an average, ~84.4% of all rewards. Attestations, although committee and slot assignments are random, occur for every active validator once each epoch. Along with rewards, attestations are also subject to penalties for being missing, late or incorrect. They are hence probably the most important economic metric to keep track of for a validator over the long term. It becomes imperative, then, to have some mechanism of seeing how certain attestations would have performed in terms of rewards earned and penalties incurred, i.e. there is a need for an 'attestation simulator' of sorts to help validators effectively analyse this.

## Project description

The project consists of implementing and adding an attestional simulator metric in the Lighthouse client. This would involve the client 'pretending' to create an attestation every slot, and then seeing how that attestation would have performed.

## Specification

This is still being chalked out with the Lighthouse team. You can see preliminary details [here](https://github.com/sigp/lighthouse/issues/4526)

## Roadmap

Weeks 1-4: Reading the ETH2 book in-depth, discussing the exact spec with the Lighthouse team, contributing to issues which improve normal attestation metrics

Weeks 2-6: Implement the simulator from scratch and see which modules/components it relies on, and improve those as well

Weeks 6-12: Test out the simulator with actual in-production clients

## Possible challenges

TBA

## Goal of the project

The success of this project has two aspects:

1. Improving and working on issues related to attestations in Lighthouse, especially those related to rewards/penalties

2. Implementing an end to end attestation simulator to be used in production. 

## Collaborators

### Fellows 

[Ameya Deshmukh](https://github.com/ameya-deshmukh)


### Mentors

[Paul Hauner](https://github.com/paulhauner)

## Resources

Provide links to repositories, PRs and other resources which constitute the project.
