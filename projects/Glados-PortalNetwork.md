## Motivation


The problems my project is solving is creating useful ways to monitor and visualise the health of the portal network and improving glados in its entirety in every way I can, either that be by writing tests, improving glados ui, creating graphs, improving run time complexity and improving glados’s navigation. This is very important because it allows for more diversity into who’s able to view and understand the health of the Portal Network especially for user’s but is all helpful for the developers as well. It is also very important because the more ways to be able to visualise the health of the Portal Network and where things are going wrong or failing the better.


## Project description


My proposed solution for my problem is to create useful ways to monitor and visualise the health of the portal network and improve glados in its entirety by creating different graphs, writing tests, Improving navigation, working on dynamically loading everything to improve runtime complexity and improving the ui. Possibly also lower level improvements depending how things progress and time I have left.


## Specification


- Graphs: First find data that I can graph that will give us a better/novel visibility into the networks performance, then find which graph would best suit the information I'm displaying, then figure out how I can pull the data I'm looking to display from the database and display the data on the page through the graph. Some cool ideas for graphs that I might display are 
  - where in the nodes are located something cool for this would be like displaying like a world map with dots on it that displays where in the world those nodes are located
  - the average data radius of nodes on the network
  - estimated total storage within a given network 
  - a pie chart that displays how many nodes are on the network and which clients they are so trin, fluffy, ultralight, and unknown.
  - recently seen nodes


- Tests: When we encounter a problem or error within glados it is sometimes a good idea to write tests to ensure we do not encounter these issues again. I would also write tests to help me find where a problem might be occurring. The test’s I foresee writing the most are rust integration tests to ensure things are working correctly and help prevent these problems from occurring again, but also write rust unit tests to help me find where the code is not working or an error is occurring when I run into a bug. Examples of tests I could write would be
  - Regression tests to make sure when we add new indexes it doesn't break sql inserts/updates
  - Tests to make sure new code doesn't break pages from working
 


- UI: Create a ruff daft using figma of how I would improve the ui run it over with the Portal Network team and if they approve of it begin styling it in my ide.


- Navigation: Implementing features like breadcrumb links and top navigation.

- Dynamic loading: Instead of everything loading all at once, it will load one thing at a time to improve performance and time complexity.


- (If I have extra time) Lower Level Features: This is to be determined on how my progress goes during the fellowship. But would be a bonus depending how my project goes and would be a growth opportunity for me. Some examples of lower level features might be 
  - Rewriting functions to increase parallelization lowering start to finish completion times. This will likely be done in high IO tasks
  - Optimizing the consensus code to more efficiently gather the data we need feed certain graphs and visuals that where originally unplanned and hence not optimized for
  - working on unresolved github issues 


- Data I want to visualize
  - Average node radius's
  - client diversity on the network
  - Estimated total storage available on the network
  - Client location diversity
  - Is the data on the network, are there any holes? And if so what chunks are missing
  - Do nodes evenly cover the potential content space? Or do nodes clump up causing lots of certain information to be stored but other data ends up more rare.


- What does being able to visual the health of the network entail? Being able to visual the health of the network is important because without it, we will only know something is wrong when it is too late. This can entail many things but here are a few examples
  - Being able to quickly view if the clients on the network cover the key space evenly. This is important because it can be warning there is a bug, but other then that it could cause gaps in the network where certain content ranges will just not be stored.
  - Being able to see that nodes are spread out and not all hosted on one data center. If one data center is running half of the nodes on the network, a meer power outage could cause half the network to shutdown, which can potentional be used as a form of censorship.
  - Another reason we want to track an even distribution of the keyspace is it could be a warning of eclipse attacks. An attack where evil nodes mine node_id's close to a target node. This can be for censorship list among other issues.
  - Knowing that client diversity is strong. If one client controls a major of the network a bug can cause preventable outages.


Overall I hope to improve Glados to make it both visual appealing but also highly functional, so we can quickly identify bugs and resolve them to protect the security of the network.
  




## Road Map

- Continuous Work: Through the entire cohort I plan to always be on the lookout for any aesthetic refinements and ui improvements I can make, my main challenge will be implementing interesting graph where tests will be more of side quests, test will come up in the forms of bus I find along the way.
  - Tests: Writing test's for bug's I find along the way
  - UI Improvements: Throughout the entire fellowship I'm going to be looking into any improvements I can add to the UI of glados in every way that I can because the end goal is for glados is for it to look extremely nice/clean and really easy to navigate through and find what you are looking for.

Throughout the entire program I've been attending every weekly meeting on the Portal Network discord server giving my weekly updates there as well on Mondays and Thursdays, I will contining to give my weekly updates in the portal network calls for the rest of the cohort program and hopefully even longer.

- 1st Phase: During First phase of the ethereum fellowship program I already had a strong sense of what I wanted to work on and contribute towards, which ended up being glados. In the first phase I was working on my first contribution towards glados which is a pie chart that displays how many nodes are on the network and which clients they are, I also ended up doing a ton of research into ethereum and the portal network, there's still some more work I need to do before this PR can be merged, but while working on this implementation I ended up learning alot of important skill along the way like
  - parsing certain data I wanted to pull from the database in pier sql 
  - then learning to convert the sql into sea-orm and sea-query
  - templating in data from the database
  - adding graphs to the page and displaying information through them
  


- 2nd Phase: In the second phase I began working really hard on my project proposal and practicing my presenting my presentation, so I can try to give the best presentation possible. In this phase of the fellowship I also began doing a ton of research into kademlia and discv5 as well even more research into ethereum and the portal network to overall really trying to improve my knowledge and ability to view and understand all the data I look at while working on glados. I also styled most pages of glados giving them a more clean and modern look if you view my PR's from my development updates you can view the before and after images.




- 3rd Phase: Going into Phase 3 I'm going to be begin implementing my second graph of the program where I'm going to be displaying the estimated total storage within a given network, during this phase im also going to be add a top navigation/navbar feature and taking the time to learn how routing works in rust to increase the ability to find what your looking for and to improve the overall navigation the site. 




- 4th Phase: In the 4th Phase I plan to start implementing my next graph which will display the average data radius of nodes on the network, considering I have managed to complete the previous graph I was implementing. I will also be adding a breadcrumb link feature in this phase as well.




- 5th Phase: By the end of this phase I will have finished implementing my third graph of the program 




- 6th: (Optional Phase if I have extra time): deep dive into the lower level workings of glados to add new features or optimizations. Examples: Optimizing the census code to feed certain graphs and visuals that where not meant to originally, improving how fast thing’s load like the Content Dashboard which loads fairly slow atm, aesthetic refinements or working on problems under the issue section and overall improving glados as much as I can

While I've articulated my anticipated accomplishments for each phase of the program, the timeline for their completion might very. This is due to the dual nature of my project simultaneously working on the tasks at hand and engaging in a continuous learning process to acquire the skills to be able to implement the contributions I'm working on. Later throughout the program I may find better data to display and graph ideas so my roadmap might end up changing later in the program.

## Possible Challenges


- Some of the possible challenges I believe that I may occur are facing some learning curves along the way which may prevent me from getting PR’s out as fast and temporary halt my learning and progress along the way.




- Working on contributions that when reviewed will be merged and are useful, while trying not to spend all my time on something that in the end might not be implemented




Here are some examples of learning curves I believe I might face along the way, struggling to find data that would benefit if was displayed on the page and maybe struggling to figure out how to implement a certain change.


Something I believe might hold me back is struggling to view and understand certain data. Which is not a problem because this is a learning experience and I will only get better at this by putting in the work and wanting to learn which I do.


## Goal of the project
#### Outline of the tangible goals for this project
- Pages look more modern and readable, from a hello world looking site to a sleek minimalistic design with functionality at its core
- Pages load faster increasing user satisfaction, instead of 8 to 20 second loading times for certain pages today
- The home page instead of being empty is fill with insightful graphs which give quick insights into the performance/health of the network. (Graphs currently planned can be seen in the specification section.)
- Tests are added to prevent bugs from reappearing and to ensure new changes aren't breaking the site whether that is new or old functionality
- Navigation of the website is intuitive and scalable as we add new pages and features, finding the page you want should take only a second

The goals of which graphs and features that will be implemented will evolve as the project continues. This is a natural progression of my research in the field. The more I understand the better insights I will have to make better visualization and optimizations to the codebase. A part of this project is just doing the work and finding out, then re-evaluating from there. So well I do already have a somewhat planned roadmap I am sure I might think of better new idea's. These deviations could happen which just mean a better final result then I could have predicted in this current proposal. 

Of course that goes without saying, but I see this as a great opportunity to grow as an individual, so I am very happy to be given the opportunity although permissionlessly the inclusive structure is really helping me grow. Self improvement and growth being very important goals of the project to me. So thank you for this opportunity. 

## Collaborators


Fellows: KaydenML


Mentors: Mike Ferris


## Resources


- https://github.com/ethereum/glados




- https://github.com/eth-protocol-fellows/cohort-four/blob/master/projects/project-template.md



















