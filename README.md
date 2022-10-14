

# Blockchain Technology

Blockchain is a distributed ledger—write once and never erase. Although originally invented for financial transactions,1 its applications are broad. Refered as Distributed Ledger Technology (DLT)  makes the history of any digital asset unalterable and transparent through the use of descentralization and cryptographic hashing.

![what is exactly a blockchain network](https://github.com/aridiosilva/Blockchain/blob/main/Figure%20Blockchain%20Network_001.jpg)

- [Hyperledger Whitepaper](https://github.com/aridiosilva/Blockchain/blob/main/Whitepaper%20-%20Hyperledger.pdf)
- [Whitepaper - Bitcoin A Peer-to-Peer Electronic Cash System - Satoshi Nakamoto ](https://github.com/aridiosilva/Blockchain/blob/main/Whitepaper%20-%20Bitcoin%20A%20Peer-to-Peer%20Electronic%20Cash%20System%20%20-%20Satoshi%20Nakamoto%20%20%209%20pages%202008.pdf)
- [Whitepaper - Practical Byzantine Fault Tolerance - Miguel Castro and Barbara Liskov](https://github.com/aridiosilva/Blockchain/blob/main/Whitepaper%20-%20%20Practical%20Byzantine%20Fault%20Tolerance%20-%20Miguel%20Castro%20and%20Barbara%20Liskov.pdf)

- [Blockchan simply explained in this video](https://www.youtube.com/watch?v=SSo_EIwHSd4)

# Architecture of Blockchain System

![architecture](https://github.com/aridiosilva/Blockchain/blob/main/Figure%20-%20Architecture%20of%20Blockchian%20System%20-%20The%20Layers.jpg)

# Distributed Ledger Tecnologies

![distributed ledger technologies](https://github.com/aridiosilva/Blockchain/blob/main/Figure%20Illustrative%20Distributed%20Ledger%20Technologies%20(source%20KPMG)%20001.jpg)

The difference among centralized (client/server), discentralized, and distributed network toplogies is shown in the iamge below

![Figure Network Architectures and Blockchain 001](https://github.com/aridiosilva/Blockchain/blob/main/Figure%20Network%20Architectures%20and%20Blockchain%20001.jpg)

# Main Elements of Blochchain

![main elements](https://github.com/aridiosilva/Blockchain/blob/main/Main%20Elements%20of%20blockchain.jpg)

# Mining Difficulty in Blokchain

## What is Mining Difficulty?

> - The difficulty is a measure of how difficult it is to mine a Bitcoin block, or in more technical terms, to find a hash below a given target. 
> - A high difficulty means that it will take more computing power to mine the same number of blocks, making the network more secure against attacks. 
> - The difficulty adjustment is directly related to the total estimated mining power estimated in the Total Hash Rate (TH/s) chart.
> - The difficulty is adjusted every 2016 blocks (every 2 weeks approximately) so that the average time between each block remains 10 minutes. The difficulty comes directly from the confirmed blocks data in the Bitcoin network.

- [Link to see the Network Difficulty chart of Bitcoin](https://www.blockchain.com/charts/difficulty)
- [link to see the Hash Rate chart of Bitcoin](https://www.blockchain.com/charts/hash-rate)

## What Determines Mining Difficulty?

### To Maintain Network Integrity

The level of Bitcoin mining difficulty increases or decreases according to the ease of mining within the protocol. Remember, Bitcoin needs to have a consistent block time of 10 minutes. In other words, new BTC can be injected into the circulating supply every 10 minutes. To make sure that this timing doesn’t change the Bitcoin protocol:

> - **Increases network difficulty** when it becomes easier for miners to mine.
> - **Decrease network difficulty** when it becomes harder for miners to mine.

The Bitcoin network has a universal block difficulty. All valid blocks must have a hash below the target. Mining pools also have a pool-specific share difficulty setting a lower limit for shares.

### Relationship with the Hash Rate

One of the critical metrics in judging the health of a proof-of-work network is hash rate. Simply put, hashrate shows you how powerful the miners are within the network. Higher the bitcoin network hashrate, higher it’s overall security and speed. However, these networks need to keep their hashrate under control for consistent block production. This is why, when hashrate becomes high, the bitcoin difficulty eventually gets higher as well, making it tougher for miners to mine easily within the network.

The inverse is also true. If Bitcoin’s hashrate decreases, the network difficulty will reduce as well. Hashrate may decrease because of the following reasons:

> - Bitcoin currently has a high difficulty, which is why the miners are having a tough time mining in the system.
> - The price of BTC went down, which is why a lot of miners quit mining.

To understand the correlation between the two, let’s check out their graphs. Up first, we have the hash rate. After that, we have the bitcoin difficulty chart:

![Image_total_hash_rate_blockchain_chart001](https://github.com/aridiosilva/Blockchain/blob/main/Image_total_hash_rate_blockchain_chart001.jpg)

- [take a look at the currenty  Hash Rate chart of Bitcoin](https://www.blockchain.com/charts/hash-rate)

Mining hashrate is a key security metric. The more hashing (computing) power in the network, the greater its security and its overall resistance to attack. Although Bitcoin’s exact hashing power is unknown, it is possible to estimate it from the number of blocks being mined and the current block difficulty. Daily numbers (raw values) may periodically rise or drop as a result of the randomness of block discovery : even with a hashing power constant, the number of blocks mined can vary in day. Our analysts have found that looking at a 7 day average is a better representation of the underlying power. The hashing power is estimated from the number of blocks being mined in the last 24h and the current block difficulty. More specifically, given the average time T between mined blocks and a difficulty D, the estimated hash rate per second H is given by the formula H = 2 32 D / T.

![Image_network_difficulty_blockchain_chart001](https://github.com/aridiosilva/Blockchain/blob/main/Image_network_difficulty_blockchain_chart001.jpg)

- [take a look at the currenty Network Difficulty chart of Bitcoin](https://www.blockchain.com/charts/difficulty)

As you can see, there is a very close correlation between the two. Around March 26, the network difficulty fell by 16% from 16.55 trillion to 13.9 trillion. This was the largest crash in network difficulty since early 2013. To understand why this happened this time around, look at how the hashrate dropped as well just before the bitcoin difficulty drop. This dip occurred because of Bitcoin’s price crash, which forced a lot of miners to quit operations.

### How does Bitcoin calculate difficulty?

Bitcoin’s network difficulty changes every 2016 blocks. The formula used by the network to calculate difficulty goes like this:

      difficulty = difficulty target / current target

In the formula above:

> - currente target is a 256-bit number. As per Bitcoin’s protocol, the targets are a custom floating-point type with limited accuracy. Bitcoin clients approximate difficulty based on this fact. This value is also known as bdiff.
> - difficulty target can be different depending on how you choose to measure difficulty. Traditionally, it represents a hash where the leading 32 bits are zero and the rest are one. In fact, this value is also known as pool difficulty or pdiff.

Every single block stores a packed representation of bitcoin difficulty in their blocks called “Bits.” This target usually appear as 0x1b0404cb (stored in little-endian order: cb 04 04 1b).

A block calculates the target value via a predetermined formula. Eg. With the packed target given above, i.e. 0x1b0404cb. The hexadecimal target is:

      0x0404cb * 2**(8*(0x1b – 3)) = 0x00000000000404CB000000000000000000000000000000000000000000000000

Now let’s calculate bdiff and pdiff.

The highest possible target (difficulty_1_target) is defined as 0x1d00ffff or, in hex form:

      0x00ffff * 2**(8*(0x1d – 3)) = 0x00000000FFFF0000000000000000000000000000000000000000000000000000

Now that we know this value, we can use this to calculate our bdiff using the 

      difficulty = difficulty_1_target / current_target formula

Now, as we have defined in the previous section, the current_target is 

    0x1b0404cb or 0x00000000000404CB000000000000000000000000000000000000000000000000.

So, to calculate current difficulty:

    0x00000000FFFF0000000000000000000000000000000000000000000000000000 /
    0x00000000000404CB000000000000000000000000000000000000000000000000
    = 16307.420938523983

Hence, bdiff is 16307.420938523983.

Now, let’s calculate the pdiff. Mining pools tend to use non-truncated targets which puts difficulty_1_target at 
  
     0x00000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF.

If that’s the case then for the same current_target, our pdiff will be:

    0x00000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF /
    0x00000000000404CB000000000000000000000000000000000000000000000000
    = 16307.669773817162

Here is a program code taken from Bitcoin wiki which relies on logs to make difficulty calculation easier:

```c++
#include <iostream>
#include <cmath>
inline float fast_log(float val)
{
   int * const exp_ptr = reinterpret_cast <int *>(&val);
   int x = *exp_ptr;
 
   const int log_2 = ((x >> 23) & 255) – 128;
   x &= ~(255 << 23);
   x += 127 << 23;
   *exp_ptr = x;
   val = ((-1.0f/3) * val + 2) * val – 2.0f/3;
   return ((val + log_2) * 0.69314718f);
}
float difficulty(unsigned int bits)
{
   static double max_body = fast_log(0x00ffff), scaland = fast_log(256);
   return exp(max_body – fast_log(bits & 0x00ffffff) + scaland * (0x1d – ((bits & 0xff000000) >> 24)));
}
int main()
{
   std::cout << difficulty(0x1b0404cb) << std::endl;
   return 0;
}
```

## How do you set a mining difficulty?

Miners use specialized ASIC hardware to mine Bitcoins. These machines are extremely fast and produce tetrahashes every single second. It will be extremely impractical for a system to painstakingly check every single one of them to see if they satisfy all the necessary conditions, or not. This is exponentially true for mining pools. They can’t check all the hashes produced by a bitcoin miner every single second. This is why mining pools use a concept called “Share Time.”

So, let’s imagine that your bitcoin mining pool has set a Share Time of 5 seconds. This means that, on average, your mining pool will require miners to submit a share to them every 5 seconds.

### How exactly is this done?

Your bitcoin mining pool will set a value called Share Difficulty for every miner. The share difficulty of a miner is directly proportional to their individual hashrate. As such, higher the miner’s hashrate, higher their Share Difficulty. The idea is that the miner will use their equipment to generate tons of hashes. The moment they find a hash that meets the target Share Difficulty, they will send the hash to the pool.

### How are the miners rewarded?

Miners in the pool are rewarded on a “Pay per share” (PPS) basis. In this system, the miners get rewarded for the shares they submit. The values of the shares are entirely dependent on how difficult it was to discover the share.

Let’s take an example to see how this works:

> 1) Suppose you are a miner with an individual hashrate of 50 TH/s.
> 1) The mining pool that you have joined has set your Share Difficulty at 1,000,000.
> 1) The moment that you get shares above 1,000,000, you’ll be rewarded by the pool.
> 1) The pool may change your difficulty to make sure that you are not submitting your shares too quickly.
> 1) Now, if you buy some new equipment and increase your hashrate to 150 TH/s, the pool will increase your difficulty to 3,000,000. You will be submitting shares at the same rate that you were previously submitting. However, you’ll get 3 times the reward that you were previously receiving for the shares you submit.
> 1) The reason why pools recommend higher difficulties for faster hardware is to reduce network load on both the miner’s system and the pool. It also reduces decreases the restart delay for your mining hardware as it prepares for the next work unit. At the same time, the pool must be careful not to set the difficulty too high which will result in a lot of stale shares.

       NOTE: Share Target = 1 / Share Difficulty

### The Importance of Difficulty in Nakamoto consensus

To understand how critical difficulty is to Bitcoin’s ecosystem, you need to know how Nakamoto consensus works. For a wide area network with no centralized entity, consensus protocols are the only way to maintain any form of governance. Traditional consensus algorithms like Raft are not ideal for maintaining a wide-area cryptoeconomic protocol. This is why Satoshi Nakamoto, the creator of Bitcoin, came up with Nakamoto consensus. The central tenet of the Nakamoto consensus is that to participate in the system, one must pay a price. In the case of proof-of-work (POW), i.e., Bitcoin’s consensus, miners pay a price with “work.” Work, in this case, is the heavy amount of computational energy that a miner must spend to mine one Bitcoin. This is where difficulty comes in.  Difficulty is the metric that makes Bitcoin mining hard, plus, this is what Nakamoto consensus leverages to solve the double spending problem.

### What is double spending?

Double spending is the reason why all the attempts at creating a decentralized cryptocurrency had failed miserably before Bitcoin. In simple terms, it is a flaw that can allow one Bitcoin to be spent more than once at the same time. We never encountered this issue while dealing with physical cash. After all, if you are buying something with a $10 note, you can’t simultaneously purchase something else with that same note, right?

However, a digital token has digital files that can be easily duplicated, leading to inevitable double spending. As you can imagine, double spending can have several devastating effects on the ecosystem’s economy:

> - Firstly, it inflates the total supply of the coins within the ecosystem, which throws the supply-demand equation out of control.
> - Secondly, if anyone, anywhere can spend the same coin without restriction, it will reduce the people’s faith in the sanctity of that currency.

Bitcoin requires all the transactions to be included in the blockchain, without fail. This makes sure that anyone in the network can trace every single Bitcoin right to its very source. Such a high level of transparency ensures no one will be able to double spend without the entire network noticing. However, let’s think of something more diabolical. Suppose, someone decides to hijack the blockchain by forking out and try to double spend all the Bitcoins.

### What happens then?

Well, it turns out that due to network difficulty, the amount of resources and money that the attacker will need to take over the chain will be exponential. As such, it will simply not be economically worth it for them to act against the interests of the system. This is how network difficulty gives Nakamoto Consensus the firepower it needs to maintain network security and integrity.

# Blockchain Structure

To reduce storage, if a block B is “voted” to be correct because the chain is long enough (ie, there are already many blocks created after B), we can discard the transactions contained in B, without changing the hash of B’s header (otherwise all blocks after B would need to be changed). To do this, instead of saving the content of all transactions directly in a block, we first compute the hash values of each transaction, and then construct a tree structure (a Merkle tree), to “combine” (ie, hash again) all hash values, and store only the Merkle Root hash value at the block header. This way we can prune the transactions in the tree later, without changing the Merkle Root and the block header. In other words, the size of the blockchain is now proportional to the number of blocks instead of being proportional to the number of transactions. Belowe an example blockchain without a Merkle tree. 

![blockchain withou a merlkle tree](https://github.com/aridiosilva/Blockchain/blob/main/Figure%20BlockChain%20Without%20Markle%20Tree%20001.jpg)

The blocks enclose transactions without adopting a Merkle tree. As a result, the size of a block will grow proportionally to the number of transactions (eg, transaction T12) that are enclosed. Below a blockchain with a Merkle tree. 

![Blockchain with a Merkle tree](https://github.com/aridiosilva/Blockchain/blob/main/Blockchain_and_Merkle_Tree_figure001.jpg)

A Merkle tree is constructed by hashing paired data (the leaves) to create a parent node iteratively, until a single hash, the Merkle Root,1 remains. In this example, the transactions (eg, T12) are first encoded into a binary raw-transaction format and then hashed to create the hashes (eg, Hash of T12). Then, hashes such as the Hash of T12 are paired with other hashes such as the Hash of T11 (if a hash does not have a pair, it simply duplicates itself to be paired) to compute the hash as their parent node (ie, Hash of T11–12). The pairing/hashing process repeats until only 1 hash (the Merkle Root) remains, and the Merkle tree construction process is then completed. Finally, by only enclosing the Merkle Root in each block header, the storage space required to verify the integrity/validity of transactions can be reduced. That is, if an attacker tries to change the content of any transaction such as T12, all of the related hashes (ie, Hash of T12, Hash of T11–12, and Hash of T11–14), and eventually the Merkle Root (ie, Hash of T11–18) will also change and can be easily verified. To enclose this new Merkle Root to pass the verification process, the attacker then needs to re-create block B1 and all blocks thereafter, which is computationally expensive and is enough to prevent such modification. A Merkle tree is the basis of lightweight nodes described in Figure below (ie, the blockchain nodes that only need to verify transactions can store parts of the Merkle trees to save space, while the full blockchain nodes that need to “mine” new blocks store all of the Merkle trees).

![another approach Merkle tree](https://github.com/aridiosilva/Blockchain/blob/main/Blockchain_and_Merkle_Tree_figure002_reduced.jpg)


Another technique to reduce the need for each user to keep the full history of transactions is to use lightweight nodes together with a Merkle tree. For a user who only wants to use coins but does not want to “mine” new blocks, the full transaction history (more than 150 GB as of January 2018) is too large, especially for smartphones. Therefore, a user can adopt lightweight nodes so that only the Merkle Branch that links the transactions that the user would like to verify is used. An example of the Merkle Branch for transaction T12 stored on a blockchain lightweight node (eg, on a mobile device), in contrast to the data storage of a full node (eg, on a personal computer), is shown in this figure above. With the use of the Merkle tree, a lightweight node only stores data relevant to specific transactions (eg, T12) to save space. For example, in addition to T12 itself, this lightweight node only needs to store related hashes (ie, Hash of T11, Hash of T13–14, and Hash of T15–18), instead of storing the full Merkle tree, to make sure T12 is linked to block B1. That is, one can first compute the Hash of T12 using T12, and then compute the Hash of T11–12 using the Hash of T11 and the Hash of T12. Eventually, one can compute the value of the Merkle Root (Hash of T11–18), and compare it with the one stored in B1, to make sure T12 has been verified in B1. This way, a lot of required storage space for those lightweight nodes is saved, making applications such as wallet apps on mobile devices feasible. This verifying process is also known as Simplified Payment Verification. As a result, users/nodes can be divided into 2 groups: full nodes (the ones storing the whole transaction history and performing mining) and lightweight nodes (ie, the nodes using Simplified Payment Verification just for transactions, without mining), thus reducing the storage space for lightweight nodes and improving the scalability of a blockchain network.

# Features of Blockchain Plaforms -  Main Options and Implications

## F1 - Network Permission

> - **Permissionless network**: A public blockchain network configuration designed to allow public participation;
> - **Permissioned network**  : A private blockchain network configuration that includes only authorized participants;

## F2 - Consensus Protocols

![](https://github.com/aridiosilva/Blockchain/blob/main/Figure%20Blockchain-Consensus-Algorithms-that-are-Popular-in-the-Market%20001.png)

Consensus Mechanism is a method of autenticating and validating a value or transaction on a Blockchain or a Dsitributer Ledge without the need to trust or rely on a central authority. Consensus mechanisms are central to the functioning of any blockchain or distributer ledger.

![Figure Consensus Mechanisms Time Line Eovolution 001](https://github.com/aridiosilva/Blockchain/blob/main/Figure%20Consensus%20Mechanisms%20Time%20Line%20Eovolution%20001.jpg)

![part 2](https://github.com/aridiosilva/Blockchain/blob/main/Figure%20Consensus%20Mechanisms%20Time%20Line%20Eovolution%20001-part2.jpg)

### How Concensus Mechanisms work

Basic parameters that define a consensus mechanism are:

-	**Decentralized Governance** – A single central authority cannot provide transaction finality
-	**Quorum Structure** – Nodes exchange messages in predefined ways, which may include stages or tiers
-	**Authentication** – This process provides means to verify of the participants´identities
-	**Integrity** – It enforces the validation of the transaction integrity (e.g., mathematically through cryptography)
- **Nonrepudiation** – This provides means to verify that the supposed sender really sent the message
-	**Privacy** – It helps ensure that only the intended recipient can read the message
-	**Fault Tolerance** – The network operates efficiently and quickly, even if some nodes or servers fail or are slow
-	**Performance** – It considers throughout, liveness, scalability, and latency

Within these parameters, there are significantly differences between one consensus mechanism and another. 

Many blockchain platforms operate as a distributed computing system, often with orders of magnitude more nodes than their traditional counterpart. How these nodes communicate with one another and maintain truth in the presence of faults is known as consensus. First, consensus relevant to distributed computing is described, followed by the present-day case of blockchains. One strategy to handle updating the state involves replicating the database across multiple instances and comparing the information. The state of the system is a sequential list of commands that is replicated between all nodes in the network. Coming to consensus on the state means every node executes the linearly ordered log arriving at the same result. A consensus algorithm must maintain consistent copies of the state across all nodes and process updates proposed by any of those nodes.  Figure below illustrates consensus as a state diagram that seeks to identify who is proposing an update and how agreement is to be achieved all:

  ![consensus scope](https://github.com/aridiosilva/Blockchain/blob/main/Figure%2001%20Consensus%20Scope%20Blockchain.jpg)
  
  ![Figure - Historical Comparison of Consensus Mechanism (source; KPMG Report)](https://github.com/aridiosilva/Blockchain/blob/main/Figure%20-%20Historical%20Comparison%20of%20Consensus%20Mechanism%20(source%3B%20KPMG%20Report).jpg)

Various types of consensus algorithms have been devised over time for varying applications, but all of these algorithms must hold these properties for tolerating halting failures: 

1) **Termination**: the process of achieving consensus on a given data value should come to an end; i.e., eventually, every correct node must decide some value.
1) **Agreement seeking**: each consensus protocol should try to bring about as much agreement as possible from the network.
1) **Collaborative**: the aim of the participants of the system should be to work in unison for the welfare of the group by achieving a result that favors the best interest of the group.
1) **Cooperative**: the participants should not put their interests first and work as a team more than individuals.
1) **Egalitarian**: a system that is trying to achieve consensus must be as egalitarian as possible; i.e., weightage of every vote should be equal. In simple words, one vote cannot be less important than another.
1) **Inclusive**: for a system to reach consensus, it should try to involve as many entities as possible in the process. It should not be similar to normal voting; i.e., it should not be the case that certain entities do not vote because they feel that it is not worthy to cast their vote as it will not have any weightage in the long run.
1) **Participatory**: everyone should participate actively in the entire process of consensus. 
1) **Integrity**: if v is the value that is decided by the majority of correct processes, then that same value (v) must be decided by any correct process

### Actual Consensus Mechanisms

> - **Proof of Work (PoW)**: A compute-intensive protocol with proof of security; suitable for permission-less blockchain networks but can also be used in permissioned blockchain networks to increase security. The Bitcoin blockchain uses this protocol: unfortunately, many people mistakenly believe that all blockchain networks need to use this typically high-energy consumption protocol, which is not true. PoW is adopted by Bitcoin,Ethereum, etc. PoW selects one node to create a new block in each round of consensus by computational power competition. In the competition, the participating nodes need to solve a cryptographic puzzle. The node who first addresses the puzzle can have a right to create a new block. The flow of the block creation in PoW is presented in Fig. below. It is very difficult to solve a PoW puzzle. Nodes need to keep adjusting the value of nonce to get the correct answer, which requires much computational power. It is feasible for a malicious attacker to overthrow one block in a chain, but as the valid blocks in the chain increase, the workload is also accumulated, therefore overthrowing a long chain requires a huge amount of computational power. PoW belongs to the probabilistic-finality consensus protocols since it guarantees eventual consistency.
>  
>  ![PoW](https://github.com/aridiosilva/Blockchain/blob/main/Fig.%201.%20Flow%20of%20PoW.jpg) 
>
> - **Proof of Stake (PoS)**: A low-energy consumption protocol that is suitable for healthcare applications operating on permission-less or permissioned blockchain networks. In PoS, selecting each round of node who creates a new block depends on the held stake rather than the computational power. Although nodes still need to solve a SHA256 puzzle:
The different from PoW is that nodes do not need to adjust nonce for many times, instead, the key to solve this puzzle is the amount of stake (coins). Hence, PoS is an energy-saving consensus protocol, which leverages a way of the internal currency incentive instead of consuming lots of computational power to reach a consensus. The flow of PoS is shown in Fig. below. Like PoW, PoS is also a probabilistic-finality consensus protocol. PPcoin was the first cryptocurrency to apply PoS to the blockchain. In PPcoin, in addition to the size of the stake, the coin age is also introduced in solving a PoS puzzle. For instance, if you hold 10 coins for a total of 20 days, then your coin age is 200. Once a node creates a new block, his coin age will be cleared to 0. In addition to PPcoin, many cryptocurrencies adopt PoS, e.g., Nxt, Ouroboros. Note that Ethereum plans to transition from PoW to PoS.
>  
>  ![PoS](https://github.com/aridiosilva/Blockchain/blob/main/Fig.%202.%20Flow%20of%20PoS.jpg) 
>
> - **Delegated Proof of Stake(DPoS)**:
> 
>  The principle of DPoS is to let nodes who hold stake vote to elect block verifiers (i.e., block creators). This way of voting makes the stakeholders give the right of creating blocks to the delegates they support instead of creating blocks themselves, thus reducing their computational power consumption to 0. We can clearly see the flow of DPoS. DPoS is like a parliamentary system, if the delegates are unable to generate blocks in their turns, they will be dismissed and the stakeholders will select new nodes to replace them. DPoS makes the most use of the shareholders’ votes to reach a consensus in a fair and democratic way. Compared to PoW and PoS, DPoS is a low-cost and high-efficiency consensus protocol. There are also some cryptocurrencies adopting DPoS such as BitShares, EOS, etc. The new version of EOS has turned DPoS to BFT-DPoS (Byzantine  Fault Tolerance-DPoS).
> 
> ![DPoW](https://github.com/aridiosilva/Blockchain/blob/main/Fig.%203.%20Flow%20of%20DPoS..jpg)
> 
> - **Byzantine Fault Tolerance (BFT)**:
> 
>   BFT name came from a solution to “Byzantine generals’ problem,” a logical dilemma that researchers Leslie Lamport, Robert Shostak and Marshall Pease explained in an academic paper. BFT is being used to fix the issue of a rogue or unreliable node. If any member of the community sends inconsistent information to others about transactions, the reliability of the blockchain breaks down, and there is no central authority that can step in to correct it. To solve this, PoW already offers BFT through its processing power. On the other hand, PoS needs a more definite solution. Nodes will regularly vote in order to identify the true transaction. Using a version of PoS which works with BFT looks like the most promising approach to approving transactions in the blockchain.
> 
> - **PBFT (Practical Byzantine Fault Tolerance)**:
> 
>   PBFT is a Byzantine Fault Tolerance protocol with low algorithm complexity and high practicality in distributed systems [11]. PBFT contains five phases: request, pre-prepare, prepare, commit and reply. Fig. 4 describes how PBFT works. The primary node forwards the message sent by the client to the other three nodes. In the case that node 3 is crashed, one message goes through five phases to reach a consensus among these nodes. Finally, these nodes reply to the client to complete a round of consensus. PBFT guarantees nodes maintain a common state and take a consistent action in each round of consensus. PBFT achieves the goal of strong consistency, thus it is an absolute-finality consensus protocol. As mentioned before, EOS takes a combined consensus protocol. EOS leverages PBFT to simultaneously work with the block validation and creation in DPoS, greatly reducing the time required for a round of consensus [10]. A new protocol called Stellar is an improvement of PBFT. Stellar adopts FBA (Federated Byzantine Agreement) protocol, in which nodes can choose the federation they trust to conduct the consensus process [12].
>
> ![PBFT](https://github.com/aridiosilva/Blockchain/blob/main/Fig.%204.%20Process%20of%20PBFT..jpg)
> 
> - **SIEVE**:
> 
>   SIEVE consensus mechanism is being used by Hyperledger Fabric which allows the network to detect and remove possible non-deterministic requests, and also achieve consensus on the output of the suggested transactions.
> 
> - **Ripple**: 
> 
>   Ripple is an open source payment protocol [13]. In Ripple, transactions are initiated by clients and broadcast throughout the network via tracking nodes or validating nodes. However, the consensus process in Ripple is performed by validating nodes, each of which owns a list of trusted nodes called UNL (Unique Node List). Nodes in UNL can vote on the transactions they support. The process of consensus in Ripple is presented in Fig. 5. Each validating node sends its own transactions set as a proposal to other validating nodes. Once receiving the transaction proposals sent by nodes in UNL, the validating node will check each transaction in the proposal. The transaction in the proposal will get one vote if there is the same transaction in its local transactions set. When the transaction gets more than  of the votes, this transaction will enter the next round. The screening threshold will be increased for each round, and transactions with more than  of the votes will be finally recorded in the distributed ledger. Hence, Ripple is an absolute-finality consensus protocol. Ripple use “collectively trusted sub-networks” consensus algorithms called “Unique Node Lists”(UNL) to deal with high latency, which usually characterizes BFT-tolerant systems. To reach consensus, a node requires to ask its own UNL in place of the entire network. This mechanism allows less than one-fifth of its nodes being faulty.
>
> ![ripple](https://github.com/aridiosilva/Blockchain/blob/main/Fig.%205.%20Process%20of%20Ripple..jpg)
>
> - **Proof of Elapsed Time (PoET)**:
> 
>   Proof of Elapsed time is a network consensus protocol invented and developed by the Intel Corporation in 2016. A lottery-based, low-energy consumption protocol that can scale well for a network with many nodes while needing more time to reach consensus. The algorithm is predominantly used in permissioned blockchain ledgers. The hardware used in PoET is specially designed for this protocol. For example, Intel Software Guarded Extension (SGX) is used in networks using PoET. This consensus protocol is used to allocate blocks to miners on the network. In permissioned blockchain systems, the miners’ identity is determined before allowing access int o the network. Therefore, anonymity is not a feature in this protocol. Each node in the network is assigned a random waiting time. The first node to complete the randomly chosen period validates the new block. The specialized hardware puts the processor to sleep during the wait time—this repeats over all the blocks in the network. he major disadvantage of this algorithm is its dependency on specialized hardware. This exposes it to various security vulnerabilities due to the lack of standardized and tried and tested protocols. IBMs Hyperledger Sawtooth supports PoET mechanism for custom blockchain applications development.
>   
>   Proof of Elapsed Time (PoET), a lottery style blockchain network consensus mechanism, has a similar workflow like that of the PoW mechanism, but it requires far less
computational resources, i.e., it eradicates the need for mining-intensive processes, thus preventing high energy consumption and resource utilization. In PoET, a separate
random timer that operates independently at every node of the distributed ledger determines whether or not that node creates the new block for the blockchain and gets the reward. Thus, it mainly focuses on efficiency and ensures that the probability of every node to be the next block generator is equally likely.
>
>   The PoET concept was invented to solve the computing problem of “Random Leader Election” and is essentially used to achieve consensus in the permissioned blockchain 1.2 networks. As stated above, in PoET, each participating node within the network is given a random timer object; i.e., each node is required to wait for a randomly chosen amount of time. Each of the nodes within the blockchain network goes to sleep for the duration specified by their timer. +e node which completes the designated waiting time first; i.e., the one with the shortest wait time becomes the next block generator and commits a new block to the blockchain by broadcasting the new block to the entire peer network. +e process of choosing the block generator is depicted in Figure below. For the discovery of the subsequent blocks, the method is repeated.
>   
>   Before moving on to the working of the PoET mechanism, we need to go through a sophisticated technology that plays a crucial role in this protocol, namely, Software Guard
Extension (SGX). It is effectively a set of security-related instruction code executed on CPU which is employed by applications to isolate certain trusted regions of code and
data. +ese isolated regions are called enclaves. It primarily protects sensitive data and code from any outer interference or inspection, by providing a secure enclave for developers. Primarily, SGX functions to provide a trusted execution environment (TEE) which allows specific trusted code and data to execute independently of the application and system on which it runs [36]. Code that executes in a trusted environment created using SGX has the capability to generate a signed attestation from within the platform or application which is rooted in the CPU and provides authentication that the code has been correctly booted up in a trusted environment. SGX acts as a mechanism by which participant nodes hitch the network and confirm whether they are executing the trusted code needed for the PoET consensus implementation.
>
>    ![PoET](https://github.com/aridiosilva/Blockchain/blob/main/Fig.%206.%20Process%20of%20PoET.jpg)
>
> - **Proof of activity (PoA)**:
> 
>   To avoid hyperinflation (what happens when too much of a currency floods the system) bitcoin will only ever produce 21m bitcoins. That means, at some point, the bitcoin block reward subsidy will end and bitcoin miners will only receive transaction fees. Some have speculated this might cause security issues resulting from a ‘tragedy of the commons‘, where people act in self-interest and spoil the system. So, proof of activity was created as an alternative incentive structure for bitcoin. Proof of activity is a hybrid approach that combines both proof of work and proof of stake. In proof of activity, mining kicks off in a traditional proof-of-work fashion, with miners racing to solve a cryptographic puzzle. Depending on the implementation, blocks mined do not contain any transactions (they are more like templates), so the winning block will only contain a header and the miner’s reward address. At this point, the system switches to proof of stake. Based on information in the header, a random group of validators is chosen to sign the new block. The more coins in the system a validator owns, the more likely he or she is to be chosen. The template becomes a full-fledged block as soon as all of the validators sign it. If some of the selected validators are not available to complete the block, then the next winning block is selected, a new group of validators is chosen, and so on, until a block receives the correct amount of signatures. Fees are split between the miner and the validators who signed off on the block. Criticisms of proof of activity are the same as for both proof of work (too much energy is required to mine blocks) and proof of stake (there is nothing to deter a validator from double signing). 
Decred is the only coin right now using a variation of proof of activity.
>
> - **Proof of Burn (PoB)**:
> 
>   With proof of burn, instead of pouring money into expensive computer equipment, you ‘burn’ coins by sending them to an address where they are irretrievable. >   By committing your coins to never-never land, you earn a lifetime privilege to mine on the system based on a random selection process. Depending on how proof of burn is implemented, miners may burn the native currency or the currency of an alternative chain, like bitcoin. The more coins you burn, the better chance you have of being selected to mine the next block. Over time, your stake in the system decays, so eventually you will want to burn more coins to increase your odds of being selected in the lottery. (This mimics bitcoin’s mining process, where you have to continually invest in more modern computing equipment to maintain hashing power.) While proof of burn is an interesting alternative to proof of work, the protocol still wastes resources needlessly. Another criticism is that mining power simply goes to those who are willing to burn more money. The only coin that uses proof of burn is slimcoin, a cryptocurrency based on peercoin. It uses a combination of proof of work, proof of stake and proof of burn, but is only semi-active at this time.
>   
>   In Proof-of-Burn, rather than spending money on expensive computer equipment, you ‘burn’ coins by sending them to an address where they are unrecoverable. You can earn a lifetime privilege to mine on a system based on a random selection process. Miners can burn the native currency or any currency of an alternative chain. The more number of coins you burn, the chances are high that you will be selected to mine the next block. If your stake in the system fails, so eventually, you will want to burn more coins to increase your odds of being selected for the next block. PoB is a good alternative for PoW, although the protocol wastes resources. Slimcoin is the only coin who uses Proof-of-Burn. Slimcoin uses a combination of PoW, PoS, and PoB.
>
> - **Robust Proof of Stake (RPoS)**:
> 
>    The RPoS selects the data-writing node based on the coin balance, and others will accept the new data to keep the ledger consistent. RPoS uses the amount of coins to select miners and limits the maximum value of the coin age to effectively avoid coin age accumulation attack and Nothing-at-Stake (N@S) attack. Under a comparison framework, we show that the RPoS equals or outperforms Proof of Work (PoW) protocol and Proof of Stake (PoS) protocol in three dimensions: energy consumption, robustness, and transaction processing speed. To compare the three consensus protocols in terms of trade eciency, we built an agent-based model and find that RPoS protocol has greater or similar trade request-satisfied ratio than PoW and PoS. Hence, we suggest that RPoS is very suitable for building a robust digital economy distributed system.
>
> - **Proof of Capacity (PoC)**:
> 
>   This consensus algorithm mechanism is different from others. Here you pay for your hard disk space. The more hard disk space you have, the chances are high that you will mine the next block & earn rewards. Before mining in a PoC, the algorithm generates a large number of data sets known as ‘plots’, which you store on your hard drive. The more number of plots you have, you have better chances of finding the next block. To use this mechanism, you have to spend a lot on hard drive space. Burstcoin is the only cryptocurrency to use a form of proof of capacity.
>   
>   As we’ve seen, most of these alternative protocols employ some type of pay-to-play scheme. Proof of capacity is no different, but here you ‘pay’ with hard drive space. The more hard drive space you have, the better your chance of mining the next block and earning the block reward. Prior to mining in a proof-of-capacity system, the algorithm generates large data sets known as ‘plots’, which you store on your hard drive. The more plots you have, the better your chance of finding the next block in the chain. By investing in terabytes of hard drive space, you buy yourself a better chance to create duplicate blocks and fork the system. But with proof of capacity, we still have the problem of nothing at stake to deter bad actors. Variations of proof of capacity include proof of storage and proof of space. Burstcoin is the only cryptocurrency to use a form of proof of capacity.
>
> - **Leased Proof of Stake (LPoS)**:Ç
> 
>   LPoS is an enhanced version of PoS consensus mechanism that operates on the Waves platform. Unlike the regular Proof-of-Stake method where each node with some amount of cryptocurrency is entitled to add the next blockchain, users can lease their balance to full nodes in this consensus algorithm. And the one that leases the bigger amount to the full node have a higher probability of generating the next block. Also, the leaser is then rewarded with a percentage of transaction fee that has been collected by the complete node. This PoS variant is an efficient and safe option for the development of public cryptocurrencies.
>
> - **Direct Acyclic Graph (DAG)**:
> 
>   Another basic yet prime blockchain consensus model that every mobile app development services company working with Blockchain must be familiar with is DAG. In this type of Blockchain consensus protocol, every node itself prepares to become the ‘miners’. Now, when miners are eradicated and transactions are validated by users itself, the associated fee reduces to zero. It becomes easier to validate transactions between any two closest nodes, which makes the whole process lightweight, faster, and secure. The two best examples of DAG algorithm are IOTA and Hedera Hashgraph. Though these are the prime consensus models in the development environment, many different blockchain consensus mechanisms have slowly and gradually starting gaining momentum.
>   
> - **Proof of Identity (PoI)**:
> 
>   The concept of PoI (Proof of Identity) is just like that of the authorized identity. It is a piece of cryptographic confirmation for a users’ private key that is being attached to each particular transaction. Each identified user can create and manage a block of data that can be presented to others in the network. This blockchain consensus model ensures authenticity and integrity of the created data. And thus, is a good choice for introducing in smart cities.
>   
> - **Proof of Importance (PoI)**:
> 
>   Introduced by NEM, PoI is a variation of PoS protocol that considers the role of shareholders and validators for its operation. However, this is not only influenced by the size and chance of their shares; various other factors like reputation, overall balance, and no. of transactions made through any particular address also plays a role in it. 
The networks based on POI consensus model are expensive to attack on and rewards users for contributing to the network’s security.
>   
> - **Mining Diversity**: A round-robin, low-energy consumption protocol specifically designed for permissioned healthcare applications.31 Variations can be designed to suit various needs.
> 
> - **Kafka**: A voting-based, low-energy consumption protocol that can finalize the consensus decision faster (at least initially), but that requires more time as the number of nodes in the network grows.
>
> - **Round Robin Consensus**:
> 
>   In Round Robin Consensus, validators participate in the consensus process by signing votes for blocks. There are three types of votes: a prevote, a precommit and a commit. To receive more than two third of commits means to receive commits from a two third majority of validators. A block is said to be committed by the network when a two third majority of validators have signed and broadcasted commits for that block. At each height of the blockchain a round-based protocol is run to determine the next block. Each round comprises of three steps (Propose, Prevote, and Precommit), along with two special steps Commit and NewHeight. The Propose, Prevote, and Precommit steps each take one third of the total time allocated for that round. Each round is longer than the previous round followed by a small fixed increase of time. This allows the network to eventually achieve consensus in a limited concurrent network. Round robin consensus process doesn’t depend on a single participant for block validation, Here Multiple nodes play a key role in validating and signing transactions which make this process more secure as compare to other consensus process. It has lesser probability of double spend attack because of the voting power distribution among trusted nodes. Round robin consensus mechanism is best suitable for provenance bases usecases like: trade finance, supply chain etc. Examples: Multichain, Tendermint
>  
> - **Federated Consensus**:
> 
>   In Federated Consensus, every participant in the network trusts a set of signers for reaching the consensus stage. To do it efficiently, block signers use a single block generator, which receives, holds and filters transaction. The generator’s signature is used to coordinate with signers for block validation process. Block signer verifies the block which is signed by block generator and which fulfills the certain conditions set by the network. Block get published to the network, once the block generator got enough signatures from the network. Federated consensus reliance a on single participant which provides many efficiencies and simplicity benefits and has only limited downsides in target use cases. It guarantees safety and liveness. This consensus mechanism is best for use cases like: cross boarder remittance, real time KYC etc. Examples: Stellar, Ripple 
>
> - **Consensus Protocol Comparison**:
>  
> ![comparison consensus Mechanisms](https://github.com/aridiosilva/Blockchain/blob/main/Table%207%20-%20Comparison%20Consensus%20Mechanismos%20os%20Blockchain001___.png)
>
> i) Fault tolerance
> 
>  PoW, PoS and DPoS are probabilistic-finality protocols, and attackers need to accumulate a large amount of computational power or coins (stake) to create a long private chain to replace a valid chain. For instance, in Bitcoin, a  fraction of the computational power is sufficient for an attacker to create a longer private chain to successfully complete a double-spend attack [1]. Hence, if attacker’s fraction of the computational power is more than or equal to , the blockchain network will be undermined. Like PoW, PoS and DPoS can only allow the existence of the stakeholder with less than  of the held stake. In PBFT, if there are a total of  nodes in the network, the number of normal nodes must exceed , which means that the number of malicious or crashed nodes must be less than . Therefore, the fault tolerance of PBFT is 1/3 [11]. The fault tolerance of Ripple is only , i.e., Ripple can tolerate Byzantine Problem in  of nodes in the entire network without affecting the correct result of consensus [13].
>
> ii) Limitation
> 
> There is no doubt that PoW consumes the most computational power among these consensus protocols, and the transaction throughput per second (TPS) of Bitcoin adopting PoW is only 3–7, which greatly limits the application prospect of PoW in actual payment. PoS and DPoS have similar shortcomings, although they can greatly reduce the consumption of the computational power, only the stakeholders can get the block reward, which leads to the great reduction in the liquidity of coins in DPoS, the poorer the poor and the richer the rich. PBFT requires each node communicating with other nodes to exchange messages in each round of the consensus, PBFT thus has extremely high performance requirements for the network. Moreover, the identity of each node participating in the consensus is known, so there is no guarantee on the anonymity. In Ripple, a round of consensus process is completed in a few seconds, which is suitable for the actual payment scenario. However, Ripple is managed and controlled by a few organizations, which does not satisfy the decentralization nature of blockchain.
>
> iii - Scalability
> 
> PoW, PoS and DPoS all have good scalability. Although TPS of them is not very high, there are some ways that can help improve the scalability. For instances, Bitcoin adopts lightning network to provide an off-chain payment to improve the scalability [14]. Ethereum proposed the sharding technology and Plasma, which are layer 1 and layer 2 scaling solutions, respectively [15]. The scalability of PBFT is limited since PBFT is suitable for a high performance network with a small number of nodes. Unlike PBFT, Ripple can be suitable for a large scale network, and TPS of Ripple is over 1500, hence Ripple has strong scalability.
>
> iv - Scenarios
> 
> Current blockchain systems can be categorized into three types. In public blockchain, everyone can take part in the consensus process and the distributed ledger is visible to the public. PoW, PoS, and DPoS can be applied to public blockchain. Private blockchain and consortium blockchain belong to the permissioned blockchain as only permitted nodes can participate in the consensus process. The identity of each node is known to the public in PBFT and Ripple, thus they are all suitable for private blockchain or consortium blockchain. Although private blockchain and consortium blockchain are not as decentralized as public blockchain, due to the strong consistency and high efficiency of consensus, they are more suitable for some commercial and medical scenarios.
>
> v - Conclusion
> 
> The consensus protocol is the guarantee for the stable operation of blockchain systems. Nodes agree on a certain value or transaction through the consensus protocol. In this paper, we introduced some popular blockchain consensus protocols and found their strengths, weaknesses and application scenarios through analysis and comparison. We concluded that designing a good consensus protocol should consider not only good fault tolerance but also how to make the best use of it in the appropriate application scenario.


## F3 - Special Hardware Requirement 

> - **Yes**: If special hardware (eg, Intel SGX43) is required, the specifications of the computing environment need to be confirmed before the healthcare applications can be deployed properly.
> - **No** : If no special hardware is required, the healthcare application can be deployed without further hardware checking.

## F4 - Smart Contracts Support 

> - **Yes**: If the healthcare applications focus on autonomous operations (eg, automatic payment for insurance claims), the immutable smart contract support can be essential.
> - **No** : If the healthcare applications aim at primarily serving as a ledger (eg, recording access rights or data transaction records), the blockchain platform without smart contract support would be sufficient.

## F5 - Scripting Language

> - **Bitcoin Script**: If smart contracts are not required for the healthcare applications, this basic scripting language would be sufficient.
> - **Solidity**: The main smart contract language for Ethereum; it is one of the most popular languages for writing smart contracts.
> - **Chaincode**: The main smart contract language for Hyperledger Fabric; it is also one of the most popular languages for writing smart contracts.

## F6 - Software License 

> - **MIT**: A “permissive” license that allows healthcare applications to reuse the source code of the platform.
> - **GPL**: A “copyleft” license that also allows using the source code; the derivative works in some situations
must be open-source too.

# Summary of Blockchain Platforms

As we can see described below a brief summaries, no platform is perfect, and in the future the best features may be adopted by the platforms that remain in the market. It is unlikely that more than 3 or 4 platforms will become very relevant in specific business domains than others. For example, in terms of platforms likely to continue to be used for healthcare applications, Ethereum, Hyperledger and MultiChain are at the top of the list because they combine the most relevant features at the moment.

> - **Bitcoin** 
> 
>    Bitcoin, the first well-known and widely used *distributed cryptocurrency*, operates a *peer-to-peer network* without *central authority* or banks, and introduced the *blockchain technology and platform* to the world. The *management of transactions* and the issuance of coins are carried out collectively by the *blockchain network*. Bitcoin
uses *PoW* as its *consensus protocol* to verify *transactions*, and thus consumes a lot of energy. Owing to the success of Bitcoin, many other alternative cryptocurrencies and consensus protocols.
>
> - **Ethereum**
> 
>   Ethereum is a platform that lets anyone build and use *smartcontract-based decentralized applications* that run on blockchain technology. Ethereum focuses on the capability of *automatic digital asset management*, and, to do so, it supports *smart contracts* or *properties*, making the creation of the *asset managing programs* easier than when using the *scripting language* in the Bitcoin Blockchain. Ethereum also adapts the *PoW consensus protocol*.
>
> - **Zcash**
> 
>   Zcash is a decentralized and open-source cryptocurrency that offers *privacy* and *anonymity of transactions*. A challenge of the Bitcoin Blockchain is that, although the senders and recipients are represented with a *hashed address*, given enough *transaction data*, the *transactions* may still be *linked or traced through careful analysis and
inspection*. To improve this, Zcash uses a *zero-knowledge proof algorithm* known as *zk-SNARK*, to ensure that the *sender*, *recipient*, and *amount of a transaction* remain *private* even on a *publicly available blockchain network*, and thus improves the *privacy* or *anonymity of the transactions*, while verifying the transactions privately to avoid the *double spending problem*. This *level of privacy or anonymity* is also highly requireblle in healthcare applications, por example. Also, Zcash addresses the *mining centralization issue*. However, as many applications may be run on permissioned networks, platforms like Zcash that use *PoW* are less attractive than others that use different protocols.
>
> - **Litecoin**
>
>   Litecoin is a *decentralized global payment network*. The major change of Litecoin, compared with Bitcoin, is that Litecoin has a *faster transaction speed* (4 times quicker) at the expense of *4 times smaller storage space* and reduced security. Also, Litecoin adopts the *“Scrypt” hash algorithm* for the *PoW* to mitigate the *mining centralization issue*. Speed could become important in some applications in which immediate decisions are needed, but, so far, we have not seen examples of *blockchain-based applications* in business domains in which this was a *critical factor*. For example, we have not encountered situations in which a healthcare blockchain needed to accommodate as many transactions per minute as credit cards or major retailers’ websites do.
>
> - **Dash**
> 
>   Dash (or Digital Cash) is a *privacy-centric digital currency* with *instant transactions*. It is based on the *Bitcoin software*, and adds an *additional “Masternode” network tier* on top of the *Bitcoin Blockchain network*. The *Masternode network( is composed of *nodes* that are willing to put “collateral,” such as 1000 DASH coins, to serve as the *full nodes* to validate the *transactions*. The *Masternode( offers additional *privacy or anonymity* to the users via *“Darksend” (based on the “CoinJoin” technology*, a process of *merging multiple transactions together* so that the *attacker* cannot *link the transactions* using *histories*). Also, the relatively few *collateral nodes* in the *Masternode network* can speed-up the *validation process*, providing an *instant transaction mechanism* known as *“InstantX.”* The additional *privacy* for the users is attractive to some business domain applications but the *centralization* introduced by *Masternode* is a downside.
>
> - **Peercoin**
> 
>   Peercoin was derived from Bitcoin to *reduce the energy required for the coin mining process*. That is, Bitcoin’s *PoW algorithm* depends on *energy consumption1*, that, in the long run, will result in lower motivation for *miners* to keep building *blocks* unless *transactions fees* rise to high enough levels to sustain the *high energy consumption*. To avoid this situation, Peercoin proposed to initially adopt PoW and eventually switch to *Proof of Stake (PoS)*. While more appropriate for some business domain applications than *PoW*, *PoS* may also not be necessary, particularly when operating in *permissioned networks*, as the threat of *“fake” blocks* is less severe. However, for public networks, Peercoin may offer a good compromise by supporting *PoS*. 
>
> - **Ripple**
>  
>   Ripple is a *low-latency blockchain network* that atomically settles and records *transactions* on a *secure distributed database*, the *Ripple Consensus Ledger*. Ripple applies the *Ripple Consensus Protocol Algorithm*, an alternative algorithm to the *high-latency Bitcoin Blockchain PoW*, for handling the *Byzantine Generals’ Problem* and the *Sybil Attack*. The *blocks* are only validated by the relatively few *“Chosen Validators”* to enable *low-latency transactions*. While reaching consensus, the *current distributed ledger* is “closed” and considered the most recent one. Also, *Ripple coins* are *“pre-mined”* and cannot be created during the *consensus process*. 
>
> - **Monero**
> 
>   Monero is a secure, private, and untraceable cryptocurrency. Monero offers privacy or anonymity to its users by using the “Ring Confidential Transactions” (a ring signature algorithm based on CryptoNotethat generates a group signature and in which the actual signer cannot be identified) and the *“Stealth Address”* (an onetime address for each transaction) technologies, to *obfuscate the origins, destinations, and amounts of all transactions*. Therefore, the ability to “hide the destination and origin of transactions” is an important feature of Monero. This platform might be considered in applications in which the privacy or anonymity of participant users is at stake, although it only supports the *high energy consumption PoW protocol*.
> 
> - **MultiChain**
>
>   MultiChain is a blockchain platform to create and deploy *permissioned* or *private blockchain networks*. As a *fork* of the *Bitcoin Blockchain*, MultiChain focuses on providing features such as *integrating user permission management* and improve the *data ledger functions*. Also, MultiChain supports both *Bitcoin Blockchain PoW* and *“Mining Diversity,”* a *round-robin-based consensus protocol*.  The basic idea of *Mining Diversity* is that, within a *private blockchain network*, the participants are already “trusted” to some extent because they are *identifiable entities*. Therefore, *Mining Diversity* can provide consensus and mining securely on the private blockchain network without the need for the computationally intensive PoW algorithm. However, MultiChain *does not provide additional privacy for users* as do some other platforms.
>
> - **Hyperledger**
> 
>   Hyperledger is an *open-source collaborative effort* created to *advance permissioned or private, cross-industry blockchain technologies*. As the use of blockchain must respond to different needs, Hyperledger provides an infrastructure to include a range of modules, such as various *smart contract engines*. Specifically, Hyperledger
includes *differentiated blockchain frameworks and tools*. Each framework supports *different types of consensus protocols*. Hyperledger *does not support PoW* and the additional *privacy protection* is yet to be included. It should also be noted that Hyperledger has *global collaborations* with various companies.  
>

# Blockchain Applications and Services 

There are also applications and services associated with blockchains and distributed ledgers that add to their usefulness for recordkeeping. These include blockchain applications that run over blockchain networks and permit participants to easily interact with these networks.

## Smart Contracts

According to Nick Szabo in his “The Idea of Smart Contracts,” smart contracts are blockchain applications that express business logic associated with a transaction and execute on a blockchain platform. Smart contract code determines what transactions are recorded into the blockchain and the information they will contain. Through the use of smart contracts, many kinds of contractual clauses may be made partially or fully self-executing and self-enforcing. Asset registries link digital currencies to other assets or records on top of a distributed ledger, according to InterPARES Trust Terminology Project: “Key Blockchain Terms and Definitions.”

## Off-Chain Services

Off-chain services provide secure means to access capabilities outside a blockchain system, such as trusted data sources or functions. Sidechains are physically separate blockchains associated with a main blockchain, and they can participate in transactions with it, typically in both directions. In contrast, subchains are logically separate
chains that form part of a blockchain. Each subchain may be owned by a different entity and may be accessible to a different set of users. Nodes may be set up so that some nodes participate in certain subchains and not in others. The result of this configuration is that the ledger on some nodes contains transactions for that subchain while the ledgers on other nodes do not.

# What is blockchain technology?

Blockchain is a shared, immutable ledger for recording transactions, tracking assets and building trust. 

# Blockchain overview

## Blockchain defined:

Blockchain is a shared, immutable ledger that facilitates the process of recording transactions and tracking assets in a business network. An asset can be tangible (a house, car, cash, land) or intangible (intellectual property, patents, copyrights, branding). Virtually anything of value can be tracked and traded on a blockchain network, reducing risk and cutting costs for all involved.

## Why blockchain is important: 

Business runs on information. The faster it’s received and the more accurate it is, the better. Blockchain is ideal for delivering that information because it provides immediate, shared and completely transparent information stored on an immutable ledger that can be accessed only by permissioned network members. A blockchain network can track orders, payments, accounts, production and much more. And because members share a single view of the truth, you can see all details of a transaction end-to-end, giving you greater confidence, as well as new efficiencies and opportunities.

# Key elements of a blockchain

### a) Distributed ledger technology

All network participants have access to the distributed ledger and its immutable record of transactions. With this shared ledger, transactions are recorded only once, eliminating the duplication of effort that’s typical of traditional business networks.

**Some advantages** of a distributed system over single computers are:

> - Higher computing power
> - Cost reduction
> - Higher reliability
> - Ability to grow naturally

**Some disadvantages** of distributed systems compared to single computers are:

> - Coordination overhead
> - Communication overhead
> - Dependency on networks
> - Higher program complexity
> - Security issues

### b) Peer-to-Peer Systems (P2P)

Peer-to-peer networks are a special kind of distributed systems. They consistof individual computers (also called nodes), which make their computational. resources (e.g., processing power, storage capacity, data or network bandwidth) directly available to all other members of the network without having any central point of coordination. The nodes in the network are equal concerning their rights and roles in the system. Furthermore, all of them are both suppliers and consumers of resources. Peer-to-peer systems have interesting applications such as file sharing, content distribution, and privacy protection. Most of these applications utilize a simple but powerful idea: turning the computers of the users into nodes that make up the whole distributed system. As a result, the more users or customers use the software, the larger and more powerful the system becomes. This idea, its consequences, and it challenges are discussed in the following steps.

### c) Immutable records

No participant can change or tamper with a transaction after it’s been recorded to the shared ledger. If a transaction record includes an error, a new transaction must be added to reverse the error, and both transactions are then visible.

### d) Smart contracts

To speed transactions, a set of rules — called a smart contract — is stored on the blockchain and executed automatically. A smart contract can define conditions for corporate bond transfers, include terms for travel insurance to be paid and much more.

# Benefits of blockchain

What needs to change: Operations often waste effort on duplicate record keeping and third-party validations. Record-keeping systems can be vulnerable to fraud and cyberattacks. Limited transparency can slow data verification. And with the arrival of IoT, transaction volumes have exploded. All of this slows business, drains the bottom line — and means we need a better way. Enter blockchain.

### a) Greater trust

With blockchain, as a member of a members-only network, you can rest assured that you are receiving accurate and timely data, and that your confidential blockchain records will be shared only with network members to whom you have specifically granted access.

### b) Greater security

Consensus on data accuracy is required from all network members, and all validated transactions are immutable because they are recorded permanently. No one, not even a system administrator, can delete a transaction.

### c) More efficiencies

With a distributed ledger that is shared among members of a network, time-wasting record reconciliations are eliminated. And to speed transactions, a set of rules — called a smart contract — can be stored on the blockchain and executed automatically.

# Types of blockchain networks

There are several ways to build a blockchain network. They can be public, private, permissioned, or built by a consortium.

## a) Public blockchain networks

A public blockchain is one that anyone can join and participate in, such as Bitcoin. Drawbacks might include substantial computational power required, little or no privacy for transactions, and weak security. These are important considerations for enterprise use cases of blockchain.

## b) Private blockchain networks

A private blockchain network, similar to a public blockchain network, is a decentralized peer-to-peer network. However, one organization governs the network, controlling who is allowed to participate, execute a consensus protocol and maintain the shared ledger. Depending on the use case, this can significantly boost trust and confidence between participants. A private blockchain can be run behind a corporate firewall and even be hosted on premises.

## c) Permissioned blockchain networks

Businesses who set up a private blockchain will generally set up a permissioned blockchain network. It is important to note that public blockchain networks can also be a permissioned. This places restrictions on who is allowed to participate in the network and in certain transactions. Participants need to obtain an invitation or permission to join.

## D) Consortium blockchains

Multiple organizations can share the responsibilities of maintaining a blockchain. These pre-selected organizations determine who may submit transactions or access the data. A consortium blockchain is ideal for business when all participants need to be permissioned and have a shared responsibility for the blockchain.

# Types of Blockchain Consortium

## Business-Focused

These tend to develop blockchain solutions for a specific business issue. Mainly all the solutions are for business purpose only. Example: Tradelens

## Technology-Focused

These offer reusable blockchain platforms, solutions based on technical standards. Mainly these have multipurpose use cases. Ex: Hype























