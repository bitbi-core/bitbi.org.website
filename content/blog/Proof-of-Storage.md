+++
title = "Proof of Storage: How to Prove and Verify"
date = 2024-07-06
authors = ["Bu Ji"]
description = "Proof of Storage is a consensus mechanism that relies on storage space rather than computational power to secure a blockchain network. Learn how Proof of Storage works, how to prove and verify storage, and its advantages and challenges."
+++

We all know that Proof of Work (PoW) and Proof of Stake (PoS) are the two most common consensus mechanisms used in blockchain networks. However, there are other consensus mechanisms that offer unique features and benefits. One such mechanism is Proof of Storage, which is used in some storage-focused blockchains to secure the network and validate transactions. In this article, we will explore what Proof of Storage is, how it works, and its advantages and challenges.

### What is Proof of Storage?

Proof of Storage is a consensus mechanism that relies on storage space rather than computational power to secure a blockchain network. In a Proof of Storage system, network participants (often called storage nodes) store and maintain copies of the blockchain's data. These nodes are responsible for storing data securely and making it available for verification when needed. The node may store some or all of the data, depending on the network's design. 

No matter how much data the node stores, it must be able to prove that it is storing the data correctly and that it has not been tampered with. This proof is essential for maintaining the integrity of the data and ensuring that the network remains secure.

### What are the Goals of Designing a Proof of Storage System?

The primary goals of designing a Proof of Storage system are:

1. **Data Integrity:** Ensuring that the stored data is accurate and has not been tampered with.
2. **Data Availability:** Making sure that the data is available for retrieval when needed.
3. **Efficiency:** Designing a system that is efficient in terms of storage space, bandwidth, and computational resources.
4. **Security:** Protecting the data from unauthorized access, tampering, or deletion.
5. **Decentralization:** Distributing the storage of data across multiple nodes to prevent a single point of failure.
6. **Incentives:** Providing incentives for storage nodes to participate in the network and maintain the data.
7. **Scalability:** Ensuring that the system can scale to accommodate a growing amount of data and network participants.
8. **Verifiability:** Allowing network participants to verify that the data is stored correctly and has not been tampered with.
9. **Resistance to Attacks:** Protecting the network from various attacks, such as data corruption, data loss, replication cheating, or denial-of-service attacks.

### How to Ensure the Node is Storing Data Correctly?

There are several challenges to achieving this:

1. How to prove and verify that the data is stored correctly and has not been tampered with?
2. How to prevent the node from cheating when storing data? For example, discarding the data after proving it is stored, or only storing proofs instead of the actual data?
3. How to prove that the node has stored the data for a certain period of time?


After researching Filecoin, I think the following methods can be used to prove and verify the data storage:

1. **Challenge-Response Proofs:** The network can periodically challenge storage nodes to prove that they are storing the data correctly. The nodes must respond with a proof that demonstrates they have the data and that it has not been tampered with. If a node fails to respond or provides an incorrect proof, it may be penalized or removed from the network.
2. **Spot-Checking:** The network can randomly select storage nodes and request that they provide a random piece of data from the stored data. This method can help verify that the data is available and that the nodes are storing it correctly.
3. **Replica Reconciliation:** The network can compare the data stored by different nodes to ensure that it matches. If there are discrepancies, the network can take action to correct the issue and penalize the nodes responsible.
4. **Periodically Proofs:** The network can require storage nodes to periodically provide proofs that they are still storing the data. This method can help prevent nodes from discarding the data after proving it is stored or only storing proofs instead of the actual data.
5. **Time-Bound Challenges:** The network can challenge storage nodes to prove that they have stored the data for a certain period of time. This method can help ensure that nodes are not cheating by storing the data temporarily and then discarding it.

These methods are very easy to understand, but the implementation is very complex. The network must design a robust system that can handle various challenges and ensure that the data is stored correctly and securely.

The generation of proofs and verification can involve zero-knowledge proofs, Merkle trees, cryptographic hashes, and other cryptographic techniques to ensure the integrity and security of the data.

### How do Filecoin implement Proof of Storage?

Filecoin is robust and effective blockchain project that uses Proof of Storage to secure their networks. 

The proof process in Filecoin must verify that the data was properly stored at the time of the initial request and continues to be stored based on the terms of the agreement between the client and the Storage Provider (SP). For the proof processes to be robust, they must:

1. **Target a random part of the data.**

2. **Occur at a time interval such that it is not possible, profitable, or rational for an SP to discard and re-fetch the copy of data.**

In Filecoin, this process consists of two distinct types of proofs:

1. **Proof of Replication (PoRep)**: a procedure used at the time of initial data storage to validate that an SP has created and stored a unique copy of a piece of data.

2. **Proof of Spacetime (PoST)**: a procedure to validate that an SP continues to store a unique copy of a piece of data.

**PoRep** is a type of **challenge-response proof**. The network challenges the SP to prove that it has stored a unique copy of the data. The SP must respond with a proof that demonstrates it has stored the data correctly and that it has not been tampered with. If the SP fails to respond or provides an incorrect proof, it may be penalized or removed from the network.

**PoST** is a type of **periodic proof**. The network challenges the SP to prove that it has stored the data for a certain period of time. The SP must respond with a proof that demonstrates it has stored the data for the required time. If the SP fails to respond or provides an incorrect proof, it may be penalized or removed from the network.

But why should **PoRep** ensure each node stores a unique copy of the data? 

Ensuring the copy is unique is necessary. Imagine if several nodes stored the same copy of the data in a central place, the network wouldn't be able to tell if the data is stored in multiple replicas or just one replica. This is a very important issue, because if the data is stored in multiple replicas, the network can tolerate some nodes going offline. However, if the data is stored in just one replica, the network can't tolerate any node going offline.

Then, how does **PoRep** ensure the copy is unique?

Filecoin performs a seal operation on the data, which is a process that takes a unique piece of data and seals it into a unique sector. The seal operation is performed by the SP and generates a proof that the data has been sealed into a sector. This proof is then verified by the network to ensure that the data is unique and has not been tampered with.

The details of the PoRep and PoST processes are beyond the scope of this article, we'll discuss them in another article.

### Conclusion

Designing a robust Proof of Storage system is very complex. In a decentralized and trustless storage system, it must ensure that the data is stored correctly, securely, and efficiently. The network must implement various methods to prove and verify the data storage, such as challenge-response proofs, spot-checking, replica reconciliation, periodic proofs, and time-bound challenges. These methods can help ensure that the data is available, accurate, and secure, and that the storage nodes are fulfilling their responsibilities.

