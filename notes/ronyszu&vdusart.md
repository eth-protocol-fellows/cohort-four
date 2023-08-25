# Ronyszu & vdusart's notes

## Authors:

- Rony Szuster
- Victor Dusart

## Context:

We are participating at the `Ethereum Protocol Fellowship: Cohort 4` as permissionless contributors, and we are working on it on our free time after work.

You can find the project idea we choose [here](https://github.com/eth-protocol-fellows/cohort-four/blob/master/projects/project-ideas.md#api-for-calculating-eth-supply).

**API for calculating ETH supply** *(Tim Beiko)*

An API endpoint that calculates the current supply of ETH. Create basic specification and implementation which should get merged  in at least one EL<>CL combo and maybe even the API specs. Ideally, works on multiple clients and you can compare the output.

### Week 1 (10/07/2023 - 16/07/2023):

During the first week, our goal was to understand how ethers are created and how the supply evolves with time.

For that we find and read some very interesting articles, like this [one](https://blog.bitmex.com/checking-ethereums-total-supply/) made in late 2021 by Bitmex and this stats from Etherscan https://etherscan.io/stat/supply.

They describe how and from where the ethers are created, as well as calculating all the available supply at the time.

We learnt about `Ommer ( Uncle ) Blocks`, and how they increased the production of ethers.

Ommer blocks occur when two or more miners create blocks at almost the same time.

*Ommers blocks were only created when Ethereum was working with the Proof-of-Work consensus, now after the Merge, no ommers blocks are being created.*

Based on what we read our idea was to do the sum of everything that will increase (and reduce) the total ETH supply, and give our result based on that.

### Week 2 (17/07/2023 - 23/07/2023):

The main thing that we did this week was reading about another way to calculate the total ETHsupply. And this thanks to the work done on the Geth client (started with this https://github.com/ethereum/go-ethereum/pull/24723 then continued with this one https://github.com/ethereum/go-ethereum/pull/25662).

This new way consist of calculating the delta between two state tries.

It starts by calculating the issuance and then subtracts from it the Subsidy.

The subsidy is composed of the block reward (regular and ommer ones) but also the quantity burnt via EIP-1559.

Then, it sums all the ETH from all the addresses and get a estimation of the supply with very low error.
