# Eth Deb Repository

Creating a universal repository for Ethereum related packages

## Motivation

    Can we imagine a future where interacting with Ethereum-related software is as effortless as download and run?

This project stems from a fundamental question: What if utilizing Ethereum-related software was a straightforward endeavor? The inspiration for this initiative was drawn from the concept of the [eth deb repo](https://notes.ethereum.org/@MarioHavel/ethdebrepo). Presently, setting up and running nodes on the Ethereum network involves a series of manual procedures, including downloads, verifications, and configuration adjustments. This complexity poses a challenge, particularly for individuals without a technical background. The ultimate objective is to change this paradigm and make running nodes accessible to everyone. It's important to note, however, that simplifying node operation requires significant effort that exceeds the scope of this endeavor, so the work related to this will be scoped for creating debian repository, which would open the door for future improvements around this topic.

Another perspective to consider is that many development teams lack the resources to adapt their software for various distributions, as this entails a substantial time investment. Having a centralized repository for Ethereum-related packaging, focused solely on the mission of making Ethereum software user-friendly, could greatly alleviate this issue.

Third aspect, that node runners are the most up to date on the topics of what configuration or security settings needs to be adjusted, or what issues a platform might pose. It's good idea to provide a central area where such discussions can be exchanged.

The choice of Debian-based distributions is driven by their significant presence in the market, with a combined market share exceeding 30%. For more in-depth information, please refer to the enclosed statistics.

User Story: Simplifying Ethereum Node Installation for Debian Users

**As a** blockchain enthusiast who favors Debian-based distributions for their stability and familiarity,

**I want** to easily install Ethereum nodes on my Debian system without dealing with intricate setup processes,

**So that** I can actively participate in the Ethereum ecosystem, contribute to its activities, and stay up-to-date with the network developments.

## Project description

The proposed solution contains two parts

- Establishment of a repository and generation of reproducible builds for two architectures using debmake (pbuilder) or debcrafter.
- Development of configuration and service packages to streamline node operation through debcrafter (specific details are currently being discussed).

## Specification

How will you implement your solutions? Give details and more technical information on the project.

- Reproducible builds can be accomplished through minor adjustments to debmake.
- Debcrafter offers comprehensive specification files to enhance configuration and security aspects of the generated binaries. Combining these two components is a key goal.
- Comprehensive documentation to guide future maintainers.
- A dedicated space for reporting bugs, issues, and questions, most likely in a GitHub repository.

## Roadmap

What is your proposed timeline? Outline parts of the project and insight on how much time it will take to execute them.

- September - October: Creation of binary packages.
- September: Collaboration with the mentor to determine the content of the configuration and service packages.
- October - November: Focus on developing the configuration and service packaging.

## Possible challenges

What are the limitations and issues you may need to overcome?

- Within the given timeline, it might not be feasible to create packages for all architectures.
- Similarly, packaging all Ethereum-related software might be unrealistic within the project's timeframe.
- Configuration and service packages will likely feature a default minimal setup.
- Given the diversity of node settings, providing configuration options for every scenario may not be achievable within this timeline.
- Ensuring security is a priority, but it's recognized that achieving complete security might require more effort and isn't the primary focus of this project.

## Goal of the project

The end goal is to include binaries for consensus and execution clients within a repository, accompanied by supplementary service and configuration packages for these clients.

In essence, the objective outlined in the original proposal encapsulates this vision well. Link
For clarity, the ultimate goal can be summarized as follows:

- Running `apt install geth-mainnet-full` would seamlessly install all necessary software components, such as the go-ethereum client, while configuring a default full node mainnet setup and initiating it as a service for immediate usability.
- Running `apt install lighthouse` would likewise install all prerequisites (libraries and eth1 client), establish a default configuration, and prepare the software for immediate use.
- By executing `systemctl stop besu`, the Besu client can be gracefully stopped.
- The option to adjust optional configuration settings for a package can be accessed through `dpkg-reconfigure` geth.

## Included software

Execution clients

    Go-ethereum
    Nethermind
    Besu
    Erigon

Consensus clients

    Lighthouse
    Prysm
    Teku
    Nimbus
    Lodestar (npm supply chain attacks might make this not possible)

## Acceptance criteria

Acceptance Criteria:

1. The project provides a centralized Ethereum-related debian repository accessible to users. (this will only support one debian distribution)
2. The repository contains packaged software that simplifies the process of setting up and running Ethereum nodes.
3. Detailed documentation is available to guide users through the installation and configuration process.
4. Discussions and user feedback related to configuration, security settings, and potential issues have a dedicated space within the repository.
5. The debian repository is set up to allow for future improvements and expansion of features beyond the initial scope.

Not in scope 6. The repository includes Ethereum-related software adapted for various distributions, ensuring compatibility across different systems. 7. The repository's packaged software undergoes verification to ensure security and authenticity.

## Collaborators

### Fellows

If you are interested let me know.

### Mentors

Mário Havel (@taxmeifyoucan) Martinzs (@???)

## Resources

Links to repositories, PRs, and other valuable resources constituting the project will be provided soon.

[ethdebrepo](https://notes.ethereum.org/@MarioHavel/ethdebrepo)
[Debian maintainers guide to package maintainers](kixunil)
[Debian go packaging guide](https://go-team.pages.debian.net/packaging.html)
[dh-make-golang](https://github.com/Debian/dh-make-golang)
[creating Debian packages from Go packages](https://people.debian.org/~stapelberg/2015/07/27/dh-make-golang.html)
[fpm](https://fpm.readthedocs.io/en/latest/packages/deb.html)
[reprprepro](https://wikitech.wikimedia.org/wiki/Reprepro)
[Pbuilder](https://wiki.ubuntu.com/PbuilderHowto)
[Cowbuilder](https://wiki.debian.org/cowbuilder)
[Reproducible builds](https://reproducible-builds.org/docs/)
[Debcrafter](https://github.com/Kixunil/debcrafter)
[Linux Hardening guide](https://madaidans-insecurities.github.io/guides/linux-hardening.html)
[npm supply chain attacks](https://hackaday.com/2021/10/22/supply-chain-attack-npm-library-used-by-facebook-and-others-was-compromised/)
[distro market share](https://survey.stackoverflow.co/2023/?ref=itsfoss.com#technology)
[debian market share](https://www.datanyze.com/market-share/operating-systems--443/debian-market-share)
