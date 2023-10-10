# Naman Garg's Notes

## About me
Hey 👋🏻 welcome! I'm Naman, a proud software engineer and for this EPF cohort I worked on Verkle trie implementation in Nim (Nimbus client) and Java (Besu client).

For quite some time I had in mind to explore the core ethereum protocol and what could be better than EPF? So I stepped down from my position at Biconomy and with all heart pursued what I love. EPF is an amazing initiative by the Ethereum Foundation to help people get started with Ethereum protocol development. I'm really excited to be working with the clients and to be contributing to the Ethereum ecosystem.

## Author
Twitter (X): https://twitter.com/namn_grg

LinkedIn: https://www.linkedin.com/in/namn-grg/

Github: https://github.com/namn-grg

Telegram: **@namn_grg**

HackMD: https://hackmd.io/@namngrg

## Verkle Tries
During the EPF I kept my focus on Verkle Tries. Why? Because it can help Ethereum achieve statelessness! The key benefit of the vector commitments used in Verkle is that they allow for much smaller proof sizes (called witnesses). Instead of needing to provide hashes of all "sibling nodes" at each level, as in Merkle Trees, the prover needs only to provide all parent nodes (plus an extra proof, called an optional) along the paths from each leaf node to the root. Since we no longer need to provide all sibling nodes, we can structure Verkle Tries to be much wider than Merkle Trees. All of this allows for much smaller witness sizes. 

What’s so great about small witness sizes? Large witnesses are the key problem standing in the way of statelessness. When witnesses (proofs) are small enough, they can be contained within each block. This allows for the verification of any block using only what’s contained within the block itself. 

The general principle of “statelessness” is that nodes verifying blocks no longer need to store state.

## Appreciation
Honestly, before EPF I had never contributed to ethereum protocol development. Understanding of core ethereum was new to me in every sense. I had to learn a lot of things from scratch but this is what pushed me. **Late nights and early mornings** I had them both. 

The line **"Without core developers, Ethereum protocol doesn't exist"** from the town hall meeting, ignited a spark and it was not a faint spark - it actually burnt a fire in me. Slowly I started to get to know EF researchers and core devs and what actually kept me in the game was the constant support that I got from them (best thing). Looking back at the start of the cohort, I have an entirely new perspective, network and twitter feed (😅).

Imagine doing 1v1 coding sessions with 10+ yoe engineers and getting to know their thought process. It's a different feeling altogether. Shoutout to Daniel, Thomas, Zahary, Ignacio, Gballet and my fellow cohort members for helping me out in this journey.

## Future Plan
Ethereum protocol development has changed me inside out. I would like to continue working on the same and would be **open to any roles that align with my interests** - hire me! 

## Weekly Updates
- [Week 0](https://hackmd.io/@namngrg/epf4w1)
- [Week 1](https://hackmd.io/@namngrg/epf-w1)
- [Week 2](https://hackmd.io/@namngrg/epf-w2)
- [Week 3](https://hackmd.io/@namngrg/epf-w3)
- [Week 4 and 5](https://hackmd.io/@namngrg/epf-w4-w5)
- [Week 6 and 7](https://hackmd.io/@namngrg/epf-w6-w7)
- [Week 8 and 9](https://hackmd.io/@namngrg/epf-w8-w9)
- [Week 11 and 12](https://hackmd.io/@namngrg/epf-w11-w12)
