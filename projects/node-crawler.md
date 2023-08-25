# Node Crawler

Give [Node Crawler][1] some TLC, and add a new feature to allow a user to scan
their own node so they can know it's publicly accessible.

## Motivation

Node Crawler hasn't been updated in some time. It could use some TLC. Updating
the dependencies, language, and some refactoring to the standard file structure
we expect for a Go project.

When I was setting up my Ethereum node, I wanted to know if it was publicly
accessible, but I did not find any tools which I thought did this in a good way.

When I proposed making this tool on the EPF Discord channel,
[Mário][2] suggested that I could add it to the Node Crawler. This idea is
already an issue on the project: [Discover my node][3]. Hopefully, having this
will lead to a healthier state of the network with more nodes properly exposed
to the public internet.

## Project description

Update the dependencies, language, and refactor the project to the directory
structure we would expect of a Go project.

When the refactoring is done, add the new feature to scan/add a node to the
database for scanning.

## Specification

For the new feature, I would need to add a new page to the website where a user
can scan/add their node, and the ability to see if the scan is successful or
not. A history of scans and their success would be an interesting feature.

## Roadmap

I don't really have one. I will work on the project when I have time.
I'm working in a best-effort capacity because I still have a full time job to
tend to.

## Possible challenges

I have some experience with Go, but less so with front-end, so this part would
be the most challenging part. From what I see, it doesn't look too difficult,
but maybe someone could help me make it look nice. :)

## Goal of the project

The current state of the project is that it hasn't been contributed to in some
time, so I hope I can get it into some better state, and add my feature for
scanning your node to make sure it's publicly accessible.

## Collaborators

### Fellows

[Angaz][4]

### Mentors

None

## Resources

[Node Crawler][1]

[1]: https://github.com/ethereum/node-crawler
[2]: https://github.com/taxmeifyoucan
[3]: https://github.com/ethereum/node-crawler/issues/20
[4]: https://github.com/angaz
