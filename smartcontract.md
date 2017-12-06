# Introduction to Smart Contracts

Now we get into the exciting stuff. All of the things we have seen Dragonchain do before have been things that are old hat to any user of a database backed web service.

When I was a youngster I read Snow Crash by Neal Stephenson, and his vivid descriptions of cyberspace and how it interacted with the physical world lit a fire in my imagination. His Hiro Protagonist, uses computers to spin up companies and manipulate the legal and physical world in intersting ways. I feel that Blockchain technology + Smart Contracts is the first step toward bringing those imaginings of Stephenson into our world.

So what is a Smart Contract? A smart contract is a computer program that runs on the data in a blockchain. As you might remember, data on a blockchain has been agreed to be real from either from a Proof-of-Work concensus, or a Proof-of-Stake concensus. And a Smart Contract has the ability to take that data, and perform actions based on the agreed true data. And because the program is published on the blockchain and is crypotographically signed... No one can alter it, without all of the parties involved being able to see the modification.

Lets get cracking on writing our first Dragonchain smart contract.

## Getting Started
The Dragonchain team is working on multi-lingual smart contracts, aka Smart Contracts that you can write in a wide variety of supported languages such as Javascript or C#,  The current public version on github only supports python so that is what we are going to use for this blog post.

There are several different types of Dragonchain smart contracts, but the most basic, is a Transaction Smart Contract (TSC). A TSC smart contract runs when a transaction is submitted to a L1 nodes such as the one we have setup in the previous demos.

To get started we are going to say we have a business rule that we don't allow more than 100 Dragons to be traded in any group of transactions. To implement this we are going to write a simple Transaction Smart Contract.

````
def func(self, txn):
    strJson = json.dumps(txn)
    txnStructure = json.loads(strJson)
    txnPayload = txnStructure['payload']['Transactions']

    totalDragonsCount = 0
    for x in  range(len(txnPayload)):
        totalDragonsCount = totalDragonsCount + int(txnPayload[x]['numberOfDragons'])
        if totalDragonsCount > 100:
            return False  
    return True
````

So to get started we are package up this new TSC and get it running on Dragonchain when a Transaction of the type DragonSwap happens.















## More to come
