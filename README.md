
# Consensus and Reliable Broadcast

Why we need the consensus in blockchain

# Broadcast
If a process sends a message m, then every process eventually delivers m.  
How can we adapt the spec for an environment where processes can fail? And what does "fail" mean?

# A hierarchy of failure models

Fail-stop, Crash, Send Omission, Receive Omission, General Omission, Arbitrary failures with message authentication, Arbitrary (Byzantine) failures.

# Reliable Broadcast

Validity: If the sender is correct and broadcasts a message m, then all correct processes eventually deliver m.    

Agreement: If a correct process delivers a message m, then all correct processes eventually deliver m.   

Integrity: Every correct process delivers at most one message, and if it delivers m, then some process must have broadcast m.  


Termination: Every correct process eventually delivers some message.  

Safety: Block accepted is a "Safe" block.  

Liveness: New blocks are created & accepted.  

Process: could be a node/ computer/ 

Lantency: sending to recieving


# Selfish-mining attack:
 

# Nakamoto consensus 
 
 Summary:
 1. longest chain considered to be correct
 2. Proof of words (nonce: creating hash value of a nonce)
 3. Canonical chain longest one
 4. 

 Nakamoto consensus is a name for Bitcoin’s decentralized, pseudonymous consensus protocol. It is considered as Bitcoin’s core innovation and its key to success. The consensus protocol doesn’t require any trusted parties or pre-assumed identities among the participants.   
 
At any given point in time the network of peer parties has an established agreement about a global ledger of transactions which have happened so far. The ledger consists of blocks each of which comprises individual valid transactions as well as special transaction called block reward. There are special types of parties called miners which decide to compete each other to produce a new block and win the block reward as well as optionally collect transaction fee. The consensus protocol is needed in order to decide which next block to include into the ledger. The consensus protocol says that the first announced valid block containing solution to a computational puzzle is considered correct; and all other miners are to start searching for a followup block after that moment. This may occasionally lead to temporary forks due to several simultaneously found solutions. The longest fork in that case is considered valid. In case of equal-length forks miners can choose either one. Due to probabilistic nature of computational puzzle, one fork will eventually get longer than the other.
 
The computational puzzle plays essential role in establishing the consensus. It is often referenced as proof-of-work in spite the fact that the process of finding the solution is rather probabilistic.

# Proof of Work

Bitcoin: There are keys buried x feet under. Any key will open this treasure box. Go and dig!

while (key noot found) {
  grab a spot and dig x feet
}

Why BAR tolerant?
* Incentives
* Fake answers are easily verifiable and rejected

Litecoin: 
Monero: 
Zcash:

Puzzle: hard to solve but easy to verify.

Take home: 
1. Watch Berkeley vedio
2. Distributed system test book
3. Read ahead concensus slide til TRB for benign failures


# Benign Synchronous Message Passing Model

* Execution is a sequence of rounds
* In each round evert process takes...

# A simple consensus algorithm

# Echoing values

# Dangerous Chains

f faulty processes -> at most f + 1 nodes in the chain -> it is safe to decide by the end of round f + 1!

# Consensus
Termination: p1 eventually decides.  
Integrity: Every p1 decides on at most one from p1
Agreement: '' the same u 
Validity: '' on a value

# Agreement
Every new value that you recieve in certain round, there must be a tracable chain
All process in the sequence are distinct

# MTTF: Mean Time Failure
If expect 1 failure, do 2 rounds, if expect 2 failures do 3 rounds

# Terminationg Reliable Broadcast

Validity: 
Agreement: 
Integrity: 
Termination: 

# A hierarchy of failure modes

# Early stopping the idea
Suppose processes can detect the set of processes taht have failed by the end of roundi

Call that set faulty(p,i)
If(fault(p,i)| < i there can be no active dangerous chains, and p can safely deliver SF)


# Terminationg Reliable Broadcast

# A Lower Bound
Theorem: There is no algorithm that solves the consensus problem in fewer than f + 1 rounds in the presence of f crash failures, if n >= f + 2
We consider a pecial case (f=1) to study the proof technique

# ETH
hash puzzle / longest chain

decide f and n => n = 3f + 1, n is fixed.

# Views
View of process p1 in a denoted bt a|p1, is the subsequence of computation and message receive events that occur in p1 together with the state of pi in the initial configuratuib of a.

# Authentications
Authenticity is identification and assurance of origin of information

TO VERIFY THE ORIGIN

# Basic Public Key Cryptography

Signature: should be 1. unforgeable 2. non-mallenable

# Public-Key Cryptographic Algorithm

RSA: Rivest, Shair and Adleman

Example: 
* Encryption: 

# Public-key infrastructure

1) Having "right" public key
Consensus: assume so. Blockchain: identuty = public key H(public key)

2) Hash + private key


# 2019/2/26

# Arbitrary failures with message authentication
Faulty <=> not sending a msg or sending conflict msg

# Valid message
A valid message m has the following form:
in round1:
  m : s id (m is signed by the sender)
in round r > 1, if received by p from q:
  m : p1, p2, p3 ... pr where 
  p1 = sender; pr = q
  p1, ... , pr are distinct from each other and from p
  message has not been tampered with

# Vector clock

# Properties of broadcast and accept
* Correctness
* Unforgeability
* Relay

# Implementing broadcast and accept

* A process that wants to broadcast m, does so through a series of witnesses
  * Sends m to all
  * Each correct process becomes a witness by relaying m to all
* If a process receives enough witness confirmations, it accepts m.  (f + 1) for eaxmple

We can rely on witnesses, only if not too many faulty processes!

# The plot thickens

majority voting: 
We have a mathematical proof that to tolerate n malicious nodes, you need 2n + 1 good nodes. 

round r, p sends (init,p,m,r) to all

# What about asynchronous systems?

FLP says consensus cannot be solved in asynchronous system

Correct process can not know whether the process is fault or just slow

# The Model - 1

n processes
a message buffer

# Assumptions:

Liveness Assumption
One time Assumption

WLOG, process pi

# Configurations

# State machine 
Using states to determing the blockchian behaviours

Do not use it in blockchain
One way to forward verification

# Schedules

A schedule S of A is a finite or infinite sequence of steps of A

# Schedules and configurations
1. C ->(Has a schedule to become C') -> C', config C' is accessible from config C. C' is a configuration of S(C) if exists a S' prefix of S such that S'(C) = C' 

# Runs
A run of A is a pair <I, S> where I is an initial config,
1. partial
2. admissible
3. unacceptable

# Structure of the proof

# Classifying configurations

0-valent
1-valent
Bivalent

# FLP (impossibility) result

Even with one crash failure, consensus fails in asynchronous network
Indistinguishable between slow and lost

# Eventual sychrony

# The famous 1/3 (! Memorize)
f faulty nodes out of n total
Byzantine nodes may not send msg Honest nodes receive >= (n-f) msgs
Out of (n-f) msgs, f msgs may be faulty // Good node only recieve (n - f) and go on, to prevent infinitely waiting
(n-2f) msgs are from honest nodes 
(n-2f) > f -> n>3f -> f < 1/3

# !(Memorize) Consensus is hard
Impossible when the network is unreliable (Tow general's problem)
Impossible when the network is asynchronous (no bound on latency)
Possible when the network has eventual synchrony (bound on delay)

# Byzantine-fault tolerance (BFT)
BFT = the system achieves the goal in ther presnce of Byzantine-faulty users using redundancy/replication

# Primary-backup + quorum system

# Midterm Review

## 6 properties of secure hash functions

1. H can be applied to a block of data at any size
2. H produces a fixed length output
3. H(x) is easy to compute for any given x.
4. For any given block x, it is computationally infeasible to find x such that H(x) = h.
5. For any given block x, it is computationally infeasible to find y != x such that H(x) = H(y).
6. It is computationally infeasible to find any pair (x, y) such that H(x) = H(y).

## Collisions: avoidance vs resistance

1. Collision avoidance means that given an infinite amount of tries it is impossible to find a h(x) = h(y) where x != y. This is non existing
2. Collision resistance which is what we aim to have, means that it should be computationally infeasible to find a h(x) = h(y) where x != y, but it will still happen.  

## one-wayness: 
Hash should be hard to invert

## how to use cryptographic hash functions (and public key cryptography) for authentication
1. Asymmetric cryptography means we have 1 key for encryption and 1 key for decryption.
2. In public key cryptography, there are 5 elements: the actual data, sender's public key, sender's private key, receiver's public key and receiver's private key.
3. A public key is announced and known to the world. A private key is stored in the owners node or in a physical/digital safety locker. Private key is otherwise called a secret key.
4. At a given point, neither the sender nor receiver can know each other's private key. Public key of sender and receiver. Private key of their own
5. You can encrypt a piece of data with a public key, but the decryption can be done only with its corresponding private key
6. A sender would always start with the receiver's public key for encryption. The receiver would use its own (receiver) private key for decryption.
7. Receiver still does not know who sent the data. It could have been sent by a hacker. So the sender needs to let the receiver know that the data is indeed sent by sender. This process is called signing. Signing is done by attaching a small piece of addtional data called the signature.
8. The process:
Sender:
  * Sender encrypts the data with sender's private key: sender-privkey(data) = sender-privkey-encryp-data (the signature)
  * Sender the combines the 'sinature' with the receivers public key: recv-pub-key(data + signature) = receiver-pubkey-encrypted-data
  * Send to receiver
Receiver:
  * Reveive message: receiver-pubkey-encrypted-data
  * receiver-privkey(receiver-pubkey-encrypted-data) = data + signature
  * Receiver can now see the data
  * Receiver checks the signature: sender-pubkey(signature) = data1
  * Since data = data1, receiver can confirm sent by sender
Notes the message sent through the network is twice the size of the intended message.
  * This is because ofthe signature "sender-privkey-encryp-data"
  * The size of the signature can be compressed by hashing the actual data and then encrypting only the hash.
  * Hence, instead of encryptiong a huge: "data + sender-privkey-encrypted-data", we can encrypt only the "data + sender-privkey-encrypted-hash".



## Merkle Tree

1. Merkle tree is a hash tree where leaves contain hashes of individual data blocks and parent nodes contain hashes of their respective children
2. It employs a hash-based architecture to maintain and verify data integrity.

## How to build a Merkle tree
1. Concatenate the hash values of each pair of nodes and find its hash value, if a node does not have a pair, concatenate it with itself and find that hash value
2. Use the new Hash Value as a node, which is the parent of the previous child nodes
3. Find a neighbouring parent node to form a pair and repeat Step1

## How to use a Merkle tree to compare two data sets, and its time complexity
1. Two Merkle tress can be compared if they have same hash depth
2. The trees are compared recursively starting at root hash.
3. If root hashes match in both the trees then all the data blocks in the tree's token range are consistent between replcas.
4. If root hashes disagree, then the left child hashes are compared followed next by right child hashes.
5. The comparison proceeds until all the token ranges that differ between the two are calculated.

## Merkle Proof
1. To verify the position and integrity of a piece of data within a database that has a particular root.
2. We need three components: 1. Data value, 2. Merkle Path, 3, Root value

## How to use a Merkle tree to show the integrity of data (that the data has not changed), and its time complexity

1. Merkle proofs, with wich, someone can verify that the hashing of data is consistent all the way up the tree and in the correct position without having to actually look at the entire set of hashes.
2. Instead, they can verify that a data chunk is consistent with the root hash by only checking a small subset of the hashes rather than the entire data set.

## What is a Merkle path?

1. In a Merkle tree, data can be audited using the root hash in logarithmic time to the number of leaves.
2. This is called a Merkle Proof and it works by recreating the branch containing the piece of data to be audited up to the root.
3. This recreation follows an authentication path from the leaf up to the root and is called the Merkle path.

## What is a trie (radix tree)
1. In a radix tree, a key is the actual path taken through the tree to get to the corresponding value.
2. That is, beginning from the root node of the tree, each cahracter in the key tells you which child node to follow to get to the corresponding value, where the values are stored in the leaf nodes taht terminate every path through the tree.
3. Supposing the keys come from an alphabet containning N characters, each node in the tree can have up to N children, and the maximum depth of the tree is the maxium length of a key.

## What is the benefit of using trie over binary search tree?

1. Radix trees are nice because they allow keys that begin with the same sequence of characters to have values that are closer together in the tree.
2. They can, however, be rather inefficient, like when you have a long key where no other key shares a common prefix.
3. In this case, a considerable number of nodes in the tree would need to be traversed to get to the value, despite there being no other values along the path.

## How is a Trie different from a Patricia Trie

1. A patricia trie is a compressed prefix tree, making it more space efficient.
2. With long character paths it is inevitable tha after traversing the first few layers of the trie, you will reach a node where no divergent path exists for at least part of the way down.
3. It would ne naive to require such a node to have empty values in every index (one for each of the 16 hex characters) besides the target index (next nibble in the path).
4. A Patricia trie adds a level of complexity which shortcuts the descent by setting up an extension node wich contains the "partial path" to skip ahead and the key is for the next db lookup.

## What is the difference between Patricia trie and Patricia Merkle Trie?

1. First to make the tree cryptographically secure, each node is referenced by its hash.
2. With this scheme, the root node becomdes a cryptographic fingerprint of the entire data structure (hence, Merkle).
3. Second, a number of node types are introduced to improve efficiency: 
  * Blank node: which is simply empty and the standard leaf node, which is a simple list of [key, value].
  * Extension Nodes, which are also simple [key, value] lists, but where value is a hash of some other node. The hash can be used to look-up taht node in database.
  * Branch nodes, which are lists of length 17. The first 16 elements correspond to the 16 possible hex characters in a key, and the final element holds a value if there is a [key, value] pair where the key ends at the branch node.
4. They are fully deterministic, meaning that a Patricia trie with the same (key, value) bindings is guaranteed to be exactly the same down to the last byte and therefore have the same root hash, privide the holy grail of O(log(n)) efficiency for inserts, lookups and deletes.


## How to build a Patricia Trie
## How to insert a new key into a Patricia Trie and its time complexity
## How to delete a key in a Patricia Trie and its time complexity
## How to use a Patricia Trie to test if a key exists and its complexity

## Transaction support
TODO
## What is ACID properties?
TODO
## Example of non-atomic transactions resulting in an inconsistent state
TODO


## Nakamoto consensus:



# What does Ethereum require as proof of work

1. For each block of transactions, miners use computers to repeatedly and very quicky guess answers to a puzzle until one of them wins.
2. More specifically, the miners will run the block's unique header metadata (including timestamp and software version) through a hash function (which will return a fixed-length, scrambled string of numbers and letters that looks random),only changing the 'nonce value', which impacts the resulting hash value.
3. If the miner finds a hash that matches the current target, the miner will be awarded ether and broadcast the block across the network for each node to validate and add to their own copy of the ledger.
4. If a miner, B, finds the hash, another miner A will stop work on the current block and repeat the process for the next block.

## What is a fork in blockchain

1. Temporary Fork: are forks that occur when miners, on cryptocurrency systems discover a block at the same time. The results in two split competing blockchains. Temporary forks are resilved in proof-of-work systems such as Bitcoin when miners select which chain to form subsequent blocks upon. The longest blockchain is viewed as being the 'true' blockchain, and will win out, whilst the shorter chain will be abandoned.

2. Soft forks: This is a method of upgrading the blockchain. A soft fork is software upgrade that is backward compatible with previous sersions of the software. A blockchain fork is essentially a colectively agreed upon software update. An example of a soft fork would be the implementation of a new rule changing. An example of a soft fork would be the implementation of a new rule changing the network lock size from 1MB to 500 KB. Nodes that have not upgraded will continue to see incoming transactions as valid, as these nodes follow the old set of consensus rules as well as the new. However, mining nodes that have not upgraded and attempt to mine new bloks will have these blocks rejected, as it does not conform to the new set of consensus rules (block sizes of 500KB).

# How does Ethereum resolve a temporary fork

We choose the branch that has produced the greatest amount of computing power

# How does Ethereum resolve a fork

When we have two chains, over time, one chain will eventually outpace the other. The longer chain will be considered the main chain.

# What is Nakamoto consensus

Longest chain + Proof of Work = Nakamoto Consensus


## Consensus in crash failure model:

## Example execution where a simple consensus protocol (slide 140 fails to achieve consensus)
## What is a dangerous chain
## Prove the minimal number of rounds to achieve consensus when up to f processes can have crash failures
## Early termination protocol

## Imagine there are n processes, p0 ... p(n-1). p0 broadcasts its proposal, and receives everyone else's proposal, and decides on the minimum value among all received values and its own proposal. p1 does the same, p2 does the same, etc. Could all of this happen in 1 round if there are no faulty processes? Explain your answer.

## Imagine there are n processes, p0.. p(n-1) and there can be up to 2 faulty processes. Draw an execution diagram that shows how consensus fails in the presence of 2 faulty processes in 2 rounds.



# Public-key Cryptography

## 6 requirements for public-key cryptography

1. Easy generation of a pair: public and private keys
2. Easy for the sender to generate cipher text
3. Easy for receiver to decrypt cipher text using private key
4. Infeasible to determine private key with public key
5. Infeasible to recover message M, knowing public key and cipher text
6. One of the keys is used for encryption and the other for decryption

## How to use RSA public key and private key for the encryption and decryption (?)

## Why is RSA secure (what assumptions are necessary for RSA to be secure?)

1. The main reason why RSA is secure lies within the difficulty to find the decryption key.
2. Person A = self, Person B = Key holder, Person C = Interceptor
3. A third party that intercepts the message knows that n=pq, the simplest way to find n would be somehow factor n into the exact primes used by Person B in the algorithm.
4. With larger (which are more secure) primes, this turns out to be nearly impossible to do.
5. Now factoring n is basically impossible to do by hand.
6. It would need large amount of computing power to factor n.


# How to use public/private key (and cryptographic hash function) for authentication

1. Asymmetric encryption uses two keys to encrypt a plain text.
2. Secret keys are exchanged over the Internet or a large network. It ensures that malicious persons do not misuse the keys.
3. It is important to note that anyone with a secret key can decrypt the message and this is why asymmetrical encryption uses two related keys to boosting security.
4. A public key is made freely available to anyone who might want to send you a message.
5. The second private key is kept a secret so that only you can know.

## What is public-key infrasetructure(PKI)? (why do we need this?)

The Public key infrastructure (PKI) is the set of hardware, software, policies, processes and procedures required to create, manage, distribute, use, store, and revoke digital certificates and public-keys.

## How does Ethereum provides PKI? (?)

## Terminating Reliable Broadcast

1. Validity: If the sender is correct and broadcasts a message m, then all correct processes eventually deliver m.
2. Agreement: If a correct process delivers a message m, then all correct processes eventually deliver m.
3. Integrity: Every correct process delivers at most one message, and if it delivers m, then some process must have broadcast m.
4. Termination: Every correct process eventually delivers m.

## Consensus
1. Validity: If all processes that propose a value propose v, then all correct processes eventually decide v.
2. Agreement: If a correct process decides v, then all correct processes eventually decide v.
3. Integrity: Every correct process decides at most one value, and if it decides v, then some process must have proposed v.
4. Termination: Every correct process eventually decides some value. 

# Consensus in Crash Failure Models

## Arbitrary failure with message authentication
Example execution where consensus algorithm for crase failure model (slide 30) fails

1. We may be unable to achieve consensus in just one round, due to possible failures in certain processes.
2. However, we can achieve consensus in two rounds by echoing values.
3. Echoing: A process that receives a proposal in round 1, relays it to all others in round 2.


## Dangerous chain

1. A dangerous chain is when the last process in the chain is correct, but all others are faulty.
2. If we have f faulty processes, a dangerous chain will have at most f+1 nodes in the chain, spans at most f rounds. It is safe to decide at the end of round f+1.

## Prove the minimum number of rounds to achieve consensus is when up to f processes can have crash failures

1. f + 1 is when we are able to achieve consensus.
2. A dangerous chain is having one new value introduced every single round after round 1. Where in round 1 every process sends a valid value to every other round.
3. The last process that can fail is p(f-1). So the dangerous chain ends at p(f).
4. This is the last process that learns of a new value, which is at round f.
5. Since f processes failed/crashed, during round f + 1, p(f) will tell all other processes its final result which allows all processes have the same set.
6. Therefore the longest possible dangerous chain ends at round f.

7. This is worst case scenario. As p(f) goes through the rounds, there is a dangerous chain building up. Up until round f, p(f) will know that the size of the faulty nodes can be from 0->f. When: "number of faulty nodes" < "the number of rounds", then we know the dangerous chain is no longer in progress. If "number of faulty nodes" == "the number of rounds", then the dangerous chain is still in progress.

## Early termination protocol

1. Suppose processes can detect the set of processes that have failed by the end od round 1.
2. Where the set of faulty processes are called: faulty(p, i)
3. If faulty(p, i) < i, (faulty process are less than the number of rounds), then there can be no active dangerous chains, and p can safely deliver SF.

## A lower bound

There is no algorithm that solves the consensus problem in fewer than f + 1 rounds in the presence of f crash failures, if n >= f + 2

## Arbitrary failure with message authentication (signatures)

1. A correct process discards all non-valid messages
2. If a message is valid: 1. Extract value form message, 2. relay the message with its own signature appended.
3. At round f+1: 1. if it extracted exactly one message, process delivers it, else p delivers SF (Source/Sender Failure)

## 2 properties of message authentication (signature)

1. Message sent has not been modified while in transit: This ensures that processes cannot send conflicting message to different receivers.
2. Message is signed and so receiver can verify the source of the message: Unforgeable signatures.



## How the algorithm in slide 86 achieves consensus in the example execution above
(?)

# Arbitrary failure model
## 2 properties of broadcast/accept primitives


## Example execution where consensus algorithm on slide 86 fails to achieve consensus without msg auth
## Requirements to become a witness of a message (p, m, r), i.e. when to send echo
## How the algorithm in slide 94 achieves consensus in the example execution above

## Impossibility results

Impossible to achieve consensus: 1. Message can be lost. 2. Asynchronous network
Possible to achieve consensus: Eventual synchrony.

# PBFT
How does a client decide the response to a command
How many messages are sent for one client's command
How can backup nodes build a proof of misbehavior of faulty primary

## Byzantine Fault Tolerance

A Byzantine fault is where components may fail and there is imperfect infomation on whether a component has failed.
It is the ability of a distrubuted computer network to remain fault tolerant with valid consensus despite imperfect information or failed components of the network.



# Byzantine General's Problem

If there are 1/3 or greater faulty nodes, there can be no solution/consensus.



# Recap

NFS: Network File System 

Practical BFT 
PBFT: 

eventual syhchrony


first round: Primary send msg to back up
Second round: check primary node is consistant
Third round: check back up is conststant

Critical path: 

Three phases:
Pre-prepare
Prepare
Commit

# How does Ethereum provides PKI (?)

# How the algorithm in slide 94 achieves:

filter out invalid msg

Broadcast: 
Accept: 
-> mimic msg authentication
-> non-forgeable, -> relay

# Early termination protocol:
Count what protocols was faulty

# Prove the minimal number of rounds to a...

# What is public-key infrastructure

# Build a Gossip Network

properties:
  Write: [Public, Consortium, Private]
  Read: [Public, Consortium, Private]

E.g: 
  Ethereum: public write, public read
  Passort/IO: private write, public read
  Walmart/IBM blockchain: Consortium write & read
  Mediledger: Consortium write, public read
  Cosmetics/Authentication: Consortium write, public read

KEY:
Flooding
Topology -> number of hops
Overlay Network = connectivity, independent from physical connection, topology independent from actual internet connection

Overlay Network is more stable than physical connection.

# Proof of Work

# Proof of Stake

## Ethereum/Casper
Users vote on the new block

## Cardano/Ouroboros
Users vote on the slot leader

## Direct democracy
Almost every node with "stakes(shares)" can vote

# Stake
vote = stake holders can vote
leader election = stake holder can become leaders

Byzantine <-> BFT
Altruistic - vote on one branch
Rational - vote on both <-> incentive compatible

# BlockChain for marketplace
