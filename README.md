# Blockchain

Blockchain is a distributed ledger—write once and never erase. Although originally invented for financial transactions,1 its applications are broad. Refered as Distributed Ledger Technology (DLT)  makes the history of any digital asset unalterable and transparent through the use of descentralization and cryptographic hashing.

- [Hyperledger Whitepaper](https://github.com/aridiosilva/Blockchain/blob/main/Whitepaper%20-%20Hyperledger.pdf)
- [Whitepaper - Bitcoin A Peer-to-Peer Electronic Cash System - Satoshi Nakamoto ](https://github.com/aridiosilva/Blockchain/blob/main/Whitepaper%20-%20Bitcoin%20A%20Peer-to-Peer%20Electronic%20Cash%20System%20%20-%20Satoshi%20Nakamoto%20%20%209%20pages%202008.pdf)
- [Whitepaper - Practical Byzantine Fault Tolerance - Miguel Castro and Barbara Liskov](https://github.com/aridiosilva/Blockchain/blob/main/Whitepaper%20-%20%20Practical%20Byzantine%20Fault%20Tolerance%20-%20Miguel%20Castro%20and%20Barbara%20Liskov.pdf)

- [Blockchan simply explained in this video](https://www.youtube.com/watch?v=SSo_EIwHSd4)

# Main Elements of Blochchain

![main elements](https://github.com/aridiosilva/Blockchain/blob/main/Main%20Elements%20of%20blockchain.jpg)

# Blockchain Structure

![Blockchain Merkle tree](https://github.com/aridiosilva/Blockchain/blob/main/Blockchain_and_Merkle_Tree_figure001.jpg)

To reduce storage, if a block B is “voted” to be correct because the chain is long enough (ie, there are already many blocks created after B), we can discard the transactions contained in B, without changing the hash of B’s header (otherwise all blocks after B would need to be changed). To do this, instead of saving the content of all transactions directly in a block, we first compute the hash values of each transaction, and then construct a tree structure (a Merkle tree), to “combine” (ie, hash again) all hash values, and store only the Merkle Root hash value at the block header. This way we can prune the transactions in the tree later, without changing the Merkle Root and the block header. In other words, the size of the blockchain is now proportional to the number of blocks instead of being proportional to the number of transactions. (A) An example blockchain without a Merkle tree. The blocks enclose transactions without adopting a Merkle tree. As a result, the size of a block will grow proportionally to the number of transactions (eg, transaction T12) that are enclosed. (B) A blockchain with a Merkle tree. A Merkle tree is constructed by hashing paired data (the leaves) to create a parent node iteratively, until a single hash, the Merkle Root,1 remains. In this example, the transactions (eg, T12) are first encoded into a binary raw-transaction format and then hashed to create the hashes (eg, Hash of T12). Then, hashes such as the Hash of T12 are paired with other hashes such as the Hash of T11 (if a hash does not have a pair, it simply duplicates itself to be paired) to compute the hash as their parent node (ie, Hash of T11–12). The pairing/hashing process repeats until only 1 hash (the Merkle Root) remains, and the Merkle tree construction process is then completed. Finally, by only enclosing the Merkle Root in each block header, the storage space required to verify the integrity/validity of transactions can be reduced.56 That is, if an attacker tries to change the content of any transaction such as T12, all of the related hashes (ie, Hash of T12, Hash of T11–12, and Hash of T11–14), and eventually the Merkle Root (ie, Hash of T11–18) will also change and can be easily verified. To enclose this new Merkle Root to pass the verification process, the attacker then needs to re-create block B1 and all blocks thereafter, which is computationally expensive and is enough to prevent such modification. A Merkle tree is the basis of lightweight nodes described in Figure 3 (ie, the blockchain nodes that only need to verify transactions can store parts of the Merkle trees to save space, while the full blockchain nodes that need to “mine” new blocks store all of the Merkle trees).

![another approach Merkle tree](https://github.com/aridiosilva/Blockchain/blob/main/Blockchain_and_Merkle_Tree_figure002_reduced.jpg)

Another technique to reduce the need for each user to keep the full history of transactions is to use lightweight nodes together with a Merkle tree. For a user who only wants to use coins but does not want to “mine” new blocks, the full transaction history (more than 150 GB as of January 2018) is too large, especially for smartphones. Therefore, a user can adopt lightweight nodes1 so that only the Merkle Branch1 that links the transactions that the user would like to verify is used. An example of the Merkle Branch for transaction T12 stored on a blockchain lightweight node (eg, on a mobile device), in contrast to the data storage of a full node (eg, on a personal computer), is shown in this figure. With the use of the Merkle tree, a lightweight node only stores data relevant to specific transactions (eg, T12) to save space.1 For example, in addition to T12 itself, this lightweight node only needs to store related hashes (ie, Hash of T11, Hash of T13–14, and Hash of T15–18), instead of storing the full Merkle tree, to make sure T12 is linked to block B1. That is, one can first compute the Hash of T12 using T12, and then compute the Hash of T11–12 using the Hash of T11 and the Hash of T12. Eventually, one can compute the value of the Merkle Root (Hash of T11–18), and compare it with the one stored in B1, to make sure T12 has been verified in B1. This way, a lot of required storage space for those lightweight nodes is saved, making applications such as wallet apps on mobile devices feasible. This verifying process is also known as Simplified Payment Verification.1,59 As a result, users/nodes can be divided into 2 groups: full nodes (the ones storing the whole transaction history and performing mining) and lightweight nodes (ie, the nodes using Simplified Payment Verification just for transactions, without mining), thus reducing the storage space for lightweight nodes and improving the scalability of a blockchain network.

# Features of Blockchain Plaforms -  Main Options and Implications

## F1 - Network Permission

> - **Permissionless network**: A public blockchain network configuration designed to allow public participation;
> - **Permissioned network**  : A private blockchain network configuration that includes only authorized participants;

## F2 - Consensus Protocols

Consensus Mechanism is a method of autenticating and validating a value or transaction on a Blockchain or a Dsitributer Ledge without the need to trust or rely on a central authority. Consensus mechanisms are central to the functioning of any blockchain or distributer ledger.

How Concensus Mechanisms work
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
>  The principle of DPoS is to let nodes who hold stake vote to elect block verifiers (i.e., block creators). This way of voting makes the stakeholders give the right of creating blocks to the delegates they support instead of creating blocks themselves, thus reducing their computational power consumption to 0. We can clearly see the flow of DPoS. DPoS is like a parliamentary system, if the delegates are unable to generate blocks in their turns, they will be dismissed and the stakeholders will select new nodes to replace them. DPoS makes the most use of the shareholders’ votes to reach a consensus in a fair and democratic way. Compared to PoW and PoS, DPoS is a low-cost and high-efficiency consensus protocol. There are also some cryptocurrencies adopting DPoS such as BitShares, EOS, etc. The new version of EOS has turned DPoS to BFT-DPoS (Byzantine Fault Tolerance-DPoS).
> 
> ![DPoW](https://github.com/aridiosilva/Blockchain/blob/main/Fig.%203.%20Flow%20of%20DPoS..jpg)
> 
> - **PBFT (Practical Byzantine Fault Tolerance)**:
> 
>  PBFT is a Byzantine Fault Tolerance protocol with low algorithm complexity and high practicality in distributed systems [11]. PBFT contains five phases: request, pre-prepare, prepare, commit and reply. Fig. 4 describes how PBFT works. The primary node forwards the message sent by the client to the other three nodes. In the case that node 3 is crashed, one message goes through five phases to reach a consensus among these nodes. Finally, these nodes reply to the client to complete a round of consensus. PBFT guarantees nodes maintain a common state and take a consistent action in each round of consensus. PBFT achieves the goal of strong consistency, thus it is an absolute-finality consensus protocol. As mentioned before, EOS takes a combined consensus protocol. EOS leverages PBFT to simultaneously work with the block validation and creation in DPoS, greatly reducing the time required for a round of consensus [10]. A new protocol called Stellar is an improvement of PBFT. Stellar adopts FBA (Federated Byzantine Agreement) protocol, in which nodes can choose the federation they trust to conduct the consensus process [12].
>
> ![PBFT](https://github.com/aridiosilva/Blockchain/blob/main/Fig.%204.%20Process%20of%20PBFT..jpg)
> 
> - **Ripple**: 
> 
>   Ripple is an open source payment protocol [13]. In Ripple, transactions are initiated by clients and broadcast throughout the network via tracking nodes or validating nodes. However, the consensus process in Ripple is performed by validating nodes, each of which owns a list of trusted nodes called UNL (Unique Node List). Nodes in UNL can vote on the transactions they support. The process of consensus in Ripple is presented in Fig. 5. Each validating node sends its own transactions set as a proposal to other validating nodes. Once receiving the transaction proposals sent by nodes in UNL, the validating node will check each transaction in the proposal. The transaction in the proposal will get one vote if there is the same transaction in its local transactions set. When the transaction gets more than  of the votes, this transaction will enter the next round. The screening threshold will be increased for each round, and transactions with more than  of the votes will be finally recorded in the distributed ledger. Hence, Ripple is an absolute-finality consensus protocol.
>
> ![ripple](https://github.com/aridiosilva/Blockchain/blob/main/Fig.%205.%20Process%20of%20Ripple..jpg)
>
> - **Proof of Elapsed Time (PoET)**:
> 
>   Proof of Elapsed time is a network consensus protocol developed by the Intel Corporation. The algorithm is predominantly used in permissioned blockchain ledgers. The hardware used in PoET is specially designed for this protocol. For example, Intel Software Guarded Extension (SGX) is used in networks using PoET. This consensus protocol is used to allocate blocks to miners on the network. In permissioned blockchain systems, the miners’ identity is determined before allowing access int o the network. Therefore, anonymity is not a feature in this protocol. Each node in the network is assigned a random waiting time. The first node to complete the randomly chosen period validates the new block. The specialized hardware puts the processor to sleep during the wait time—this repeats over all the blocks in the network. he major disadvantage of this algorithm is its dependency on specialized hardware. This exposes it to various security vulnerabilities due to the lack of standardized and tried and tested protocols. IBMs Hyperledger Sawtooth supports PoET mechanism for custom blockchain applications development.
>
> - **Proof of activity (PoA)**:
> 
>   To avoid hyperinflation (what happens when too much of a currency floods the system) bitcoin will only ever produce 21m bitcoins. That means, at some point, the bitcoin block reward subsidy will end and bitcoin miners will only receive transaction fees. Some have speculated this might cause security issues resulting from a ‘tragedy of the commons‘, where people act in self-interest and spoil the system. So, proof of activity was created as an alternative incentive structure for bitcoin. Proof of activity is a hybrid approach that combines both proof of work and proof of stake. In proof of activity, mining kicks off in a traditional proof-of-work fashion, with miners racing to solve a cryptographic puzzle. Depending on the implementation, blocks mined do not contain any transactions (they are more like templates), so the winning block will only contain a header and the miner’s reward address. At this point, the system switches to proof of stake. Based on information in the header, a random group of validators is chosen to sign the new block. The more coins in the system a validator owns, the more likely he or she is to be chosen. The template becomes a full-fledged block as soon as all of the validators sign it. If some of the selected validators are not available to complete the block, then the next winning block is selected, a new group of validators is chosen, and so on, until a block receives the correct amount of signatures. Fees are split between the miner and the validators who signed off on the block. Criticisms of proof of activity are the same as for both proof of work (too much energy is required to mine blocks) and proof of stake (there is nothing to deter a validator from double signing). 
Decred is the only coin right now using a variation of proof of activity.
>
> - **Proof of Burn**:
> 
>   With proof of burn, instead of pouring money into expensive computer equipment, you ‘burn’ coins by sending them to an address where they are irretrievable. By committing your coins to never-never land, you earn a lifetime privilege to mine on the system based on a random selection process. Depending on how proof of burn is implemented, miners may burn the native currency or the currency of an alternative chain, like bitcoin. The more coins you burn, the better chance you have of being selected to mine the next block. Over time, your stake in the system decays, so eventually you will want to burn more coins to increase your odds of being selected in the lottery. (This mimics bitcoin’s mining process, where you have to continually invest in more modern computing equipment to maintain hashing power.) While proof of burn is an interesting alternative to proof of work, the protocol still wastes resources needlessly. Another criticism is that mining power simply goes to those who are willing to burn more money. The only coin that uses proof of burn is slimcoin, a cryptocurrency based on peercoin. It uses a combination of proof of work, proof of stake and proof of burn, but is only semi-active at this time.
>
> - **Proof of capacity**:
> 
>   As we’ve seen, most of these alternative protocols employ some type of pay-to-play scheme. Proof of capacity is no different, but here you ‘pay’ with hard drive space. The more hard drive space you have, the better your chance of mining the next block and earning the block reward. Prior to mining in a proof-of-capacity system, the algorithm generates large data sets known as ‘plots’, which you store on your hard drive. The more plots you have, the better your chance of finding the next block in the chain. By investing in terabytes of hard drive space, you buy yourself a better chance to create duplicate blocks and fork the system. But with proof of capacity, we still have the problem of nothing at stake to deter bad actors. Variations of proof of capacity include proof of storage and proof of space. Burstcoin is the only cryptocurrency to use a form of proof of capacity.
>
> - **Mining Diversity**: A round-robin, low-energy consumption protocol specifically designed for permissioned healthcare applications.31 Variations can be designed to suit various needs.
> 
> - **Kafka**: A voting-based, low-energy consumption protocol that can finalize the consensus decision faster (at least initially), but that requires more time as the number of nodes in the network grows.
> 
> - **Proof of Elapsed Time (PoET)**: A lottery-based, low-energy consumption protocol that can scale well for a network with many nodes while needing more time to reach consensus.
>
> - ** Comparison of Main Consensus Protocols
>  
> ![table Comparison Consensus Protocols](https://github.com/aridiosilva/Blockchain/blob/main/Table%201%20-%20%20Main%20Concensus%20Protocols%20Comparison_5_Cases_.jpg)
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

These offer reusable blockchain platforms, solutions based on technical standards. Mainly these have multipurpose use cases. Ex: Hyperledger

## Dual-Focused

Here, they focus on both technology and business when offering a platform or solution: EX: RS

![Top-Blockchain-Consortuim](https://github.com/aridiosilva/Blockchain/blob/main/Top-Blockchain-Consortuim_.png)

# What Would Blockchain Consortium Offer 

## Cutting the costs

Blockchain industry consortium architecture would help you cut all the expenses quite effortlessly. As these are mainly suited for industrial purposes, you can easily link these up with your existing network more efficiently than public or private Blockchain.

So, investing in this kind of blockchain industrial consortium would be highly beneficial for your enterprise.

## Very Low Transaction Fees

Another significant aspect of this blockchain industry consortium is that they can give a lower transactional fee. You have to know that public blockchains do claim to offer similar features; however, the reality is quite far from it.

In reality, when many users start to use the network, it starts to slow down drastically. Thus, transaction processing becomes harder than usual. When something like this happens, the transactional fee rises.

You have to know that in terms of the consortium, this is not the issue. It’s a more controlled environment, and only permissioned people can get in. So, that means it would be much more stable and can handle any pressure.

## Regulatory Environment

Enterprises need regulations to function properly. And most importantly, as many organizations would work here together, there need to be certain rules. Thus, a blockchain industry consortium can help you flourish in a regulated environment and also give them freedom of decentralization.

## No Criminal Entry

Obviously, you would want to stay far away from criminals in a collaborative environment. Unlike a public blockchain, only authorized persons can get into this kind of network. And so, every node would be authenticated and wouldn’t leave any scope for criminals.

# What Benefits Should You Expect from Blockchain Consortium?

There are certain benefits that you should expect from the federated Blockchain. Let’s see what these are –

## Cost Savings

You need to consider whether the federated Blockchain would save your costing. The basic idea of being a member is to cut expenses. So, choose the one that offers the most cost-saving features for your industry.

## Accelerate Learning

Another great benefit to expect from the federated Blockchain. To grow in the blockchain niche, you’d need full support in learning. So, expecting to accelerate learning methods would be beneficial. Many consortia offer training and other development support form experts. Opportunities like that can really nurture your team, as well.

## Sharing Risk

Well, another benefit of federated Blockchain is to share risk. So, you would definitely want a platform where every single company would share the risk in case of a new blockchain solution. As Blockchain is still new, there’s a lot of risks associated with it in the marketplace. But if members collaborate, then the overall risk is much lower whether the solutions fail or succeed.

## Build Critical Mass of Adoption

Just building only one single solution shouldn’t be the case for federated Blockchain. Taking it on a mass adoption level would help your company to reach a new height easily. Without mass adoption, reaching the global marketplace would become tough.

## Maintaining Relevance/Lifespan

Your consortium needs to offer a relevant solution or roadmap plan. As the technology keeps changing, staying relevant in the field is extremely tough. Thus, as the time will change, you should expect your consortium to change their plan according to that as well.

## Influencing Standards

Lastly, you should expect the consortium to offer influencing standards. According to the market, Blockchain would soon reach interoperability. You would need to influence standards to mark your place in that trillion dollars’ worth industry.

# Major Blockchain Consortia and Networks

These are some of the major Blockchain Consortia and Networks in the market. All these consortia seem to have a lot of companies using blockchain technology. So, let’s check out how what these consortia are:

> - **1) Hyperledger**
>
>   Let’s start with Hyperledger. Hyperledger blockchain is one of the most prominent blockchain consortia in the market right now. Just starting its journey back in 2016, Linux founded Hyperledger. In reality, this consortium can be one of the best open-source platforms for enterprises. Why? Well, it’s because Hyperledger offers tons of solutions, and they’re mainly focused on providing technological support for the blockchain revolution. At present, they have a large number of projects, including tools, platforms, libraries, and many more. >Using these, you can quickly develop your very own blockchain platforms at ease. At present, they have 260+ members in their consortium.
>
> - **2) Enterprise Ethereum Alliance**
>
>  It’s another worthy consortium for our blockchain consortium list. Vitalk Buterin actually is the original founder of Ethereum. However, as the original Ethereum is a public blockchain, they decided to roll out an enterprise-grade one as well. >Furthermore, this new one would let you get privacy in terms of transactions and many added facilities. At present, Enterprise Ethereum has over 250+ members collaborating together. Innovation is their main priority, and they tend to offer a great environment for nurturing as well.
>
> - **3) R3**
>
>  Blockchain consortium r3 is actually the oddball in the blockchain consortium list. How? Well, this is one of the dual-focused consortia at present. Not only blockchain consortium r3 have an open-source version of their platform Corda, but they also offer a commercial one for enterprises. Another great deal is that both platforms are compatible with each other. So, switching between them would be an easy task. At present, blockchain consortium r3 has an ecosystem of 200+ members and growing. However, we have to say, their tech is more geared for financial niches. But blockchain consortium r3 is slowly trying to reach other use cases as well. Many major names are already pursuing blockchain consortium r3 at present.
>
> - **4) BankChain**
>
>   BankChain is actually a banking blockchain consortium where they are implementing, building, and exploring different blockchain solutions. However, the formation of this blockchain consortia started from Primechain technologies. In reality, they are the ones responsible for maintaining, governing, and operating the system. Furthermore, they started their journey back in 2017 with 9 live projects and 34 members. Some of their products include – Invoice discounting, Bank guarantees & Documentary Credits, Corporate KYC and Charge Registry, and many more.
>
> - **5) B3i**
>
>   B3i is the next one on our banking blockchain consortium list. In 2016, the Blockchain Insurance Industry Initiative started its journey with reinsurers and insurers. At that time, they only wanted to explore the Distributed Ledger Technology and figure out the potential benefits. However, they later expanded its product line and now offer a lot of insurance-based solutions. One of them is – Property Cat XOL contract. At present, they have about 18 members.
>
> - **6) IBM Food Trust**
>
> A large part of our lives revolves around food, and Blockchain can help bring safety in this field. Apparently, IBM Food Trust offers the largest ecosystem of suppliers, producers, manufacturers, retailers, and many more. At present, they have over 80 members on their list, and there are some major giant names such as Walmart, Nestle, Unilever, and many more. And so, with help from their platforms, enterprises can track their food supply chain from the very suppliers to consumers.
>
> - **7) China Ledger**
>
>    China Ledger is a blockchain consortium launched in China. In reality, they launched the consortium to explore and understand this tech’s impact on their economy. Moreover, they are also exploring different encryption algorithms, sidechains, private chains, and many other network techs. Wanxiang Blockchain Labs is leading the alliance now. It also consists of eleven other commodity exchanges, financial asset exchanges, and equity exchanges. More so, they want to build solutions and platforms for their very own financial sectors in China later in the future.
>
> - **8) FISCO – Financial Blockchain Shenzhen Consortium**
>
>   Established on May 31, 2016, Financial Blockchain Shenzhen Consortium now has over 100 members in their consortium. As you can see by the name, they focus mainly on financial industries. And so, all of their members consist of financial information services companies and institutions. More so, FISCO already has projects in equity, credit, insurance, cloud service, loyalty points system, digital assets, and many more. However, the platform is actually open-source. China is starting to catch up in the blockchain niche, and FISCO happens to be the result of that. So, this is another blockchain for insurance consortium.
>
> - **9) Global Shipping Business Network**
> 
>   Global Shipping Business Network formed a group of nine terminal operators and ocean carriers. After that, they launched their open platform based on Blockchain. In reality, CargoSmart is the first to initiate this consortium. At present they have – OOCL, PSA International and Shanghai International Port, Evergreen Marine, COSCO Shipping Lines, Hutchison Ports, DP World, Yang Ming, and CMA CGM. CargoSmart is actually a solution provider. Moreover, the solution would offer a digital platform to connect shippers, custom agencies, logistics, carriers, and many more. So, it’s also a blockchain for supply chain consortium.
>
> - **10) Tradelens**
>
>   Tradelens is the next one on our supply chain blockchain consortium list. They are here to revolutionize the supply chain management world. It’s actually a neutral and open industry platform based on Blockchain, and many major players in the market are backing it up. At present, they have over 100 enterprises in their ecosystem. More so, it mainly includes ports, carriers, shippers, 3PLs, terminal operators, and freight forwarders. Thus, coming together under a single platform, they digitise everything related to the supply chain. If you are curious about how Blockchain can positively impact the world of the supply chain and management operations, you must enroll in our enterprise blockchains and supply chain management course now!
>
> - **11) Energy Web Foundation**
>
>   The Energy Web Foundation is taking the lead in the energy sector of a blockchain consortium. More so, they claim to be the pioneer for this enterprise blockchain for ensuring the sector’s market, operational, and regulatory needs. At present, they have over 100+ members in their ecosystem. If you’re in the energy sector, then you can definitely check it out. Energy Web Foundation also offers a lot of flexible opportunities for the members.
>
> - **12) Hashed Health Collective**
>
>   When all the other consortia are taking over the marketplace, why would the healthcare sector be left behind, right? Thus, comes the Hashed Health Collective. This Blockchain for healthcare consortia is a global community of developers, consumers, healthcare organizations, or anyone who is working in the healthcare niche. It’s an open platform and nonprofit community where they nurture new innovations and ideas based on Blockchain. Anyhow, we couldn’t find the exact number of members of their ecosystem; however, ODH, Change Healthcare, Accenture, PLC, Altarum Institute, and many more happen to be on the list.
>
> - **13) Health Utility Network**
>
>    Even though it’s fairly new, till Health Utility Network is creating a lot of hype in the market. In reality, IBM, Aetna, PNC Bank, Anthem, and Health Care Service Corporation (HCSC) is collaborating to create this consortium ecosystem for healthcare sectors. Moreover, their primary goal is to improve the traceability and interoperability of the healthcare industry. As IBM is in the mix, we can safely assume that the platform would be based on Hyperledger Fabric. Anyhow, according to the, they’ll be launching a series of solutions to help grow the sector.
>
> - **14) Contour**
>
>    Contour blockchain is one of the pioneers of blockchain consortia. In reality, their project is focused on financial sectors. More so, they’ll be using R3’s technology to back up their blockchain platform. The primary goal is to digitize every single document in the financial sectors. After that, they can start to launch a series of solutions. 
At present, they have twelve banks in their ecosystem. They include – Mizuho, Scotiabank, BNP Paribas, CTBC bank, Bangkok Bank, ING, Intesa Sanpaolo, Natwest, SEB, U.S Bank, BBVA, and HSBC.
>
> - **15) Marco Polo**
>
>    Marco Polo is another great one in our blockchain consortium list. They launched in 2017 and mainly focused on the trade finance blockchain niche. Primarily, they are aiming to offer capital finance availability in their solution TradeIX platform. More so, they are building the solution of r3 Corda. Multiple financial sectors such as SMBC, Bangkok Bank, ING, Standard Chartered Bank, BNP Paribas, Forfaiting Association (ITFA), NatWest, OP Financial Group, Natixis, Commerzbank, DNB, and International Trade is a major part of the ecosystem.
>
> - **16) We.trade**
>
>   We.trade, making it easy for consumers to connect with potential sellers and vendors and manage all the payments and orders. Furthermore, every single business on the Blockchain is KYC. So, there’s no issue of fraud or corruption. Another great aspect of this blockchain consortium is that it helps to select different banking products as well. The banks within the ecosystem also offer guarantees of payments. At present, they have eight banks under the platform. Batavia was one of the smallest blockchain consortia so far. They have only five members in their ecosystem. For their technological backup, they are seeking help from IBM. These five banks are –
>
> - **17) Commerzbank, Bank of Montreal, Erste Group, UBS, and CaixaBank**
>
>   Batavia focuses on border blockchain applications, such as using smart contract features for any financial solution. With the help, you can track your cross-border payment and send or receive payments at ease. However, Batavia has merged with We.Trade and doesn’t exist anymore now. 
>   
> - **18) MOBI**
>
>   Mobility Open Blockchain Initiative is a nonprofit consortium based on Blockchain. It consists of forward-thinking NGOs, companies, and governments to ensure mobility services that are safe and affordable. Additionally, they also offer greener, efficient, and less congested solutions with the typical standards of Blockchain. They started with vehicle identities and would soon cover other mobility sectors as well. At present, they have 87 members.
>
> - **19) Trusted IoT Alliance (TIA)**
>
>    The IoT sector is in greater need of trust. Thus, came the Trusted IoT Alliance to save the day. In reality, they aim to make the IoT industry more reliable and induce readability. That’s why they are incorporating IoT sensors with smart contracts to facilitate a digital tracing environment.  Another great benefit is that they offer full freedom when it comes to innovations. So, you’ll get the best tools to develop your new project. At present, they have 42 members.
>
> - **20) Japan Exchange Group — JPX**
>
>   Various Japanese financial and IT institutions formed this blockchain consortium called Japan Exchange Group. Currently, they have 44 members, and all of them are financial or IT companies. But what is the primary goal?  Well, they want to develop solutions for the capital markets. Furthermore, some of their projects are underway. These include - KYC Operations, Trade Matching Processes, Pre-Settlement Process of Cross-Border Securities Trade and etc.
>
> - ** Conclusion Thoughts about Blockchain Consortia
>
>  In the end, blockchain consortia are really changing the way the marketplace operated all these years. Instead of competition, they are collaborating to make the world a better place. In case you want to develop your very own enterprise solution, you can start by joining a consortium where your ideas would be nurtured.

In this guide, we’ve listed the top 20 blockchain consortium. Check them out and pick the one that suits your needs. If you want to learn about this type of Blockchain in more depth, then we recommend starting with our free blockchain course.

# History of Blockchain Technology

Blockchain technology has to be one of the biggest innovations of the 21stcentury given the ripple effect it is having on various sectors, from financial to manufacturing as well as education. Unknown to many, is that the history of Blockchain dates back to the early 1990s.

Since its popularity started growing a few years back, a number of applications have cropped up all but underlining the kind of impact it is destined to have as the race for digital economies heat up. In this discussion, we’ll learn about the history of Blockchain with Blockchain evolution.

### History of Blockchain Technology – Timeline Infographic

It is important to know about the history of Blockchain for Blockchain enthusiasts and Blockchain aspirants. So, to help our reader know the Blockchain history and understand the Blockchain evolution, here we bring a detailed guide to the history of blockchain technology with its detailed evolution.

### 1991-2008: Early Years of Blockchain Technology

How did blockchain emerge? Stuart Haber and W. Scott Stornetta envisioned what many people have come to know as blockchain, in 1991. Their first work involved working on a cryptographically secured chain of blocks whereby no one could tamper with timestamps of documents.

In 1992, they upgraded their system to incorporate Merkle trees that enhanced efficiency thereby enabling the collection of more documents on a single block. However, it is in 2008 that Blockchain History starts to gain relevance, thanks to the work one person or group by the name Satoshi Nakamoto.

Satoshi Nakamoto is accredited as the brains behind blockchain technology. Very little is known about Nakamoto as people believe he could be a person or a group of people that worked on Bitcoin, the first application of the digital ledger technology.

Nakamoto conceptualized the first blockchain in 2008 from where the technology has evolved and found its way into many applications beyond cryptocurrencies. Satoshi Nakamoto released the first whitepaper about the technology in 2009. In the whitepaper, he provided details of how the technology was well equipped to enhance digital trust given the decentralization aspect that meant nobody would ever be in control of anything.

Ever since Satoshi Nakamoto exited the scene and handed over Bitcoin development to other core developers, the digital ledger technology has evolved resulting in new applications that make up the blockchain History.

A very common question, when was blockchain invented? we see can say Blockchain was invented in 1991.

### Blockchain Structure

In simple terms, Blockchain is a peer-to-peer distributed ledger that is secure and used to record transactions across many computers. The ledger’s contents can only be updated by adding another block linked to the previous block. It can also be envisioned as a peer-to-peer network running on top of the internet.

In layman or businesses term, blockchain is a platform where people are allowed to carry out transactions of all sorts without the need for a central or trusted arbitrator.

The created database is shared among network participants in a transparent manner, whereby everyone can access its contents. Management of the database is done autonomously using peer-to-peer networks and a time stamping server. Each block in a blockchain is arranged in such a way that it references the content of the previous block.

The blocks that form a blockchain hold batches of transactions approved by participants in a network. Each block comes with a cryptographic hash of a previous block in the chain.

Read our previous article Ultimate Blockchain Guide to know more about blockchain technology.

## Evolution of Blockchain: Phase 1- Transactions

### 2008-2013: Blockchain 1.0: Bitcoin Emergence

Most people believe that Bitcoin and Blockchain are one and the same thing. However, that is not the case, as one is the underlying technology that powers most applications of which one of them is cryptocurrencies.

Bitcoin came into being in 2008 as the first application of Blockchain technology. Satoshi Nakamoto in his whitepaper detailed it as an electronic peer-to-peer system. Nakamoto formed the genesis block, from which other blocks were mined, interconnected resulting in one of the largest chains of blocks carrying different pieces of information and transactions.

Ever since Bitcoin, an application of blockchain, hit the airwaves, a number of applications have cropped all of which seek to leverage the principles and capabilities of the digital ledger technology. Consequently, blockchain history contains a long list of applications that have come into being with the evolution of the technology.

> More and more organizations are joining the digital transformation revolution with the adoption of blockchain technology. Read our previous blog to understand how will blockchain change organizations.

Buterin differentiated Ethereum from Bitcoin Blockchain by enabling a function that allows people to record other assets such as slogans as well as contracts. The new feature expanded Ethereum functionalities from being a cryptocurrency to being a platform for developing decentralized applications as well.

Officially launched in 2015, Ethereum blockchain has evolved to become one of the biggest applications of blockchain technology given its ability to support smart contracts used to perform various functions. Ethereum blockchain platform has also succeeded in gathering an active developer community that has seen it establish a true ecosystem.

Ethereum blockchain processes the most number of daily transactions thanks to its ability to support smart contracts and decentralized applications. Its market cap has also increased significantly in the cryptocurrency space.

## Evolution of Blockchain: Phase 2- Contracts

### 2013-2015: Blockchain 2.0: Ethereum Development

In a world where innovation is the order of the day, Vitalik Buterin is among a growing list of developers who felt Bitcoin had not yet reached there, when it came to leveraging the full capabilities of blockchain technology, as one of the first contributors to the Bitcoin codebase.

Concerned by Bitcoin’s limitations, Buterin started working on what he felt would be a malleable blockchain that can perform various functions in addition to being a peer-to-peer network. Ethereum was born out as a new public blockchain in 2013 with added functionalities compared to Bitcoin, a development that has turned out to be a pivotal moment in Blockchain history.

Buterin differentiated Ethereum from Bitcoin Blockchain by enabling a function that allows people to record other assets such as slogans as well as contracts. The new feature expanded Ethereum functionalities from being a cryptocurrency to being a platform for developing decentralized applications as well.

Officially launched in 2015, Ethereum blockchain has evolved to become one of the biggest applications of blockchain technology given its ability to support smart contracts used to perform various functions. Ethereum blockchain platform has also succeeded in gathering an active developer community that has seen it establish a true ecosystem.

Ethereum blockchain processes the most number of daily transactions thanks to its ability to support smart contracts and decentralized applications. Its market cap has also increased significantly in the cryptocurrency space.

## Evolution of Blockchain: Phase 3- Applications

### 2018: Blockchain 3.0: the Future

Blockchain History and evolution does not stop with Ethereum and Bitcoin. In recent years, a number of projects have cropped up all leveraging blockchain technology capabilities. New projects have sought to address some of the deficiencies of Bitcoin and Ethereum in addition to coming up with new features leveraging blockchain capabilities.

Some of the new blockchain applications include NEO, billed as the first open-source, decentralized, and blockchain platform launched in China. Even though the country has banned cryptocurrencies, it remains active when it comes to blockchain innovations. NEO casts itself as the Chinese Ethereum having already received the backing of Alibaba CEO Jack Ma as it plots to have the same impact as Baidu in the country.

In the race to accelerate the development of the Internet of Things, some developers, so it fit, to leverage blockchain technology and in the process came up with IOTA. The cryptocurrency platform is optimized for the Internet of things ecosystem as it strives to provide zero transaction fees as well as unique verification processes. It also addresses some of the scalability issues associated with Blockchain 1.0 Bitcoin.

In addition to IOTA and NEO, other second-generation blockchain platforms are also having a ripple effect in the sector. Monero Zcash and Dash blockchains came into being as a way of addressing some of the security and scalability issues associated with the early blockchain applications. Dubbed as privacy Altcoins, the three blockchain platform seek to provide high levels of privacy and security when it comes to transactions.

The blockchain history discussed above involves public blockchain networks, whereby anyone can access the contents of a network. However, with the evolution of technology, a number of companies have started adopting the technology internally as a way of enhancing operational efficiency.

Large enterprises are investing big in hiring professionals as they seek to gain a head start on the use of technology. Companies like Microsoft and Microsoft appear to have taken the lead when it comes to exploring blockchain technology applications resulting in what has come to be known as private, hybrid, and federated blockchains.

## 2015: Hyperledger

In 2015, the Linux Foundation unveiled an Umbrella project of open-source blockchain. They went on to call it Hyperledger, which until to date acts as collaborative development of distributed ledgers. Under the leadership of Brian Behlendorf, Hyperledger seeks to advance cross-industry collaboration for the development of blockchain and distributed ledgers.

Hyperledger focuses on encouraging the use of blockchain technology to improve the performance and reliability of current systems to support global business transactions.

## 2017: EOS.IO

EOS brainchild of private company block.one came into being in 2017, on the publishing of a white paper detailing a new blockchain protocol powered by an EOS as the native cryptocurrency. Unlike other blockchain protocols, EOS tries to emulate attributes of real computers including CPU and GPU.

For that reason, EOS.IO doubles up as a smart contract platform as well as a decentralized operating system. Its main purpose is to encourage the deployment of decentralized applications through an autonomous decentralized corporation.

## 2020: Blockchain History & The Future

The future of Blockchain technology looks bright, in part, because of the way governments and enterprises are investing big as they seek to spur innovations and applications. It is becoming increasingly clear that one day there will be a public blockchain that anyone can use.

Advocates expect the technology to help in the automation of most tasks handled by professionals in all sectors. The technology is already finding great use in supply management as well as in the cloud computing business. The technology should also find its way into basic items such as search engines on the internet in the future.

As the technology evolves, Gartner Trend Insights expects at least one business built on blockchain to come into being valued at more than $10 billion by 2022. Due to the Blockchain Digital Transformation, the research firm expects the business value to grow to over $176 billion by 2025 and exceed the $3.1 trillion by 2030.

The evolution of Blockchain Technology in recent years has increased the demand for Blockchain professionals. the companies are also implementing Blockchain to get benefits of the Blockchain applications. So, if you are aspiring to build a career in Blockchain, it’s the right time to start it with the Free Blockchain Course.

## What is a blockchain?

> **A blockchain is a special type of database. Transactions are not governed by a single party, but rather the entire transaction history is recorded in a decentralised, > distributed ledger**.

Blockchains offer groundbreaking technology with the potential to change the internet and even the world for many reasons. As we dive deeper into how blockchains work, you will find it increasingly easy to understand exactly why.

## Blockchain & distributed ledger origins

In a traditional marketplace, middlemen oversee the exchange of assets. When you receive your paycheck, for example, a bank controls the transaction. The bank validates the check, verifies that the employer holds the required funds in their account, and records the exchange. This record, or ledger, documents the transaction and the resulting change in wealth; you can look at your bank statement and see that you’re a little bit richer. For most transactions, a central entity like a bank has sole power over this ledger.

While giving control of our transactions to a central power requires a great deal of trust, it has historically been the best method for ensuring the security of the ledger. Imagine, for instance, that your employer owned the ledger instead of the bank. Your employer could falsely claim that they paid you and manipulate the records to back up their lie. Because of this security risk, neither participant in the exchange should be given sole control of the ledger. For most of history, the best way to avoid this kind of fraud was to entrust an unbiased intermediary with the ledger and hope that this middleman would faithfully maintain the ledger. In other words, traditionally, two parties who agreed upon a transaction relied on a third-party institution to carry out and record the exchange.

However, central ledgers are no longer the only viable option for exchanging our assets. Now, due to the advent of distributed ledger technologies, we can safely get our paychecks without needing to trust a bank.

![distributed_ledgers_explained](https://github.com/aridiosilva/Blockchain/blob/main/distributed_ledgers_explained.png)

## Distributed Ledgers (DLTs) explained

Distributed ledger technologies, like blockchain, are peer-to-peer networks that enable multiple members to maintain their own identical copy of a shared ledger. Rather than requiring a central authority to update and communicate records to all participants, DLTs allow their members to securely verify, execute, and record their own transactions without relying on a middleman.

While there are a wide variety of DLTs on the market, they are all comprised of the same building blocks: a public or private / permissioned / permissionless distributed ledger, a consensus algorithm (to ensure all copies of the ledger are identical), and a framework for incentivizing and rewarding network participation.

## Public vs. Private and Permissioned vs. Permissionless

Distributed ledgers are categorized as “private” or “public” and “permissioned” or “permissionless” — they can be any combination of any of the two. To achieve full decentralization, Hedera believes distributed ledgers must public permissionless networks.

![path_to_decentralization](https://github.com/aridiosilva/Blockchain/blob/main/path_to_decentralization_.png)

### Private / Permissioned: 

This type of network offers no decentralization. The applications and the network nodes running those application must both be invited to join the network and meet certain criteria or provide a form of identification. Any party can also be removed without warning at any time.

### Private / Permissionless: 

Requires that applications deployed in production be invited to join the network and can be removed without warning at any time. The nodes which constitute the network and run said applications can freely and anonymously join and contribute, typically in exchange for a network’s native cryptocurrency.

### Public / Permissioned: 

Allows applications to be deployed in production or removed, without having to notify anyone, reveal their identity, or meet any application criteria requirements. The nodes which constitute the network and run said applications must be invited to join the network.

### Public / Permissionless: 

This type of network is the most decentralized. Applications can be deployed in production or removed, without having to notify anyone, reveal their identity, or meet any application criteria requirements. Additionally, the nodes which constitute the network can freely and anonymously join and contribute, typically in exchange for a network’s native cryptocurrency.

## Reaching consensus

Although every node on a permissioned or permissionless distributed ledger maintains and updates their own copy of the ledger, it is imperative that each of these ledgers remains identical. Imagine, for instance, that your copy of the ledger reveals that you have $100 in your account, while the cashier’s ledger holds that you have $1. This discrepancy would make it very difficult, if not impossible, to buy a candy bar. Without identical ledgers, participants in the network could not make transactions.

In order to keep the distributed ledger consistent, DLTs must have a consensus algorithm, or a method of ensuring that all copies of the ledger agree. A consensus algorithm is a method of synchronizing the data across a distributed system. In the case of a DLT, the consensus algorithm ensures that all copies of the ledger are identical.

There are many different consensus algorithms on the market, each with different advantages. Perhaps the most intuitive algorithm is a simple vote. According to this algorithm, each node independently calculates how they think they should update their ledger based on the information available to them. Then, each node sends this information to every other node. At this point, every node in the network has access to their decision and every other node’s decision. The nodes then calculate the majority or plurality vote, and they all update their ledgers according to this democratic consensus.

Although the simple vote is effective and intuitive, it is not efficient at scale. Because every node must send their vote to every other node, the bandwidth and processing power required to come to consensus grows exponentially with the size of the network. In other words, every additional node dramatically decreases the efficiency of the network. Because DLTs become more secure and transparent when more nodes are added to the network, many other consensus algorithms have been developed to better suit the need for large, efficient, and reliable peer-to-peer networks.

If you are curious about other consensus algorithms, you can learn about them by visiting the following pages within the learning center: voting-based consensus, economy-based consensus, and more coming soon.

## Cryptocurrency and compensating network participants

To carry out their consensus algorithms, DLTs require a significant amount of processing power per transaction. Just as DLTs distribute the responsibility of maintaining the ledger to each participant, so do they divide this computational burden. Every node must donate computing power to run the consensus algorithm and process transactions. Of course, computing power is not free.

To compensate participants for their work, and incentivize further participation, DLTs typically reward active membership with cryptocurrency. Cryptocurrency is a virtual, encrypted token which can be exchanged using across a decentralized network. These coins can be exchanged, purchased, or earned by participating in the network.

While cryptocurrencies have no inherent value (much like fiat currency), they may be valuable to participants in a network because they are necessary for performing actions quickly, securely, and cost effectively across the decentralized network. Their usefulness as currency generates a demand for these coins. Therefore, participants have an incentive to contribute computational resources to the network. Not only is their work rewarded in cryptocurrency, the value of that currency may rise as the network grows and more build useful applications on the distributed ledger platform.

## Main Characteristics and Properties of Blockchain 

### (1) Each node contains a complete image of a blockchain’s network

Who can be trusted in a digital space, where everything can easily be copied and most users are anonymous? Blockchain can help to solve this pressing question.

### (2) A blockchain is not updated and validated by a single individual, but by hundreds, thousands, or even millions of community members in regular timeframes.

Instead of one central party such as a company, government or bank, the entire blockchain network agrees on a shared “reality”, i.e. complete history of every transaction that has ever taken place within the network. This agreement is called consensus.

### (3) Because every single transaction that has ever taken place within the network is recorded and permanently stored, it is not possible to change the ledger’s history or send the same transaction twice

This certainty creates mutual trust. In other words, participants of a blockchain network don’t even have to trust each other because no single user can cheat the system as a whole. Blockchain technology is suitable for transactions between parties that need to be verifiable and permanent, such as contracts, ownership of intellectual property, 
identification, and, of course, cryptocurrencies like Bitcoin.

## Why are distributed ledger technologies useful?

Distributed ledger technologies allow businesses and individuals alike to quickly carry out secure transactions without needing to rely on a middleman. By avoiding intermediaries, distributing control of the ledger, and providing a tamper-apparent network, DLTs present a more cost-efficient, accessible, and reliable transaction platform than centralized ledger systems.

![distributed_ledger_uses](https://github.com/aridiosilva/Blockchain/blob/main/distributed_ledger_uses.png)

## Remove the middleman

Because central ledgers rely on intermediaries, they are burdened by the costs and inefficiencies of the middleman. DLTs do away with these limitations by avoiding middlemen and intermediaries altogether. Without a central agent, there is no need to pay a central agent. And, without the need for clunky bureaucracy, you can exchange assets directly and immediately. You no longer have to limit the speed of your transaction to the efficiency of expensive bankers, lawyers, or politicians.

Moreover, you no longer have to trust bankers, lawyers, or politicians with the ledger and your assets. DLTs are trustless systems, meaning that no participant needs to trust any other participant to guarantee a valid ledger.

## Accessibility

While centralized systems monopolize control and limit access to their ledger, DLTs provide a much more accessible service. DLTs allow businesses and individuals to carry out transactions freely, without relying or trusting any other individual. Public DLTs take this further by issuing no restrictions on transactions or participation; no one can be denied from the platform, and no transaction will be treated with priority over another.

## Tamper-apparent

Traditional ledgers may provide fast and simple record-keeping, but they are vulnerable to corruption and hacking. Because only one central entity controls the ledger, a corrupt central agent can tamper with the records without the consent or knowledge of the affected members. Moreover, because there is only one copy of the ledger, hackers have a clear, single target for their attacks. Without visibility into whether tampering has occurred, we must simply trust that the central third-party is neither corrupt nor compromised when we use a centralized ledger.

Distributed ledgers, however, are inherently resistant to tampering. While a malicious agent could compromise a central system by altering the single ledger, they would need to alter at least a plurality of ledgers to have an impact on a distributed system.

Though DLTs are not tamper-proof, they are tamper-apparent. That is, if tampering does occur, the network’s transparency ensures that all members of the network will be aware of the change. Though a participant of a DLT cannot be completely certain that the ledger will remain unaltered, they can rest assured that they will know if tampering does occur.

Hedera Hashgraph has achieved the gold standard of security in distributed ledger consensus mechanisms, which is asynchronous Byzantine fault tolerance (aBFT) and is the only distributed ledger to-date which has formally proven this quality. Hedera guarantees consensus, in real time, and is resistant to Distributed Denial of Service (DDoS) attacks, an area of vulnerability for some public ledger platforms.

## Immutability and controlled mutability

Some distributed ledgers take security beyond tamper-apparent by establishing immutability, preventing any and all participants from changing established records for any reason. Members of these immutable DLTs can only view the ledger and carry out new transactions. Even if all participants in the network wished to change the ledger, there would be no pathway within the system’s architecture for that change to occur. Therefore, participants of an immutable distributed ledger can be certain that their ledger is not only tamper-apparent, but tamper-proof. A distributed ledger technology is immutable if it does not provide any participant or group of participants the ability to alter or delete established records.

Of course, immutability does come with downsides. In some cases, changing past records could be beneficial. For instance, if a bug in the DLT’s code causes a transaction to be misrepresented in the ledger, immutability would prevent anyone from fixing that problem. The invalid transaction would forever be part of the official ledger. Additionally, as laws change to catch up with technology, new government regulations may necessitate a change in record-keeping practices. Immutable systems would not be able to adapt to these changing legal conditions, and would therefore risk violating government standards.

Recognizing the downsides of both mutability and immutability, some DLTs opt for controlled mutability. DLTs with controlled mutability allow records to be changed, but place heavy restrictions upon that pathway.

Controlled mutability is the best of both worlds: no malicious participant or group of participants can alter the records without everyone knowing (tamper-apparent), but the DLT can adapt to bugs and changing regulations. Hedera Hashgraph is one example of a DLT with controlled mutability. 

## How do blockchains work?

> To ensure that the network’s transaction history is not manipulated by anyone, the community behind the network has to agree on a common “reality”.
 
In a blockchain, transactions are stored in blocks, with each newly generated block referring to the block before it with a unique identifying number called a “hash.”

These blocks constitute a chain, hence the name “blockchain”. This chain continues on indefinitely. In the case of blockchains such as Bitcoin, trust is based on technological features such as the fact that all blocks can be viewed by the public. No transaction is added to a block without first being verified by a miner - a special type of computer in the network. This way the community ensures that no fraudulent transaction is recorded in a blockchain. Consequently, a blockchain can even be used by parties who don’t necessarily trust each other to do business because they know their transactions are tamper-proof.

# What is a Node in a Blockchain Network?

Because nodes are a critical component of a blockchain’s infrastructure. Without nodes, a blockchain’s data would not be accessible. You could say that nodes are the blockchain.

A blockchain exists out of blocks of data. These blocks of data are stored on nodes (compare it to small servers). Nodes can be any kind of device (mostly computers, laptops or even bigger servers). Nodes form the infrastructure of a blockchain. All nodes on a blockchain are connected to each other and they constantly exchange the latest blockchain data with each other so all nodes stay up to date. They store, spread and preserve the blockchain data, so theoretically a blockchain exists on nodes. A full node is basically a device (like a computer) that contains a full copy of the transaction history of the blockchain.

# What do Nodes do?

When a miner attempts to add a new block of transactions to the blockchain, it broadcasts the block to all the nodes on the network. Based on the block’s
legitimacy (validity of signature and transactions), nodes can accept or reject the block. When a node accepts a new block of transactions, it saves and stores it on top
of the rest of the blocks it already has stored. In short, here is what nodes do:

1) Nodes check if a block of transactions is valid and accept or reject it.
1) Nodes save and store blocks of transactions (storing blockchain transaction history).
2) Nodes broadcast and spread this transaction history to other nodes that may need to synchronize with the blockchain (need to be updated on transaction history).

# Difference between a Miner and a Node

A miner always needs to run a full node in order to select valid transactions to form a new block. Without a full node it cannot determine what proposed transactions are valid according to the current blockchain’s transaction history (aka if all balances involved in the transactions are sufficient enough to perform the proposed transactions), because it does not have access to the full blockchain history. Therefore, a miner is always also a full node. A node however, is not necessarily simultaneously a miner. A device can run a full node by receiving, storing and broadcasting all transaction data (much like a server) without actually creating new blocks of transactions itself. In this case it functions more like a pass point with a directory, whereas a miner is the same but simultaneously tries to create new blocks of transactions as well.

# Definition of a node in blockchain:* **A full node is a full copy of the blockchain transaction history on any device.**

# How Nodes secure the Blockchain

Nodes can be online or offline. Online nodes are receiving, saving and broadcasting all the latest blocks of transactions from and to other nodes, while offline nodes do
not. When an offline node comes back online, it will need to catch up with the rest of the blockchain first by downloading all blocks that were added to the blockchain
ever since the node went offline. This process is often referred to as synchronizing with the blockchain.

An entire blockchain can theoretically run on a single node, but since it would be stored on only a single device, it would be extremely vulnerable to things like power 
outages, hackers or systemic crashes. The more full nodes a blockchain is running on, the better its resilience against such catastrophes is. When the blockchain data
is spread across so many devices, it will be very hard for a corrupt entity to wipe out all this data at once. Even if a large number of nodes suddenly goes offline and
becomes inaccessible because of a global crisis, a single node can theoretically keep an entire blockchain operational. And even if all nodes go offline, it only takes one
node with the full blockchain history to come back online to make all the data accessible again.

# Who can run a Node?

Some blockchains have thousands of nodes simultaneously online. Anyone can runa node by simply downloading the transaction history of a blockchain. Many crypto and blockchain enthusiasts are running nodes voluntarily. They do this to contribute to a blockchains community, its development, security and integrity, but also simply becau se it’s their hobby and makes them feel part of the project. 

Running a node is considered fairly simple for someone slightly tech savvy, and does not require a lot of resources. Some blockchains however, now contain such a large amount of transaction data that it actually requires a lot of memory on a device to run a full node. Many crypto users who just want to use a blockchain therefore use wallet applications. These applications allow them to broadcast transactions from their wallet without being required to download the entire blockchain history on their own device.

# What are Masternodes?

Some blockchains also feature masternodes. Masternodes are usually heavier equipped than normal nodes. Next to validating, saving and broadcasting transactions, masternodes sometimes also facilitate other events on the blockchain dependent on their nature, such as governing voting events, providing execution of protocol operations and enforcing the laws of the according blockchain. 

Masternodes are generally always online (24/7), and facilitate much more memory than normal nodes. You could say a masternode is like hosting a very large server
on the network. Because hosting a masternode usually requires much more resources (electricity, up-time, maintenance, storage space, memory), hosting one generally provides payment in the form of interest.

# Who can run a Masternode?

Not just anyone can run a masternode though. The power of controlling a masternode can be abused, and therefore it requires the host to deposit a minimum (often quite large) amount of crypto as collateral. This collateral is taken hostage when the masternode host violates the rules of the blockchain. The interest rate a masternode host receives is calculated over their collateral deposit.

Dash (DASH) is one of the most common blockchains that has a masternode feature built in. However, hosting a masternode on the Dash blockchain doesn’t come cheap — the minimum collateral to qualify for hosting a masternode on this blockchain is currently a staggering 1,000 DASH, worth $200,000 at the time of writing. It can still be an attractive investment though, as the DASH blockchain returned a yearly interest rate of 11% in 2016 for example.

At the time of writing, a website screening the live number of masternodes currently running on the DASH network claims there are up to 4,941 masternodes running, of
which 1284 in the United States and 1038 in the Netherlands. 

# Different Types of Blockchain Nodes

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

![bitcoin nodes](https://github.com/aridiosilva/Blockchain/blob/main/Types%20of%20Nodes%20in%20a%20Blockchain%20Network_.jpg)


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

### Lightweight (SPV) Nodes

Another type of blockchain nodes, used in day to day crypto operations, is the lightweight node or Simple Payment Verification (SPV) node. You’ve probably come across it already, but you’re most likely familiar with the “light wallet” definition.

These types of nodes communicate with the blockchain while relying on full nodes to provide them with the necessary information. As they don’t store a copy of the chain, they only query the current status for which block is last, and broadcast transactions for processing.

Having in mind the above features, it’s clear to see that running SPV node doesn’t require many resources, but it does sacrifice security for the sake of convenience.

### Lightning Nodes

Lightning nodes are a very interesting concept. They fit into the constraints of neither full nodes nor lightweight nodes as I’ve presented them to you so far.

The idea behind them is to establish a connection between users outside the blockchain. This way, the load on the network is reduced, transfer times are shortened significantly and there’s increased usability of crypto coins. Transaction fees are really low in the lightning network – the equivalent of roughly 10 to 20 satoshi in general.

The way it works is by opening a separate payment channel between entities. Take for example a bagel shop and Bob. Bob and the shop create something like a safe-deposit box (a multi-signature address) to which they both have separate keys. Bob deposits his funds and uses them to pay for bagels. Each transaction is agreed upon by both sides and happens pretty much instantly. Once he’s had enough bagels or simply runs out of money, he or the shop can close the connection, take the latest balance sheet and broadcast it onto the network.

This way, instead of waiting for each transaction to be confirmed and filling the network with space-wasting data, parties can interact between each other and lower the load on the blockchain. Furthermore, if someone else wants to deal with the same party, the lightning network will search for a path with the least number of intermediaries and lowest transfer fees, thus reducing wait times.

This way, instead of waiting for each transaction to be confirmed and filling the network with space-wasting data, parties can interact between each other and lower the load on the blockchain. Furthermore, if someone else wants to deal with the same party, the lightning network will search for a path with the least number of intermediaries and lowest transfer fees, thus reducing wait times.

### What Happens to a Node After a Fork?

Now that I’ve covered the different types of cryptocurrency nodes and you’re familiar with their operation, let’s explore how that ties into the network consensus and eventual forks.

In previous paragraphs, I mentioned that if there’s not at least a 51% agreement between full nodes, a proposed change to the network is rejected. But what happens if there’s a large part of the community that still wants to accept the suggested alteration? That is where forks come into play. A developer decides to create a new client, using the source code of the coin and implements the proposed change. Users willing to go on in that direction, download the new version and decide to support the now forked chain.

### Hard Fork

In short, a hard fork is a change to the network consensus algorithm. Every alteration that is not compatible with the previous version of the client used, is considered a hard fork. Parameters of the consensus that can provoke a hard fork when changed, may include a new block reward, block time, transition from PoW to PoS, implementation of masternodes and others.

Once a hard fork is launched, every node on the network that hasn’t updated to the new version of the software is rejected by the consensus as for its operating on invalid rules. That is one of the reasons why developers and communities generally avoid major changes, as it means some people will be left out or the transition phase may compromise the security of a network.

![hard-fork-mobile](https://github.com/aridiosilva/Blockchain/blob/main/hard-fork-mobile.jpg)

### Soft Fork

Another way of introducing changes to a network is via a soft fork. Contrary to hard forks, with this type of alteration, there’s no mandatory rule for users to update their nodes.

One such example is the addition of the Segregated Witness feature to Bitcoin. To this day, transactions can be made on BTC’s blockchain with or without using this feature. Once 95% of clients on the network are updated to the version that supports SegWit, the consensus will automatically change and refuse any old transactions without it. This way, we have a smoother transition that does not force users to immediately update.

![Soft Fork](https://github.com/aridiosilva/Blockchain/blob/main/soft-fork-mobile.jpg)

### Virtual Private Servers (VPS) and Their Usage with Nodes

Whether or not you decide to use a Virtual Private Server is up to personal preference. If you decide to run a masternode, lightning node or even a cold staking node, a VPS will be beneficial as you pay a small fee in return for protection from DDoS attacks, not having to maintain any hardware and not worry about your bandwidth capabilities.

On the other hand, if you don’t take enough security precautions, you risk someone hacking into your server and stealing your funds, provided you’re storing your coins in those wallets. These are the basics, but I’d recommend researching VPS servers in detail before deciding on whether or not to rent one. 

# How do Blockchain Mining and Transactions Work

# Blockchain: The mystery of mining difficulty and block time..

Mining difficulty is the degree that determines how hard it is for miners in terms of hashing power (and thus also time) to find an eligible hash aka signature for their block (a block of transactions needs an eligible hash to be verified and added to the blockchain). On the Bitcoin blockchain, miners try to find an eligible hash by hashing random numbers. Let’s briefly zoom in on this process.


# How Does Bitcoin Mining Work?

## What is Bitcoin Mining?

Cryptocurrency mining is painstaking, costly, and only sporadically rewarding. Nonetheless, mining has a magnetic appeal for many investors interested in cryptocurrency because of the fact that miners are rewarded for their work with crypto tokens. This may be because entrepreneurial types see mining as pennies from heaven, like California gold prospectors in 1849. And if you are technologically inclined, why not do it?

** KEY TAKEAWAYS **

> * By mining, you can earn cryptocurrency without having to put down money for it.
> * Bitcoin miners receive Bitcoin as a reward for completing "blocks" of verified transactions which are added to the blockchain.
> * Mining rewards are paid to the miner who discovers a solution to a complex hashing puzzle first, and the probability that a participant will be the one to discover the solution is related to the portion of the total mining power on the network.
> * You need either a GPU (graphics processing unit) or an application-specific integrated circuit (ASIC) in order to set up a mining rig.

However, before you invest the time and equipment, read this explainer to see whether mining is really for you. We will focus primarily on Bitcoin (throughout, we'll use "Bitcoin" when referring to the network or the cryptocurrency as a concept, and "bitcoin" when we're referring to a quantity of individual tokens).

The primary draw for many mining is the prospect of being rewarded with Bitcoin. That said, you certainly don't have to be a miner to own cryptocurrency tokens. You can also buy cryptocurrencies using fiat currency; you can trade it on an exchange like Bitstamp using another crypto (as an example, using Ethereum or NEO to buy Bitcoin); you even can earn it by shopping, publishing blog posts on platforms that pay users in cryptocurrency, or even set up interest-earning crypto accounts. An example of a crypto blog platform is Steemit, which is kind of like Medium except that users can reward bloggers by paying them in a proprietary cryptocurrency called STEEM. STEEM can then be traded elsewhere for Bitcoin.

The Bitcoin reward that miners receive is an incentive that motivates people to assist in the primary purpose of mining: to legitimize and monitor Bitcoin transactions, ensuring their validity. Because these responsibilities are spread among many users all over the world, Bitcoin is a "decentralized" cryptocurrency, or one that does not rely on any central authority like a central bank or government to oversee its regulation.

## How To Mine Bitcoins

Miners are getting paid for their work as auditors. They are doing the work of verifying the legitimacy of Bitcoin transactions. This convention is meant to keep Bitcoin users honest and was conceived by bitcoin's founder, Satoshi Nakamoto. By verifying transactions, miners are helping to prevent the "double-spending problem." 

Double spending is a scenario in which a bitcoin owner illicitly spends the same bitcoin twice. With physical currency, this isn't an issue: once you hand someone a $20 bill to buy a bottle of vodka, you no longer have it, so there's no danger you could use that same $20 bill to buy lotto tickets next door. While there is the possibility of counterfeit cash being made, it is not exactly the same as literally spending the same dollar twice. With digital currency, however, as the Investopedia dictionary explains, "there is a risk that the holder could make a copy of the digital token and send it to a merchant or another party while retaining the original."

Let's say you had one legitimate $20 bill and one counterfeit of that same $20. If you were to try to spend both the real bill and the fake one, someone that took the trouble of looking at both of the bills' serial numbers would see that they were the same number, and thus one of them had to be false. What a Bitcoin miner does is analogous to that—they check transactions to make sure that users have not illegitimately tried to spend the same bitcoin twice. This isn't a perfect analogy—we'll explain in more detail below.

Once miners have verified 1 MB (megabyte) worth of bitcoin transactions, known as a "block," those miners are eligible to be rewarded with a quantity of bitcoin (more about the bitcoin reward below as well). The 1 MB limit was set by Satoshi Nakamoto, and is a matter of controversy, as some miners believe the block size should be increased to accommodate more data, which would effectively mean that the bitcoin network could process and verify transactions more quickly.

Note that verifying 1 MB worth of transactions makes a coin miner eligible to earn bitcoin—not everyone who verifies transactions will get paid out.

1MB of transactions can theoretically be as small as one transaction (though this is not at all common) or several thousand. It depends on how much data the transactions take up.

"So after all that work of verifying transactions, I might still not get any bitcoin for it?"  That is correct.

To earn bitcoins, you need to meet two conditions. One is a matter of effort; one is a matter of luck.

1) You have to verify ~1MB worth of transactions. This is the easy part.
2) You have to be the first miner to arrive at the right answer, or closest answer, to a numeric problem. This process is also known as proof of work. 

"What do you mean, 'the right answer to a numeric problem'?"

The good news: No advanced math or computation is involved. You may have heard that miners are solving difficult mathematical problems—that's not exactly true. What they're actually doing is trying to be the first miner to come up with a 64-digit hexadecimal number (a "hash") that is less than or equal to the target hash. It's basically guesswork.

The bad news: It's guesswork, but with the total number of possible guesses for each of these problems being on the order of trillions, it's incredibly arduous work. In order to solve a problem first, miners need a lot of computing power. To mine successfully, you need to have a high "hash rate," which is measured in terms of megahashes per second (MH/s), gigahashes per second (GH/s), and terahashes per second (TH/s).

That is a great many hashes.

If you want to estimate how much bitcoin you could mine with your mining rig's hash rate, the site Cryptocompare offers a helpful calculator.

## Mining and Bitcoin Circulation

In addition to lining the pockets of miners and supporting the bitcoin ecosystem, mining serves another vital purpose: It is the only way to release new cryptocurrency into circulation. In other words, miners are basically "minting" currency. For example, as of Nov. 2020, there were around 18.5 million bitcoins in circulation.1﻿ Aside from the coins minted via the genesis block (the very first block, which was created by founder Satoshi Nakamoto), every single one of those Bitcoin came into being because of miners. In the absence of miners, Bitcoin as a network would still exist and be usable, but there would never be any additional bitcoin. There will eventually come a time when Bitcoin mining ends; per the Bitcoin Protocol, the total number of bitcoins will be capped at 21 million.2﻿ However, because the rate of bitcoin "mined" is reduced over time, the final bitcoin won't be circulated until around the year 2140. This does not mean that transactions will cease to be verified. Miners will continue to verify transactions and will be paid in fees for doing so in order to keep the integrity of Bitcoin's network.

Aside from the short-term Bitcoin payoff, being a coin miner can give you "voting" power when changes are proposed in the Bitcoin network protocol. In other words, miners have a degree of influence on the decision-making process on such matters as forking.

## How Much a Miner Earns

The rewards for bitcoin mining are reduced by half every four years. When bitcoin was first mined in 2009, mining one block would earn you 50 BTC. In 2012, this was halved to 25 BTC. By 2016, this was halved again to 12.5 BTC. On May 11, 2020, the reward halved again to 6.25 BTC. In November of 2020, the price of Bitcoin was about $17,900 per Bitcoin, which means you'd earn $111,875 (6.25 x 17,900) for completing a block.3﻿ Not a bad incentive to solve that complex hash problem detailed above, it might seem.

f you want to keep track of precisely when these halvings will occur, you can consult the Bitcoin Clock, which updates this information in real-time. Interestingly, the market price of bitcoin has, throughout its history, tended to correspond closely to the reduction of new coins entered into circulation. This lowering inflation rate increased scarcity and historically the price has risen with it.

If you are interested in seeing how many blocks have been mined thus far, there are several sites, including Blockchain.info, that will give you that information in real-time.

## What Do I Need To Mine Bitcoins?

Although early on in Bitcoin's history individuals may have been able to compete for blocks with a regular at-home computer, this is no longer the case. The reason for this is that the difficulty of mining Bitcoin changes over time. In order to ensure the smooth functioning of the blockchain and its ability to process and verify transactions, the Bitcoin network aims to have one block produced every 10 minutes or so. However, if there are one million mining rigs competing to solve the hash problem, they'll likely reach a solution faster than a scenario in which 10 mining rigs are working on the same problem. For that reason, Bitcoin is designed to evaluate and adjust the difficulty of mining every 2,016 blocks, or roughly every two weeks. When there is more computing power collectively working to mine for Bitcoin, the difficulty level of mining increases in order to keep block production at a stable rate. Less computing power means the difficulty level decreases. To get a sense of just how much computing power is involved, when Bitcoin launched in 2009 the initial difficulty level was one. As of Nov. 2019, it is more than 13 trillion.

All of this is to say that, in order to mine competitively, miners must now invest in powerful computer equipment like a GPU (graphics processing unit) or, more realistically, an application-specific integrated circuit (ASIC). These can run from $500 to the tens of thousands. Some miners—particularly Ethereum miners—buy individual graphics cards (GPUs) as a low-cost way to cobble together mining operations. The photo below is a makeshift, home-made mining machine. The graphics cards are those rectangular blocks with whirring fans. Note the sandwich twist-ties holding the graphics cards to the metal pole. This is probably not the most efficient way to mine, and as you can guess, many miners are in it as much for the fun and challenge as for the money.

## The "Explain It Like I'm Five" Version

The ins and outs of bitcoin mining can be difficult to understand as is. Consider this illustrative example of how the hash problem works: I tell three friends that I'm thinking of a number between one and 100, and I write that number on a piece of paper and seal it in an envelope. My friends don't have to guess the exact number; they just have to be the first person to guess any number that is less than or equal to the number I am thinking of. And there is no limit to how many guesses they get.

Let's say I'm thinking of the number 19. If Friend A guesses 21, they lose because of 21>19. If Friend B guesses 16 and Friend C guesses 12, then they've both theoretically arrived at viable answers, because of 16<19 and 12<19. There is no "extra credit" for Friend B, even though B's answer was closer to the target answer of 19. Now imagine that I pose the "guess what number I'm thinking of" question, but I'm not asking just three friends, and I'm not thinking of a number between 1 and 100. Rather, I'm asking millions of would-be miners and I'm thinking of a 64-digit hexadecimal number. Now you see that it's going to be extremely hard to guess the right answer.

If B and C both answer simultaneously, then the ELI5 analogy breaks down.

In Bitcoin terms, simultaneous answers occur frequently, but at the end of the day, there can only be one winning answer. When multiple simultaneous answers are presented that are equal to or less than the target number, the Bitcoin network will decide by a simple majority—51%—which miner to honor. Typically, it is the miner who has done the most work or, in other words, the one that verifies the most transactions. The losing block then becomes an "orphan block." Orphan blocks are those that are not added to the blockchain. Miners who successfully solve the hash problem but who haven't verified the most transactions are not rewarded with bitcoin.

## What Is a "64-Digit Hexadecimal Number"?

Well, here is an example of such a number: 

0000000000000000057fcc708cf0130d95e27c5819203e9f967ac56e4df598ee

The number above has 64 digits. Easy enough to understand so far. As you probably noticed, that number consists not just of numbers, but also letters of the alphabet. Why is that?

To understand what these letters are doing in the middle of numbers, let's unpack the word "hexadecimal."

As you know, we use the "decimal" system, which means it is base 10. This, in turn, means that every digit of a multi-digit number has 10 possibilities, zero through nine.

"Hexadecimal," on the other hand, means base 16, as "hex" is derived from the Greek word for six and "deca" is derived from the Greek word for 10. In a hexadecimal system, each digit has 16 possibilities. But our numeric system only offers 10 ways of representing numbers (zero through nine). That's why you have to stick letters in, specifically letters a, b, c, d, e, and f. 

If you are mining bitcoin, you do not need to calculate the total value of that 64-digit number (the hash). I repeat: You do not need to calculate the total value of a hash. 

So, what do "64-digit hexadecimal numbers" have to do with bitcoin mining? Remember that ELI5 analogy, where I wrote the number 19 on a piece of paper and put it in a sealed envelope?

In bitcoin mining terms, that metaphorical undisclosed number in the envelope is called the target hash.

What miners are doing with those huge computers and dozens of cooling fans is guessing at the target hash. Miners make these guesses by randomly generating as many "nonces" as possible, as fast as possible. A nonce is short for "number only used once," and the nonce is the key to generating these 64-bit hexadecimal numbers I keep talking about. In Bitcoin mining, a nonce is 32 bits in size—much smaller than the hash, which is 256 bits. The first miner whose nonce generates a hash that is less than or equal to the target hash is awarded credit for completing that block and is awarded the spoils of 6.25 BTC.

In theory, you could achieve the same goal by rolling a 16-sided die 64 times to arrive at random numbers, but why on earth would you want to do that?

The screenshot below, taken from the site Blockchain.info, might help you put all this information together at a glance. You are looking at a summary of everything that happened when block #490163 was mined. The nonce that generated the "winning" hash was 731511405. The target hash is shown on top. The term "Relayed by Antpool" refers to the fact that this particular block was completed by AntPool, one of the more successful mining pools (more about mining pools below). As you see here, their contribution to the Bitcoin community is that they confirmed 1768 transactions for this block. If you really want to see all 1768 of those transactions for this block, go to this page and scroll down to the heading "Transactions."

![blockchaininfo-5bfd7146c9e77c0051baafd0](https://raw.githubusercontent.com/aridiosilva/Blockchain/main/blockchaininfo-5bfd7146c9e77c0051baafd0.webp)



![blockchaininfo-5bfd7146c9e77c0051baafd0 ](https://github.com/aridiosilva/Blockchain/blob/main/dotdash_Final_How_Does_Bitcoin_Mining_Work_Dec_2020-04-2d73080ca35e4e3bab0455cac17026de_.png)

### "So how do I guess at the target hash?"

All target hashes begin with zeros—at least eight zeros and up to 63 zeros. 

There is no minimum target, but there is a maximum target set by the Bitcoin Protocol. No target can be greater than this number:

00000000ffff0000000000000000000000000000000000000000000000000000

Here are some examples of randomized hashes and the criteria for whether they will lead to success for the miner:

### "How do I maximize my chances of guessing the target hash before anyone else does?"

You'd have to get a fast mining rig, or, more realistically, join a mining pool—a group of coin miners who combine their computing power and split the mined bitcoin. Mining pools are comparable to those Powerball clubs whose members buy lottery tickets en masse and agree to share any winnings. A disproportionately large number of blocks are mined by pools rather than by individual miners.

In other words, it's literally just a numbers game. You cannot guess the pattern or make a prediction based on previous target hashes. The difficulty level of the most recent block at the time of writing is about 17.59 trillion, meaning that the chance of any given nonce producing a hash below the target is one in 17.59 trillion. Not great odds if you're working on your own, even with a tremendously powerful mining rig.

### "How do I decide whether bitcoin will be profitable for me?"

Not only do miners have to factor in the costs associated with expensive equipment necessary to stand a chance of solving a hash problem. They must also consider the significant amount of electrical power mining rigs utilize in generating vast quantities of nonces in search of the solution. All told, bitcoin mining is largely unprofitable for most individual miners as of this writing. The site Cryptocompare offers a helpful calculator that allows you to plug in numbers such as your hash speed and electricity costs to estimate the costs and benefits.

## What Are Coin Mining Pools?

Mining rewards are paid to the miner who discovers a solution to the puzzle first, and the probability that a participant will be the one to discover the solution is equal to the portion of the total mining power on the network. Participants with a small percentage of the mining power stand a very small chance of discovering the next block on their own. For instance, a mining card that one could purchase for a couple of thousand dollars would represent less than 0.001% of the network's mining power. With such a small chance at finding the next block, it could be a long time before that miner finds a block, and the difficulty going up makes things even worse. The miner may never recoup their investment. The answer to this problem is mining pools. Mining pools are operated by third parties and coordinate groups of miners. By working together in a pool and sharing the payouts among all participants, miners can get a steady flow of bitcoin starting the day they activate their miner. Statistics on some of the mining pools can be seen on Blockchain.info.

### "I've done the math. Forget mining. Is there a less onerous way to profit from cryptocurrencies?"

As mentioned above, the easiest way to acquire bitcoin is to simply buy it on one of the many exchanges. Alternately, you can always leverage the "pickaxe strategy." This is based on the old saw that during the 1849 California gold rush, the smart investment was not to pan for gold, but rather to make the pickaxes used for mining. Or, to put it in modern terms, invest in the companies that manufacture those pickaxes. In a cryptocurrency context, the pickaxe equivalent would be a company that manufactures equipment used for Bitcoin mining. You may consider looking into companies that make ASICs equipment or GPUs instead, for example.

## Is Bitcoin Mining Legal?

The legality of Bitcoin mining depends entirely on your geographic location. The concept of Bitcoin can threaten the dominance of fiat currencies and government control over the financial markets. For this reason, Bitcoin is completely illegal in certain places.

Bitcoin ownership and mining are legal in more countries than not. Some examples of places where it is illegal are Algeria, Egypt, Morocco, Bolivia, Ecuador, Nepal, and Pakistan.4﻿ Overall, Bitcoin use and mining are legal across much of the globe.

## Risks of Mining 

The risks of mining are that of financial risk and a regulatory one. As mentioned, Bitcoin mining, and mining in general, is a financial risk. One could go through all the effort of purchasing hundreds or thousands of dollars worth of mining equipment only to have no return on their investment. That said, this risk can be mitigated by joining mining pools. If you are considering mining and live in an area that it is prohibited you should reconsider. It may also be a good idea to research your countries regulation and overall sentiment towards cryptocurrency before investing in mining equipment.


# Which Industries Have adopted Blockchain Technology?

The majority of people understand Blockchain in relation to cryptocurrency. However, a number of mainstream industries, including finance, supply chain, gaming, and others, have started to use blockchain technology without any digital currencies. Let’s have a look at how such industries are using Blockchain for their operations. 

## Finance 

Finance is one of the most crucial applications of Blockchain. In fact, it is easy to see how Blockchain’s properties make it ideal for financial applications. Banks and other financial institutions are already using Blockchain for seamless cross-border payments, clearing settlements, digital identity management, and for other varying purposes. By offering decentralization, immutability transparency, and security, it can facilitate international payments and help perform worldwide financial transactions. By removing irrelevant intermediaries, it can simplify the entire transaction process and allow instant payment solutions globally. 

* AIB, Bank of Cyprus, China Banking Association, DNB, and many others are using Blockchain. 

## Supply Chain 

As various top companies have started realizing the potential of Blockchain, they have started implementing it for real-time data access, privacy, traceability, and auditability for their supply chain management.

For instance, Walmart, a well-known American multinational retail corporation, is utilizing Blockchain technology to add transparency, reliability, and traceability to its food supply ecosystem by digitizing the entire food supply chain process. Similarly, De Beers, the world’s biggest diamond producer by the value of its gems, is using Blockchain to track every natural diamond from the mine to the retail counter.

Apart from this, FedEx, United Parcel Service(UPS), and others are using this technology for their efficient supply chain.

According to the WEF study, Blockchain could contribute to a $365 billion savings by reducing food loss and waste in the food supply chain by 2030. 

As demand for Blockchain professionals is increasing in the Supply Chain Industry, become a Certified Blockchain & Supply Chain Professional today!

## Gaming Industry 

Blockchain has entered the gaming industry as well, and it is positively profiting both developers and gamers by providing a reliable and secure environment for developers with encryption techniques to secure crypto transactions. Also, with the concept of tokenization, it is enabling gamers to buy and sell game assets securely. Moreover, smart contract functionalities enable players to transfer all their in-game assets to their public addresses, thus providing complete control over digital assets.

Unlike traditional games, where powers are in the hands of players where they can abruptly shut down games, blockchain-based games give much access and control to players over their games.  

Age of Rust, Crypto Space Commander, CryptoWars, Gods Unchained are some of the interesting Blockchain-based games. 

## Pharmaceuticals

Blockchain technology continues to attract attention in the pharmaceutical domain. Amid the COVID-19 pandemic, government institutions globally have incorporated Blockchain technology. Blockchain can help in maintaining a supply chain visibility, providing real-time logging and data visualization of disease spread, early detection of epidemics, verifying communities and workplaces that are risk-free from the coronavirus outbreak, and much more. 

In 2020, several government institutions made announcements regarding plans to adopt DLT for multiple use cases, including the healthcare space. For instance, recently, it was announced that Cyprus’s Mediterranean Hospital utilizes the VeChain platform to store its COVID-19 vaccination records. Similarly, in November 2020, it was announced that South Korean hospitals aim to usher in the new healthcare era by utilizing Blockchain technology. 

Looking for the best Blockchain Certification? Get enrolled and become a Certified Blockchain & Healthcare Professional now!

## Voting 

Blockchain can play a significant role in voting as well. It can help in maintaining digital identity, prevents hacking and fraud, and allows anonymous voting. Moreover, Blockchain-based voting eliminates electoral malpractices like manipulations, tampering, recording errors, etc.

For example, South Korea has considered moving to the Blockchain for security reasons. Similarly, it was announced that the Indian state of Telangana is developing a blockchain-based electronic voting system to facilitate remote voting. Apart from this, Russia, the United States, and many others have already used a blockchain electronic voting system. 

# How do blockchain mining and transactions work 

Here is how a blockchain transaction is processed on a blockchain, in steps:

### Step 1: 

A user signs off on a transaction from their wallet application, attempting to send a certain crypto or token from them to someone else.

### Step 2: 

The transaction is broadcasted by the wallet application and is now awaiting to be picked up by a miner on the according blockchain. As long as it is not picked up, it hovers in a ‘pool of unconfirmed transactions’. This pool is a collection of unconfirmed transactions on the network that are waiting to be processed. These unconfirmed transactions are usually not collected in one giant pool, but more often in small subdivided local pools.

### Step 3: 

Miners on the network (sometimes referred to as nodes, but not quite the same!) select transactions from these pools and form them into a ‘block’. A block is basically a collection of transactions (at this moment in time, still unconfirmed transactions), in addition to some extra metadata. Every miner constructs their own block of transactions. Multiple miners can select the same transactions to be included in their block.

Example: two miners, miner A and miner B. Both miner A and miner B can decide to include transaction X into their block. Each blockchain has its own maximum block size. On the Bitcoin blockchain, the maximum block size of one block is 1 MB of data. Before adding a transaction to their block, a miner needs to check if the transaction is eligible to be executed according to the blockchain history. If the sender’s wallet balance has sufficient funds according to the existing blockchain history, the transaction is considered valid and can be added to the block. If a Bitcoin owner wants to speed up their transaction, they can choose to offer a higher mining reward. Miners will usually prioritise transactions such transactions over others, because they provide a better mining reward.

### Step 4: 

By selecting transactions and adding them to their block, miners create a block of transactions. To add this block of transactions to the blockchain (which means having all the nodes on the blockchain register the transactions in this block), the block first needs a signature (also referred to as a ‘proof of work’). This signature is created by solving a very complex mathematical problem that is unique to each block of transactions. Each block has a different mathematical problem, so every miner will work on a different problem unique to the block they formed. Each block’s problem is equally hard to solve. In order to solve this mathematical problem, a lot of computational power is used (and thus a lot of electricity). You can compare it to running a calculation on a calculator, only this is much heavier and on done a computer. This is the process referred to as mining. If you want to know more about how the mathematical problem works exactly (it’s not actually that complicated), please continue reading below, otherwise, in case you want to keep it a little more simple, skip to step 5.

> **Mining aka hashing (Proof of Work consensus algorithm)** - he mathematical problem every miner is facing when trying to add a block to the blockchain is to find a hash output (aka signature) for the data in its block, that starts with a certain amount of consecutive zero’s. That sounds complicated, right? But it isn’t really that hard. Let me try to explain this to you in a simple way.

A hash function is simply put a mathematical problem that is very hard to solve, but where the answer is very easy to verify. A hash function takes an input string of numbers and letters (literally any string of random letters, numbers and/or symbols), and turns it into a new 32 digit string existing out of random letters and numbers. This 32 digit string is the hash output. If any number or letter in the input string is changed, the hash output will also change randomly. However, the same string of input will always give the same string of output.

Now consider the data inside a block to be the hash input (a string of data). When this input is hashed, it gives a hash output (32 digit string). A rule of the Bitcoin blockchain is that a block can only be added to the blockchain if its signature, the hash output, starts with a certain amount of zeros. However, the output string generated by an input string is always random for each different input string, so what if the data string of the block does not lead to a signature (hash output) that starts with so many consecutive zeros? Well, this is why miners repeatedly change a part of the data inside their block called the nonce. Every time a miner changes the nonce, it slightly changes the composition of the block’s data. And when the composition of the block’s data changes (it’s input), it’s signature (it’s output) also changes. So every time the nonce of a block is changed, the block gets a new random signature.

Miners repeat this process of changing the nonce indefinitely until they randomly hit an output string that meets the signature requirements (the zeros). Below illustrates this in an example. This example uses seven zeros, but the amount of zeros really depends on the block difficulty of a blockchain. Block difficulty is a little more complicated though, so I suggest you save that for later.

This is how miners need to find an eligible signature to their block, and it is also the reason that so much computational power is needed to solve this mathematical problem. Guessing so many different nonces takes a lot of time and computational power. Also, when more hashing power (miners) joins a blockchain, the difficulty of it’s mathematical problem will increase and lead to higher average electricity expenses to solve a block (more about this here). Good work if you followed through, now let’s move on to step 5.

Note: This process is actually not defined as a mathematical problem, but rather as a deterministic thing — computers are performing pre-determined operations on a number to see if the output is desirable.

### Step 5: 

The miner that finds an eligible signature for its block first, broadcasts this block and its signature to all the other miners.

### Step 6: 

Other miners now verify the signature’s legitimacy by taking the string of data of the broadcasted block, and hashing it to see if its hash output indeed leads to its included signature of so many zeros (hard to solve, easy to verify, remember?). If it is valid, the other miners will confirm its validity and agree that the block can be added to the blockchain (they reach consensus, aka they all agree with each other, hence the term consensus algorithm). This is also where the definition ‘proof of work’ comes from. The signature is the ‘proof’ of the work performed (the computational power that was spent). The block can now be added to the blockchain, and is distributed to all other nodes on the network. The other nodes will accept the block and save it to their transaction data as long as all transactions inside the block can be executed according to the blockchain’s history.

### Step 7: 

After a block has been added to the chain, every other block that is added on top of it counts as a ‘confirmation’ for that block. For example, if my transaction is included in block 502, and the blockchain is 507 blocks long, it means my transaction has 5 confirmations (507–502). It is referred to as a confirmation because every time another block is added on top of it, the blockchain reaches consensus again on the complete transaction history, including your transaction and your block. You could say that your transaction has been confirmed 5 times by the blockchain at that point. This is also what Etherscan is referring to when showing you your transaction details. The more confirmations your transaction has (aka the deeper the block is embedded in the chain), the harder it is for attackers to alter it (you can read more about how this works here). After a new block is added to the blockchain, all miners need to start over again at step three by forming a new block of transactions. Miners cannot continue mining aka solving the problem of the block they were working on earlier because of two reasons:

> **One:** it may contain transactions that have been confirmed by the last block that was added to the blockchain (remember, multiple miners can select/include the same transactions(s) in the block they are solving) already. Any of those transactions initiated again could render them invalid, because the source balance might no longer suffice.

> **And two:** every block needs to add the hash output (signature) of the last block that was added to the blockchain into their metadata. This is what makes it a blockchain. If a miner keeps mining the block they were already working on, other miners will notice that the hash output does not correspond with that of the latest added block on the blockchain, and will therefore reject the block.


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

## Who Is Satoshi Nakamoto?

No one knows who invented bitcoin, or at least not conclusively. Satoshi Nakamoto is the name associated with the person or group of people who released the original bitcoin white paper in 2008 and worked on the original bitcoin software that was released in 2009. In the years since that time, many individuals have either claimed to be or have been suggested as the real-life people behind the pseudonym, but as of January 2021, the true identity (or identities) behind Satoshi remains obscured.

Although it is tempting to believe the media's spin that Satoshi Nakamoto is a solitary, quixotic genius who created Bitcoin out of thin air, such innovations do not typically happen in a vacuum. All major scientific discoveries, no matter how original-seeming, were built on previously existing research.

There are precursors to bitcoin: Adam Back’s Hashcash, invented in 1997,8﻿﻿ and subsequently Wei Dai’s b-money, Nick Szabo’s bit gold, and Hal Finney’s Reusable Proof of Work. The bitcoin whitepaper itself cites Hashcash and b-money, as well as various other works spanning several research fields. Perhaps unsurprisingly, many of the individuals behind the other projects named above have been speculated to have also had a part in creating bitcoin.

There are a few possible motivations for bitcoin's inventor deciding to keep their identity secret. One is privacy: As bitcoin has gained in popularity—becoming something of a worldwide phenomenon—Satoshi Nakamoto would likely garner a lot of attention from the media and from governments.

# SWOT Analysis of Blockchain Technology

In a world filled with emerging technologies, the blockchain technology is arguably one of the most exciting, being labeled as ‘disruptive’ and ‘innovative’ by many. Despite often being associated abundantly with Bitcoin and other cryptocurrencies, the underlying technology, this distributed ledger, the ‘blockchain’ has been receiving attention from a variety of industries. The concept of recording transactions in a secure, stable and chronological way, has led to possible applications in many areas.

Whilst we have to admit that blockchain is still in its infancy. Many issues like unwanted centralization, slow transaction verification times and low throughput aren’t easy to solve. We have to try and find the balance between security and speed.

To help you make sense of this complicated landscape we applied a simple SWOT analysis to the blockchain and integrated our iOlite’s solutions in this analysis.

![swot analysis](https://github.com/aridiosilva/SmartContractsBlockchain/blob/main/Blockchain%20SWOT%20Analysis%20of%20BLOCKCHAIN%20TECHNOLOGY__.png)


# Blockchain Mining Software

## What Is Bitcoin Mining Software?

Bitcoin mining software is essentially what makes Bitcoin work. By tracking and securing transactions known as blockchains, users are able to earn bitcoins rather than having to pay for them with actual currency.

Bitcoin mining software can only be used by specialized hardware that is powerful enough to run the complex calculations required to create new secure blocks. The software connects to the hardware to either mine bitcoins directly or, more often, to a mining pool where multiple users share their hardware’s power and earn shares of bitcoins.  

## How Long Does It Take to Mine One Bitcoin? 

In general, it takes about 10 minutes to mine one bitcoin. However, this assumes an ideal hardware and software setup which few users can afford. A more reasonable estimate for most users who have large setups is 30 days to mine a single bitcoin.    

## Can You Mine Bitcoin for Free?

Although bitcoin mining software is free, there are tremendous costs involved in both hardware and electricity costs. The specialized mining hardware can cost between a few hundred dollars to $10,000. 

Mining equipment is also very power-hungry. Depending on the cost of electricity in a miner’s area, it could potentially cost $73,000 to process one bitcoin in a month’s time.2﻿ One way to reduce this cost is to join a mining pool that harnesses the computational power of hardware owned by multiple miners. The drawback is that each miner only receives a small portion of each mined bitcoin.    

While some dismiss Bitcoin as a passing fad, many more are beginning to see it as the future of commerce. A 2020 survey showed that 36% of small and mid-sized businesses already accept cryptocurrency, as do many larger businesses and organizations including Microsoft, AT&T, and Wikipedia. While Bitcoin can be purchased with real cash, it’s more commonly “mined” using a combination of specialized hardware and software. In this article, we review the best bitcoin mining software based on reputation, features, ease of use, and more. Here are our top four picks.   

# Some Bitcoin Mining Software

- [**CGMiner**](https://github.com/ckolivas/cgminer)
- [**BFGMiner**](http://bfgminer.org/)
- [**MultiMiner**](https://nwoolls.github.io/MultiMiner/)
- [**Awesome Miner**](https://www.awesomeminer.com/)

## GMiner

As one of the oldest bitcoin mining software, CGMiner is our choice as the best overall due to its open-source build, ability to run on any computer, and compatibility with multiple mining hardware. This is a multi-threaded multi-pool FPGA and ASIC miner for bitcoin. This code is provided entirely free of charge by the programmer in his spare time so donations would be greatly appreciated. Please consider donating to the address below. Driver development for new ASIC only bitcoin hardware can be suitably sponsored. 

> - **Pros** :  Open source,  Runs on Mac, Windows, and Linux, Compatible with ASIC, GPU, and FPGA
> - **Cons** :  Better for advanced users,  Obscure command-line interface,  Hard to install on Windows 10 computers.

CGMiner was developed in 2011 by Australian anesthetist and programmer Con Kolivas for mining cryptocurrencies such as Bitcoin and Litecoin. It’s widely regarded as one of the best bitcoin mining software available due to its open-source nature, simple interface with direct controls, and cross-platform and cross-hardware compatibility.  

CGMiner uses a command-line interface that allows users to mine their rigs remotely and control fan speeds and other settings with simple keyboard commands. The software also offers advanced detection of new blocks and makes it easy to scale up hashing power without delays. 

Although it’s Linux-based, CGMiner is cross-platform compatible and can run on Mac and Windows computers. It’s also open-source and written in C, making it easy for anyone to verify the software’s code. In addition to being cross-platform compatible, CGMiner works with a variety of mining hardware besides ASICs, including FPGAs, GPUs, and CPUs.     

CGMiner’s lack of a graphical user interface may be daunting to beginners, making it a better choice for advanced users. The software has been known to be difficult to install on computers running Windows 10. Antivirus software including Windows Defender can also give users a difficult time. CGMiner is free to download and use and is available on GitHub.

##  BFGMiner

Designed for FPGA and ASIC mining, BFGMiner offers advanced users the opportunity to tweak many aspects of their mining process, with dynamic clocking, monitoring, and remote mining rig interface, making the software our pick as the best for customization.

> - **Pros**:  Mines multiple cryptocurrencies simultaneously,  Runs on Mac, Windows, and Linux,  Compatible with ASIC and FPGA
> - **Cons**:  Better for more advanced users,  Not compatible with GPU

Released in 2012 by developer Luke Dashjr, BFGMiner has become one of the most popular mining software available, second only to CGMiner. It allows users to monitor hardware temperature, detect and start idle threads, and manage rigs remotely, putting it squarely in the category of the best software for customization.    

Because BFGMiner was originally created to add FPGA support to a popular GPU miner at the time it was developed, the software is only compatible with FPGA and ASIC. Like CGMiner, the software is written in C and runs on Linux, Mac, and Windows machines and even offers an option to install on Raspberry Pi.   

One of BFGMiner’s most popular features is its support for mining multiple cryptocurrencies at the same time. By simultaneously hashing on mining algorithms like Scrypt and SHA256d, the software lets users mine, hedge, and redistribute their risk with multiple cryptocurrencies.   

Like CGMiner, BFGMiner uses a command-line interface with customizable hotkeys. While easy to use for advanced users, the lack of a GUI may make the software impenetrable to beginners. BFGMiner is also free to download and use.

## MultiMiner

Developed using the mining engine of BFGMiner, MultiMiner features a clean GUI, automated hardware detection and mining features, and cross-platform compatibility, making it our clear choice as the best for ease of use.

> - **Pros**:  Graphical user interface, Automated mining features, Optimized for Windows computers
> - **Cons**:  Additional software required for Linux and MacOS

MultiMiner was developed in 2013 by BFGMiner developer Nate Woolls. Although it’s built on the BFGMiner engine, the software features an easy-to-use GUI and quick-start mining features, making it our favorite choice as the best for ease of use.

While most mining software requires some coding skills, novices can get started with MultiMiner with no technical skills. The software walks users through the installation process and then scans the details of the hardware, including average hashing power and the linked pool. 

MultiMiner goes even further and shows users exactly how to connect to a pool, including where to enter the information associated with the pool. The software also offers users remote access to their mining rigs, lets them choose their mining strategy, and automatically mines the most profitable or lowest-difficulty cryptocurrency with a display of estimated profits.

MultiMiner installs easily on Windows computers, but users will need to install additional software for Mac and Linux machines. The software also makes it easy to switch mining rigs, including GPUs, ASICs, and FPGAs. Despite its appeal to beginners, power users can also access MultiMiner’s advanced features, including direct access to API settings and engine arguments. The software is also free to download and us.

# Awesome Miner

Awesome Miner is a powerful mining software that lets users manage multiple mining rigs and miner’s pools, all from one dashboard. As a result, it tops our list as the best centralized management software.

> - **Pros**:  Supports more than 25 mining engines, Customized triggers and actions, Access from any computer, tablet, or smartphone
> - **Cons**:  No MacOS software, Not for novice users

Awesome Miner was developed by Swedish software company IntelliBreeze in 2014 as a cryptocurrency mining management application for Windows machines. It supports large-scale mining with a dashboard that lets users manage multiple mining engines and pools in one operation, making it the best software for centralized management.

Awesome Miner offers a number of powerful features to help users maximize profit and minimize downtime. The software can handle multiple mining hardware types at the same time (including ASICs and FPGAs), supports more than 25 mining engines (cgminer, bfgminer, xmrig, srbminer, etc.), and is compatible with popular mining algorithms (SHA-256, Scrypt, X11, Ethereum, and Zcash).  

Awesome Miner also makes it easy for users to add, switch, and manage multiple miner pools with one click so they can start mining in less time. All of this is managed in Awesome Miner’s comprehensive dashboard, which also displays hardware properties like fan speed, temperature, etc. The software features a built-in C# script engine miners can use to make customized triggers and actions.

Although Awesome Miner is designed for Windows and Linux, the web version of the software can be accessed on any computer or browser. Awesome Miner is free to download and use.


