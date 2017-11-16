#Introduction to Dragonchain

Dragonchain is an exciting new open-source blockchain. The code exists on [github](https://github.com/dragonchain/dragonchain), and it provides an amazing toolkit for building your own blockchain based on your needs.

The Dragonchain project was originally developed at the Seattle Office of the Walt Disney Company, and it was open sourced [link](https://disney.github.io). The Dragonchain Foundation [link](https://dragonchain.github.io) manages the open source project. A company called Dragonchain [link](http://dragonchain.com) did an ICO in the winter of 2017, to fund further development of the project. 

#Dragonchain Goals 
Dragonchain was developed to handle the needs of organizations and developers. Which has caused it to diverge from the orthodoxy that that has driven many of the decisions that exist in both Bitcoin and Ethereum. That said, it elegantly inter-ops with the public blockchains when that integration is desired. 

Dragonchain was developed to meet business needs and goals. Which lead to four design decisions that are a bit different than the usual with Blockchain based applications. First is the ability to build hybrid proof of stake /proof of work systems. Second is the strong integration with web based systems. Protection of business data. And lastly fixed blocks based on time. I'm going to briefly go into each one of those design decisions and explain what that means to a developer. 

##Hybrid proof of stake/proof of work
A typical blockchain is best thought of as a one dimensional stack of blocks that have back-links to previous blocks. As time progresses, new blocks are formed. For each block swarms of computers perform analysis to determine if the transactions submitted are "true". 

The use of large numbers of computers to determine "truth" is a fundamental requirement in a network of nodes, that has bad actors in it. Bitcoin and Ethereum require proof of work [link](https://en.wikipedia.org/wiki/Proof-of-work_system) to discourage bad actors.    

One of the downsides of the common poof of work algorithms is that they use a lot of resources. A single Bitcoin transaction uses about the same amount of power as an American household uses in a week. [link](https://motherboard.vice.com/en_us/article/ywbbpm/bitcoin-mining-electricity-consumption-ethereum-energy-climate-change)

Dragonchain is a bit different, as it came from an huge hybrid organization that has many large billion dollar plus companies as parts of it. Dragonchain was designed with an assumption that you *might* want trust certain organizations and their computers. A company that you are working with will have a *stake* in making sure its transactions with you are valid, and you can trust them. 

Combining the insight that you might want to trust certain computers/organizations, and that the standard Proof-of-Work systems waste a lot of resources led to Dragonchain's hybrid design. 

With Dragonchain, you can push the one dimensional series of blocks into stacks of blocks. You can setup the level of trust you have in transactions at each level, and later if you so choose, you can then push the transaction out to the public chains. 

For more information on how Dragonchain lets you build multi-dimensional blockchains look at the architecture diagram. [link](https://dragonchain.github.io/architecture#verification-and-consensus)

##Integration with web based systems
Dragonchain is different than Bitcoin and Ethereum, it leverages your existing knowledge of web development. Your programming interface to Dragonchain is HTTP (web) calls with JSON payloads. In the later post we will go through posting and querying transactions with CURL and WGET. 

Dragonchain leverages the micro services paradigm that has become a major trend in the software in the last few years and makes integration with your existing application infrastructure. It is easy to deploy via Docker and Kuberneties. (TODO URL) 

Bitcoin and Ethereum are at their core, binary protocols with embedded virtual machines that run apps inside wallets and servers. They are closer in nature to the early days ofJava and its Virtual Machine, where the majority of development was done via binary RPC (remote procedure calls). While there are web gateway interfaces, they are in many cases second class citizens to the binary interfaces. 

##Protection of business data
An advantage that Dragonchain has is that is allows you to build private chains, and connect and send the data from those private chains to a public chain if you so choose. This allows you to build mixed blockchains and allows you to have control of your data, and when and how it reaches the public. 

Other blockchain projects, by default publish all of the data to the public networks, where anyone with a blockexplorer program can investigate and see all of your data. 

##Fixed time based blocks
Default out of the box, Dragonchain is configured with a short interval, 5 second block (aka chunk of transactions). You can configure this for different settings if you so choose. 

Ok, enough introduction, lets write some code. 
First lets download and install Dragonchain (link)[???]






