# Blockchain

Refered as Distributed Ledger Technology (DLT)

## What is a blockchain?

> **A blockchain is a special type of database. Transactions are not governed by a single party, but rather the entire transaction history is recorded in a decentralised, > distributed ledger**.

Blockchains offer groundbreaking technology with the potential to change the internet and even the world for many reasons. As we dive deeper into how blockchains work, you will find it increasingly easy to understand exactly why.

## Main Characteristics and Properties of Blockchain 

### (1) Each node contains a complete image of a blockchain’s network

Who can be trusted in a digital space, where everything can easily be copied and most users are anonymous? Blockchain can help to solve this pressing question.

### (2) A blockchain is not updated and validated by a single individual, but by hundreds, thousands, or even millions of community members in regular timeframes.

Instead of one central party such as a company, government or bank, the entire blockchain network agrees on a shared “reality”, i.e. complete history of every transaction that has ever taken place within the network. This agreement is called consensus.

### (3) Because every single transaction that has ever taken place within the network is recorded and permanently stored, it is not possible to change the ledger’s history or send the same transaction twice

This certainty creates mutual trust. In other words, participants of a blockchain network don’t even have to trust each other because no single user can cheat the system as a whole. Blockchain technology is suitable for transactions between parties that need to be verifiable and permanent, such as contracts, ownership of intellectual property, 
identification, and, of course, cryptocurrencies like Bitcoin.

## How do blockchains work?

> To ensure that the network’s transaction history is not manipulated by anyone, the community behind the network has to agree on a common “reality”.
 
In a blockchain, transactions are stored in blocks, with each newly generated block referring to the block before it with a unique identifying number called a “hash.”

These blocks constitute a chain, hence the name “blockchain”. This chain continues on indefinitely. In the case of blockchains such as Bitcoin, trust is based on technological features such as the fact that all blocks can be viewed by the public. No transaction is added to a block without first being verified by a miner - a special type of computer in the network. This way the community ensures that no fraudulent transaction is recorded in a blockchain. Consequently, a blockchain can even be used by parties who don’t necessarily trust each other to do business because they know their transactions are tamper-proof.

# What is a Node in a Blockchain Network?

There are different types, but each of them shares one specific characteristic – you’ll require specific hardware in order to host or simply connect to one.

**Blockchain technology is decentralized by nature** – one of the key properties that made it so appealing to the wide public. It’s based on the principles of a P2P (Peer to Peer) network. In most networks, there are no dedicated servers, not one authority, but a consensus among users. As they’re all crucial to the security and integrity of the network, becoming a member of a certain crypto coin community is not only exciting but also a responsibility.

**Take Bitcoin for example** – you have two types of nodes. **Full nodes ** which store a copy blockchain and thus guarantee the security and correctness of the data on the blockchain by validating data. The second type is a **lightweight node** – each user participating, who needs to connect to a full node in order to synchronize to the current state of the network and be able to participate.

# The Consensus in a Decentralized Network

In the previous section, I mentioned consensus. You might be wondering what that relates to in crypto terms. The rules by which a blockchain network operates and confirms the validity of information written in blocks and/or work performed is termed “consensus”.

As we’ve already covered, cryptocurrencies operate on a decentralized P2P network. As you can imagine, agreeing on something with a large number of people is bound to lead to complications. This is where consensus algorithms come into play. The most common ones are Proof of Work (PoW) and Proof of Stake (PoS). The differences between the two, I’ll cover later down below. No matter which one has been chosen for a coin, they both have a crucial factor in common – reliance on full nodes for enforcing of rules and validation of transactions. While consensus must be achieved by a certain type of nodes, the beauty of a P2P network is that anyone can become a full node and thus achieve higher levels of independence and decentralization.

In the Bitcoin example – users are free to download the whole blockchain and validate blocks, thus increasing security, as more and more copies of the ledger are created and used for reference. The prime cryptocurrency offers one of the highest levels of decentralization, compared to EOS for example, where becoming a validator needs to be voted by a set number of users and the available positions are limited. This opens the network to corruption and manipulation.

The most common threat to a blockchain is the 51% attack, where more than half the network “power” is concentrated in one entity (be that a single person or collaboration between users). That allows said entity to change consensus rules as it sees fit, which could lead to a monopoly where everyone is either forced to continue with the new rules, hard fork (explained below) or abandon a project. While strict enforcement is a given during the day to day operation of the blockchain, for evolving the network, alterations need be voted on by the community and thus achieve long-term success.

## Types of Blockchain Nodes

In a nutshell, there are two main types of nodes – full nodes and light nodes. Another term to describe nodes is clients which supply wallet functions. Full ones contain а copy of the blockchain’s history, including all blocks created. Light nodes or SPV (Simple Payment Verification) nodes are all wallets that download only the headers of blocks and save hard drive space for users. Let us explore the different sub-kinds in detail.

![bitcoin nodes](https://github.com/aridiosilva/Blockchain/blob/main/Types%20of%20Nodes%20in%20a%20Blockchain%20Network.jpg)


### Full Nodes

Full nodes act as a server in a decentralized network. Their main tasks include maintaining the consensus between other nodes and verification of transactions. They also store a copy of the blockchain, thus being more secure and enable custom functions such as instant send and private transactions.

When making decisions for the future of a network, full nodes are the ones that vote on proposals. If more than 51% of them don’t agree with the proposition, it gets skipped. In some cases, this can lead to a hard fork in which the community cannot agree on a certain change and thus go their separate ways, creating two chains. The most well-known example of that happening is the Bitcoin Cash Fork.

### Pruned Full Node

One type is the pruned full node. The specific characteristic here is that it begins downloading blocks from the beginning and once it reaches the set limit, deletes the oldest ones, retaining only their headers and chain placement. For example, if you set a size limit of 550MB, you will store all the latest blocks that can fit in that hard drive space, but in order to get to that state, you would first have to go through the entire blockchain to validate all those previous blocks.

Pruned nodes are considered full nodes and thus can also verify transactions and be involved in the consensus.

### Archival Full Node

Archival full nodes are what most people refer to when talking about full nodes. They envision a server which hosts the full blockchain in its database. As I already shared with you above, their main task is to maintain consensus and validate blocks. The difference between pruned and archival node is one – the amount of hard drive space they take up on your server or PC.

Archival nodes can be divided into a couple of subtypes – those that can add blocks to the blockchain and ones that are unable too.

### Nodes Which Can Add Blocks

Let us begin by covering the main participants in the blockchain – nodes which can add blocks to it. They depend on the consensus rules being enforced and require at least one full archival node to operate.

* Miners (Mining Nodes)
* Stakers (Staking Nodes)
* Authority Nodes

### Masternodes

Compared to full nodes, masternodes themselves cannot add blocks to the blockchain. Their only purpose is to keep a record of transactions and validate them. Whether it will be miners or stakers, they’re the ones writing blocks on the blockchain. An added benefit, however, is that by running a masternode, you not only secure the network but can earn a share of the rewards for your services.

To establish a masternode, you will need to lock away a certain sum of funds as collateral. You are expected to be online 24/7 and hosting on a Virtual Private Server is considered good practice. If you’d like to learn more on how to set up your own masternode or which the best masternode coins are, you can check out masternodes.com;

### 
Lightweight (SPV) Nodes

Another type of blockchain nodes, used in day to day crypto operations, is the lightweight node or Simple Payment Verification (SPV) node. You’ve probably come across it already, but you’re most likely familiar with the “light wallet” definition.
These types of nodes communicate with the blockchain while relying on full nodes to provide them with the necessary information. As they don’t store a copy of the chain, they only query the current status for which block is last, and broadcast transactions for processing.

Having in mind the above features, it’s clear to see that running SPV node doesn’t require many resources, but it does sacrifice security for the sake of convenience.

### Lightning Nodes

Lightning nodes are a very interesting concept. They fit into the constraints of neither full nodes nor lightweight nodes as I’ve presented them to you so far.

The idea behind them is to establish a connection between users outside the blockchain. This way, the load on the network is reduced, transfer times are shortened significantly and there’s increased usability of crypto coins. Transaction fees are really low in the lightning network – the equivalent of roughly 10 to 20 satoshi in general.

The way it works is by opening a separate payment channel between entities. Take for example a bagel shop and Bob. Bob and the shop create something like a safe-deposit box (a multi-signature address) to which they both have separate keys. Bob deposits his funds and uses them to pay for bagels. Each transaction is agreed upon by both sides and happens pretty much instantly. Once he’s had enough bagels or simply runs out of money, he or the shop can close the connection, take the latest balance sheet and broadcast it onto the network.

This way, instead of waiting for each transaction to be confirmed and filling the network with space-wasting data, parties can interact between each other and lower the load on the blockchain. Furthermore, if someone else wants to deal with the same party, the lightning network will search for a path with the least number of intermediaries and lowest transfer fees, thus reducing wait times.

This way, instead of waiting for each transaction to be confirmed and filling the network with space-wasting data, parties can interact between each other and lower the load on the blockchain. Furthermore, if someone else wants to deal with the same party, the lightning network will search for a path with the least number of intermediaries and lowest transfer fees, thus reducing wait times.

![ln nodes](https://github.com/aridiosilva/Blockchain/blob/main/lightning-nodes-mobile.svg)

### What Happens to a Node After a Fork?

Now that I’ve covered the different types of cryptocurrency nodes and you’re familiar with their operation, let’s explore how that ties into the network consensus and eventual forks.

In previous paragraphs, I mentioned that if there’s not at least a 51% agreement between full nodes, a proposed change to the network is rejected. But what happens if there’s a large part of the community that still wants to accept the suggested alteration? That is where forks come into play. A developer decides to create a new client, using the source code of the coin and implements the proposed change. Users willing to go on in that direction, download the new version and decide to support the now forked chain.

### Hard Fork

In short, a hard fork is a change to the network consensus algorithm. Every alteration that is not compatible with the previous version of the client used, is considered a hard fork. Parameters of the consensus that can provoke a hard fork when changed, may include a new block reward, block time, transition from PoW to PoS, implementation of masternodes and others.

Once a hard fork is launched, every node on the network that hasn’t updated to the new version of the software is rejected by the consensus as for its operating on invalid rules. That is one of the reasons why developers and communities generally avoid major changes, as it means some people will be left out or the transition phase may compromise the security of a network.

![hard-fork-mobile](https://github.com/aridiosilva/Blockchain/blob/main/hard-fork-mobile.svg)

### Soft Fork

Another way of introducing changes to a network is via a soft fork. Contrary to hard forks, with this type of alteration, there’s no mandatory rule for users to update their nodes.

One such example is the addition of the Segregated Witness feature to Bitcoin. To this day, transactions can be made on BTC’s blockchain with or without using this feature. Once 95% of clients on the network are updated to the version that supports SegWit, the consensus will automatically change and refuse any old transactions without it. This way, we have a smoother transition that does not force users to immediately update.

![Soft Fork](https://github.com/aridiosilva/Blockchain/blob/main/soft-fork-mobile.svg)

### Virtual Private Servers (VPS) and Their Usage with Nodes

Whether or not you decide to use a Virtual Private Server is up to personal preference. If you decide to run a masternode, lightning node or even a cold staking node, a VPS will be beneficial as you pay a small fee in return for protection from DDoS attacks, not having to maintain any hardware and not worry about your bandwidth capabilities.

On the other hand, if you don’t take enough security precautions, you risk someone hacking into your server and stealing your funds, provided you’re storing your coins in those wallets. These are the basics, but I’d recommend researching VPS servers in detail before deciding on whether or not to rent one. 

## FAQ

### Why should I host a Full Node?

If you’re eager to support the network of a given coin or simply don’t want to rely on other full nodes for your information, you can host your own and store a copy of the blockchain. It’s more secure, however, it will take longer to set up.
   
### Is a Masternode better than a Full Node?

Masternodes and full nodes are similar in their function as discussed in the article. If your goal is to make a profit, then running a masternode would be the way to go.
    
### Can I make a Profit hosting a Blockchain Node?

Yes, but it depends on which type you decide to host. With masternodes, you will be paid for your services, but you have to consider the initial investment that you’ve locked into the masternode itself. Another option would be a staking node, it will offer you passive income which will increase as you invest more in it.
    
### How many Nodes can I run on a single Machine?

Depends on your hardware capabilities. Only one instance of a wallet may be run at the same time, so you’ll need to make use of Virtual Machines. If you decide to use a VPS, you need to make sure that you’re not using more than 80 to 85 percent of available resources, as you may be taken down, limited or some other measures may be employed by the provider.
    
### Which are the best VPS Providers?

The choice is entirely yours, however, based on my own experience and market research, some of the top suppliers include Amazon EC2, DigitalOcean Droplets, Vultr, and Microsoft Azure





