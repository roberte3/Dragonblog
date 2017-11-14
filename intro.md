#Introduction to Dragonchain

Dragonchain is an exciting new open-source blockchain. The code exists on [github](https://github.com/dragonchain/dragonchain), and it provides an amazing toolkit for building your own blockchain based on your needs.

The Dragonchain project was originally developed at the Seattle Office of the Walt Disney Company, and it was open sourced [link](https://disney.github.io). The Dragonchain Foundation [link](https://dragonchain.github.io) manages the open source project. A company called Dragonchain [link](http://dragonchain.com) did an ICO in the winter of 2017, to fund further development of the project. 

#Dragonchain Goals 
Dragonchain was developed to handle the needs of organizations and developers. Which has caused it to diverge from the orthodoxy that that has driven many of the decisions that exist in both Bitcoin and Etherum. That said, it elegantly inter-ops with the public blockchains when that integration is desired. 

Dragonchain was developed to meet business needs and goals. Which lead to four design decisions that are a bit different than the usual with Blockchain based applications. First is the ability to build hybrid proof of stake /proof of work systems. Second is the strong integration with web based systems. Protection of business data. And lastly fixed blocks based on time. I'm going to briefly go into each one of those design decisions and explain what that means to a developer. 

##Hybrid proof of stake/proof of work
A typical blockchain is best thought of as a one dimensional stack of blocks that have back-links to previous blocks. As time progresses, new blocks are formed. For each block swarms of computers perform analysis to determine if the transactions submitted are "true". 

The use of large numbers of computers to determine "truth" is a fundamental requirement in a network of nodes, that has bad actors in it. Bitcoin and Etherium require proof of work [link](https://en.wikipedia.org/wiki/Proof-of-work_system) to discourage bad actors.    

One of the downsides of the common poof of work algorithms is that they use a lot of resources. A single Bitcoin transaction uses about the same amount of power as an American household uses in a week. [link](https://motherboard.vice.com/en_us/article/ywbbpm/bitcoin-mining-electricity-consumption-ethereum-energy-climate-change)

Dragonchain is a bit different, as it came from an huge hybrid organization that has many large billion dollar plus companies as parts of it. Dragonchain was designed with an assumption that you *might* want trust certain organizations and their computers. A company that you are working with will have a *stake* in making sure its transactions with you are valid, and you can trust them. 

Combining the insight that you might want to trust certain computers/organizations, and that the standard Proof-of-Work systems waste a lot of resources led to Dragonchain's hybrid design. 

With Dragonchain, you can push the one dimensional series of blocks into stacks of blocks. You can setup the level of trust you have in transactions at each level, and later if you so choose, you can then push the transaction out to the public chains. 

For more information on how dragonchain lets you build multi-dimensional blockchains look at the architechture diagram. [link](https://dragonchain.github.io/architecture#verification-and-consensus)

##Integration with web based systems


##Protection of business data 

##Fixed time based blocks





