---
title: "Blockchain for Beginners"
teaching: 10
exercises: 0
questions:
- "What is a Blockcahin?"
- "How is that related to a Bitcoin?"
- "What is a Smart Contract?"
objectives:
- "Understand the Blockchain ecosystem and history."
keypoints:
- "A Blockchain is a decentralised database."
- "Bitcoin was first, then many more"
- "Many tools are availble to interact with the blockchain ecosystem."
---
The **blockchain** is the distributed immutable database that drives cryptocurrencies and smart contracts.
A series of transaction pools (blocks) connected by a hash pointer (chain).

<br>

# Blockchain Ecosystem

Some key words that might come up:

* [Bitcoin](https://bitcoin.org/en/), [Ethereum](https://ethereum.org/en/), [Cardano](https://cardano.org/), [Hyperledger](https://www.hyperledger.org/about)
* Cryptocurrency, (ERC) Token, NFT
* [Solidity](https://docs.soliditylang.org/en/v0.8.4/)
* Smart Contracts
* [Truffle, Ganace](https://www.trufflesuite.com/), [Metamask](https://metamask.io/), [etherum remix](https://remix.ethereum.org/), [web3.js](https://web3js.readthedocs.io/), [infura](https://infura.io/).
* Wallets, addresses, hashes

<br>

# Technology behind blockchain

* [Public-key (asymmetric) cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography)
* [Hash functions](https://emn178.github.io/online-tools/sha256.html)
* [Merkel Trees](https://upload.wikimedia.org/wikipedia/commons/9/95/Hash_Tree.svg)
* [Zero Knowledge Proofs](https://hackernoon.com/eli5-zero-knowledge-proof-78a276db9eff)

<br>

# There are many blockchains

[Bitcoin was the first](https://bitcoin.org/bitcoin.pdf) after [Satoshi Nakamoto](https://en.wikipedia.org/wiki/Satoshi_Nakamoto) solved the ["Double-Spending" problem](https://www.investopedia.com/terms/d/doublespending.asp).

[Hyperledger](https://www.hyperledger.org/about) is a popular framework for developing new blockchain technologies that may be public, private (permissioned), or some hybrid implementation.

Mining is one way to validate all the transactions that have taken place on a network AND to reward participants who have done that computational work. So this is not strictly necessary for all blockchains. 

From the original blocks mined: 1,148,800 BTC have never been spent [(ref>)](https://bitslog.com/2013/04/17/the-well-deserved-fortune-of-satoshi-nakamoto/).

<br>

# Blockchain Explorer
Visit *the blockchain* at (https://etherscan.io/) or (https://www.blockchain.com/explorer) and see live transactions. Everything is stored in the ledger.

<br>

# Uses for Blockchain

* Distributed finance
* Supply chain tracking
* Insurance 
* Fraud and counterfeit authentication
* Idenity managment 

<br>

# What are we going to do today

* Write a contract in solidity.
* Deploy the contract to the (a) blockchain.
* Use the contract and watch the transactions be stored in the blocks.
