# kaydenML's notes

## Introduction

Hi my name is Kayden Moroz Liebl and i am very excited to participate in this years cohort working hard to improve myself and my programming and problem-solving skills and learn even though im a permissionless participant.

 

## Planned Projects

Glados

- Project Proposal
  - https://github.com/KaydenML/cohort-four/blob/master/projects/Glados-PortalNetwork.md

I’m interested on working hard on Glados because I believe that it suits my skill set the best and is a great place to improve myself and learn and am planing on working hard creating interesting ways to visualize important data through different graphs on the page and trying to make everything look nicer and cleaner as well as the main page of glados. I am really interested in working hard and learning many new things as well as making many useful contributions towards glados during this year's cohort and excited to be able to contribute in every way that I can either that be by large or small implementations.


## Weekly Updates

- [Week 0](https://hackmd.io/msw-q59mQ1WIEy2s0qwbSQ?view) 
- [Week 1](https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/B1fzDR492)
- [Week 2](https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/S1t-Tmyon)
- [Week 3](https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/HkVl5dhjh)
- [Week 4](https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/Bytjmsfh3)
- [Week 5](https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/S1wFfX23h)
- [Week 6](https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/SynHLNBTh)
- [Week 7](https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/SkDUd50an)
- [Week 8](https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/SJcjUNtC2)
- [Week 9](https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/HJj1OtQkp)
- [Week 10](https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/S1iIpQ61a)
- [Week 11](https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/SJK8N0Sga)
- [Week 12](https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/S1KdrvgWT)
- [Week 13](https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/rkobPsYWp)
- [Week 14](https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/H10DvymMa)
- [Week 15](https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/H1aQpKhM6)
- [Week 16](https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/SygvXIH7T)
- [Final Update](https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/HJV0WR5mp)

## Weeks
- Update 1 https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/B1fzDR492
    - during the first week of the program i did some tests to see if my graph was running in sub-linear time on postgres because previously when i was running the the tests and tests with sqlite the tests would some up with linear time but in the end i found the cause was that my query was not compatible with sqlite and it did indeed run in sub-linear time.
    - I also started reading the Ethereum development documentation reading 8 of the topics https://ethereum.org/en/developers/docs/

- Update 2 https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/S1t-Tmyon
    - This week I had my first meeting this week with my Mentor of the project Mike Ferris, we talked about my Pie Chart PR I was working on at the time and planned to do weekly meetings going forward.
    - I continued to read the Ethereum development documentation and ended up reading 4 more topics.
    - I read the Portal Network docs https://ethereum.org/en/developers/docs/networking-layer/portal-network/
    - I read around half of the portal-network-specs git Readme section this week https://github.com/ethereum/portal-network-specs
    - Week 2 I also watched two presentations by Piper Merriam
        - https://www.youtube.com/watch?v=jAX_bgcESoc.
        - https://www.youtube.com/watch?v=jAX_bgcESoc.https://www.youtube.com/watch?v=0stc9jnQLXA

- Update 3 https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/HkVl5dhjh
    - Had another meeting with Mike Ferris we created a list of tasks for me to work on and tackle and tasks to work on going forward
    - I styled the content dashboard page adding clean bootstrap cards like I had added to the front page for the Pie Chart I had been working on
    - I displayed the total amount of nodes in the database on the front page via Mikes request
    - I fixed a migrations issue that prevented us from running Glados locally https://github.com/ethereum/glados/pull/144
    - I then finished reading the portal-network-specs readme section https://github.com/ethereum/portal-network-specs
    - Then watched another presentation Piper Merriam had done https://www.youtube.com/watch?v=M3HExSykXFI&ab_channel=UZHBlockchainCenter

- Update 4 https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/Bytjmsfh3
    - This week i began writing my first rust test to help us ensure that we do not encounter the same migration problem I fixed in the previous week.
    - I read the rust test documentation to start figuring out and learning how to write tests in rust https://doc.rust-lang.org/book/ch11-01-writing-tests.html
    - I also watched a few videos on writing tests in rust this week
        - https://www.youtube.com/watch?v=3Zg5-evaup0&ab_channel=dcode
        - https://www.youtube.com/watch?v=18-7NoNPO30&ab_channel=Let'sGetRusty
        - https://www.youtube.com/watch?v=vLOSJoLwwmU&ab_channel=shanemoloney
    - Started to work on my project presentation

- Update 5 https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/S1wFfX23h
    - I finished writing the test i began working on in the previous week https://github.com/ethereum/glados/pull/148
    - I styled the home page of Glados without my graph implementation on the same page, because I learned it's good practice to create separate PR's for these sorts of things
    - I styled the Network dashboard like i did to the content dashboard adding clean bootstrap cards https://github.com/ethereum/glados/pull/150
    - I watched 3 hour’s worth of videos on Kademila
        - https://www.youtube.com/watch?v=1QdKhNpsj8M
        - https://www.youtube.com/watch?v=3Y6vLTzM7zA
        - https://www.youtube.com/watch?v=NxhZ_c8YX8E
    - DanielRachi sent me his notes he took on Kademila which where really helpful https://hackmd.io/@danielrachi/SkQuHtMi2
    - I read some documentation on discv5
        - https://github.com/ethereum/devp2p/blob/master/discv5/discv5.md
        - https://github.com/ethereum/devp2p/blob/master/discv5/discv5-wire.md
        - https://github.com/ethereum/devp2p/blob/master/discv5/discv5-theory.md
        - https://github.com/ethereum/devp2p/blob/master/discv5/discv5-rationale.md
    - I watched a long video on discv5 https://www.youtube.com/watch?v=o17ly2hej9w
    - I also improved my project proposal after receiving JoshD's feedback

- Update 6 https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/SynHLNBTh
    - This week I finished styling the rest of the Glados pages with clean bootstrap cards
        - https://github.com/ethereum/glados/pull/145
        - https://github.com/ethereum/glados/pull/149
        - https://github.com/ethereum/glados/pull/150
        - https://github.com/ethereum/glados/pull/151
        - https://github.com/ethereum/glados/pull/152
    - Spent most of this week working on my Project Presentation and improving it as much as possible after receiving really great feedback from both JoshD and Piper Merriam
    - I also spent a bunch of time practising my presentation to myself this week to be able to give a great presentation after improving it so much

- Update 7 https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/SkDUd50an
    - This week i began starting to pair with my mentor Mike Farris on the Dht Census implementation for 7 hours this week, the Dht Census is what allowed me to finish my Pie Chart Graph and to start begin working on the next graphs I had planed to work on and complete with in the time span of the cohort
    - I finished my final draft of my project presentation
    - refined my slides and practised giving the presentation to myself a few more times 
    - Fixed a few improvements Mike Ferris asked me to do.
    
- Update 8 https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/SJcjUNtC2
    - I did my final practice for presenting my project on monday
    - I then presented my Project Proposal to everyone on tuesday
    - I started to implement a segmental control feature into glados's content dashboard to allow us to toggle between each section within the dashboard and completed it by the end of the week https://github.com/ethereum/glados/pull/156
    - I began researching into dynamically loading the items into Glados to improve load times
    
- Update 9 https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/HJj1OtQkp
    - I read some documentation on dynamic loading
    - I Paired again with Mike Ferris on the Dht Census for many hours this week and later on in the week we finished it and it was merged
    - With the Dht Census merged i spent a bunch of time reading the code really trying to understand it and everything we worked on so I could finish my Pie Chart graph and start to work on my next graph
    - Around the end of week 9 I finished my Pie Chart graph implementation

- Update 10 https://hackmd.io/@v8QYUEqNQI-q90vwuMaJaw/S1iIpQ61a
    - This week i fixed a few minor fixes Mike Ferris asked me to fix regarding my Pie Chart Graphs PR, after that I decided on the next graph i was going to work on which ended up being a radius density graph.
    - I spent a lot of time creating a prototype graph on google spreadsheets trying to find the best representation for the data
    - I then spent as bit of time trying to figure out how i was going to pull the data i need from the database and also spent some time looking to see how Trin handled the radius
    - I fixed a rlp (Recursive Length Prefix) encoding bug that was occurring with my pie chart where only the Trin node’s were appearing on my graph and the Fluffy nodes were appearing as Unknown.
    - I spent some time researching and improving my knowledge on things what is a byte, what are hexadecimal numbers, how can I convert binary to a hexadecimal number, learning how to read binary numbers

- Update 11 https://hackmd.io/ZA7C4txJRe2rGXLft8piag?view
    - I spent a ton of time working on my query for my radius graph 
    - After looking at Jason Carvers code in Trin I realised that I would be able yo us some of his code and loop over it
    - I fixed a few more minor fixes for my Pie Chart graph and then it ended up being merged https://github.com/ethereum/glados/pull/136
    - After speaking with Mike Ferris I ended up changing the model for the graph I originally planned to use and decided to display the data through the graph he suggested which was a basic density plot
    - I displayed the audit stats on the front page and it was merged shortly after https://github.com/ethereum/glados/pull/165
    - I finished my sqlite query and then converted it to rust sea-query so i would be able to template the data from the database through my html graph
    - I then looped over the code i got from Trin
    - I then started to try and display the data through the graph

- Update 12 https://hackmd.io/3frH_NoZSZ-oBnfoJ32LQQ
    - I displayed the data from my query through the density graph but i was having a really stuff time getting the data to display through the graph in a way that looked nice and how i wanted it to look
    - I decided to switch to a bar chart graph instead of a density graph because trying to get the data to display nicely through causing to much trouble and taking up way to much time
    - I watch a few videos on creating dj3 graphs from scratch
        - https://www.youtube.com/watch?v=Oo52vQyAR6w&ab_channel=CrunchyrollDubs
        - https://www.youtube.com/watch?v=aHJCt2adSWA&ab_channel=Academind
        - https://www.youtube.com/watch?v=Obh-1JffGVk&ab_channel=Packt
    - I finished displaying the data through the bar chart and then implemented a hover feature for the graph
    - But after finishing the bar chart I realised again that it was again not the best representation of the data because the bars would overlap and the data appeared so small on the chart that it was almost impossible to see
    - I ended up switch to a pie chart and reached the same point i had reached with the bar chart

- Update 13 https://hackmd.io/W5AOls3UQ06q9GVbolAHEQ
    - I spent a lot of time starting to write my presentation for dev-connect
    - I watched the presentations form last to year to give me a better idea how to write and present my project
    - I completed my Radius Pie Chart Graph and began spending a ton of time on implementing labels that don't hover overlap each other.
    - After show my now completed graph to Piper Merriam he told me that this graph also would not be the best representation of the data and suggested me to display the data through a scatter plot chart
    - The scatter plot chart required me to have to change my original query in order to handle the node_ID instead of handling the client count so i spent some time starting updating my query 

- Update 14 https://hackmd.io/nmxy4ErbQjazRa-L5KaiSQ
    - This week i finished updating my rust sea-query and updated my javascript code for the new graph to be able to handle u256 so i could display the entire node id when I hovered over a point on the graph
    - I then displayed the data through the graph and had the graph fully working
    - I then spent a very large portion of the week refining the graph, implementing a hover feature that displayed the entire node id and the radius, then incremented the node id section by 10 ticks and formatted each tick number to scientific notation instead of a super long number displaying and after quite a few refinements and improvements I finish the graph and created a PR.
    - I then started to begin working on a NavBar
    - The time i was not working on my graph and Navbar i was spending on my presentation

- Update 15
    - Implemented a working navbar that allowed us to easily traverse between each page with ease 
    - After implementing it i spent a large period of time styling it really trying to get it to look nicely with the page and finished the final product of the navbar and after some time it was merged
    - After the scatterplot ended up being reviewed by Piper and Mike there were over 15 changes requested, around 4 big ones with some challenges and around 9 smaller ones. After a days focused on fixing these changes my graph was reviewed and merged

- Update 16 https://hackmd.io/X3kLg83zR6uNcVoPoiuk0Q
    - for the last week of the project i spent most of the week working on and refining my project presentation base on the template JoshD ended up giving us
    - I spent a bit of time on my final update 
    - I also spent a bit of time looking into my next graph implementation as well

## Links And Resources

**Glados Github:**

- https://github.com/ethereum/glados

**Active PR's I'm working on and contributing towards:**

- https://github.com/ethereum/glados/pull/149

- https://github.com/ethereum/glados/pull/150

- https://github.com/ethereum/glados/pull/151

- https://github.com/ethereum/glados/pull/152

- https://github.com/ethereum/glados/pull/156

- https://github.com/ethereum/glados/pull/176

**Merged Pr Links That I've Worked On And Helped Implement:**
- https://github.com/ethereum/glados/pull/137

- https://github.com/ethereum/trin/pull/748

- https://github.com/ethereum/glados/pull/144

- https://github.com/ethereum/glados/pull/145

- https://github.com/ethereum/glados/pull/117

- https://github.com/ethereum/glados/pull/136

- https://github.com/ethereum/glados/pull/165

- https://github.com/ethereum/glados/pull/188

- https://github.com/ethereum/glados/pull/176