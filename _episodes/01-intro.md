---
title: "1. Blockchain for Beginners"
teaching: 10
exercises: 0
questions:
- "What is a Blockcahin"
- "How is that related to a Bitcoin?"
- "What is a Smart Contract?"
objectives:
- "Understand the Blockchain ecosystem and history."
keypoints:
- "SIH is availble to researchers to help them research!"
- "A Blockchain is a decentralised database."
- "Bitcoin was first, then many more".
- "Many tools are availble to interact with the blockchain ecosystem".
---
This episode introduces the [Sydney Informatics Hub](https://informatics.sydney.edu.au/), and provides a brief background on Blockchain tecnhology and the tools and terminology within the ecosystem.


# The Sydney Informatics Hub

The Sydney Informatics Hub (SIH) is a _[Core Research Facility](https://sydney.edu.au/research/facilities.html)_ of the University of Sydney. Core Research Facilities centralise essential research equipment and services that would otherwise be too expensive or impractical for individual Faculties to purchase and maintain. The classic example might be the room-size electron-microscopes, built into specialised rooms in the Sydney Microscopy & Microanalysis unit.

<figure>
  <img src="{{ page.root }}/fig/01_crf.png" style="margin:10px;width:600px"/>
  <figcaption> USyd Core Research Facilities <a href="https://sydney.edu.au/research/facilities.html">https://sydney.edu.au/research/facilities.html</a></figcaption>
</figure><br>

**Artemis HPC** itself is a multi-million dollar set of equipment, a 'supercomputer', and is the main piece of equipment supported by SIH. However, we also provide a wide range of research services to aid investigators, such as:

* [Training and workshops](https://sydney.edu.au/research/facilities/sydney-informatics-hub/workshops-and-training.html)
* [Project consulting and assisstance](https://sydney.edu.au/research/facilities/sydney-informatics-hub/project-support.html) with Statistics, Data Science, Research Engineering, Bioinformatics, Modeling/Simulation/Visualisation.
* [Research data management](https://sydney.edu.au/research/facilities/sydney-informatics-hub/digital-research-infrastructure.html) consulting and platform support.

We also aim to cultivate a **data community** at USyd, organising monthly [Hacky Hours](https://sydney.edu.au/research/facilities/sydney-informatics-hub/workshops-and-training/hacky-hour.html), outside training events (eg NVIDIA, Pawsey Center), and data/coding-related events. Look out for everthing happening on our [calander](https://www.sydney.edu.au/research/facilities/sydney-informatics-hub/workshops-and-training/training-calendar.html) or contact us (at sih.info@sydney.edu.au) to get some digital collaboration going.

<br>

# Course pre-requisites
Background in coding will be helpful.

<br>

# Blockchain Ecosystem

The **blockchain** is the distributed immutable database that drives cryptocurrencies and smart contracts.
A series of transaction pools (blocks) connected by a hash pointer (chain).

Some key words that might come up:

* Bitcoin, Ethereum, Cardano, Hyperledger 
* Cryptocurrency
* Solidity
* Smart Contracts
* Truffle, Ganace, Metamask, etherum remix, web3.js, infura.
* Wallets, addresses, hashes

<br>

# Technology behind blockchain

* Public-key (asymmetric) cryptography 
* Hash functions
* Merkel Trees
* Zero Knowledge Proofs

# There are many blockchains

Bitcoin was the first. https://bitcoin.org/bitcoin.pdf

Satoshi Nakamoto: https://en.wikipedia.org/wiki/Satoshi_Nakamoto

Public or private (permissioned) or hybrid blockchains.

From the original blocks mined: 1,148,800 BTC has never been spent [(ref>)](https://bitslog.com/2013/04/17/the-well-deserved-fortune-of-satoshi-nakamoto/).

https://www.hyperledger.org/about

# Blockchain Explorer
Visit *the blockchain* at https://etherscan.io/ or https://www.blockchain.com/explorer and see live transactions. Everything is stored in the ledger.

# Uses for Blockchain

* Distributed finance
* Supply chain tracking
* Insurance 
* Fraud and counterfeit authentication
* Idenity managment 

# What are we going to do

* Write a contract in solidity.
* Deploy the contract to a network.
* Use the contract and watch the transactions be stored in the blocks.
