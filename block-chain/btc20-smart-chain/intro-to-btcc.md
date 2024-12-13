---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# INTRO TO BTCC

### WHAT IS A CRYPTOCURRENCY? <a href="#what-is-a-cryptocurrency" id="what-is-a-cryptocurrency"></a>

A cryptocurrency is a medium of exchange secured by a blockchain-based ledger.

A medium of exchange is anything widely accepted as payment for goods and services, and a ledger is a data store that keeps track of transactions. Blockchain technology allows users to make transactions on the ledger without reliance upon a trusted third party to maintain the ledger.

The first cryptocurrency was Bitcoin, created by Satoshi Nakamoto. Since Bitcoin's release in 2009, people have made thousands of cryptocurrencies across many different blockchains.

### WHAT IS BTCC? <a href="#what-is-ether" id="what-is-ether"></a>

**BTCC** is the cryptocurrency used for many things on the BTC20 Smart Chain network. Fundamentally, it is the only acceptable form of payment for transaction fees, BTCC is required to validate and propose blocks on Mainnet. BTCC is also used as a primary form of collateral in the DeFi lending markets, as a unit of account in NFT marketplaces, as payment earned for performing services or selling real-world goods, and more.

Bitcoin Smart Chain allows developers to create **decentralized applications (dapps)**, which all share a pool of computing power. This shared pool is finite, so Bitcoin Smart Chain needs a mechanism to determine who gets to use it. Otherwise, a dapp could accidentally or maliciously consume all network resources, which would block others from accessing it.

The btcc cryptocurrency supports a pricing mechanism for Bitcoin Smart Chain's computing power. When users want to make a transaction, they must pay btcc to have their transaction recognized on the blockchain. These usage costs are known as gas fees, and the gas fee depends on the amount of computing power required to execute the transaction and the network-wide demand for computing power at the time.

Therefore, even if a malicious dapp submitted an infinite loop, the transaction would eventually run out of btcc and terminate, allowing the network to return to normal.

### MINING BTCC <a href="#minting-ether" id="minting-ether"></a>

Mining is the process in which new btcc gets created on the BTC20 Smart Chain ledger. The underlying Bitcoin Smart Chain protocol creates the new btcc, and it is not possible for a user to create btcc.

Btcc is mined as a reward for miner staked in pool, each block proposed and at every epoch checkpoint for other validator activity related to reaching consensus. The circluly amount issued depends on the number of validators and how many miner staked. This block reward is divided equally among validators in the ideal case that all validators are honest and online, but in reality, it varies based on validator performance. About 1/8 of the block reward goes to the block proposer; the remainder is distributed across the other validators. Block proposers also receive tips from transaction fees and MEV-related income, but these come from recycled btcc, not new issuance.

### DENOMINATIONS OF BTCC <a href="#denominations" id="denominations"></a>

Since the value of many transactions on BTC20 Smart Chain are small, btcc has several denominations which may be referenced as smaller units of account. Of these denominations, Wei and gwei are particularly important.

Wei is the smallest possible amount of btcc, and as a result, many technical implementations

Gwei, short for giga-wei, is often used to describe gas costs on BTC20 Smart Chain.

| Denomination | Value In BTCC | Common Usage              |
| ------------ | ------------- | ------------------------- |
| Wei          | 10-18         | Technical implementations |
| Gwei         | 10-9          | Human-readable gas fees   |

### TRANSFERRING BTCC <a href="#transferring-ether" id="transferring-ether"></a>

Each transaction on BTC20 Smart Chain contains a `value` field, which specifies the amount of btcc to be transferred, denominated in wei, to send from the sender's address to the recipient address.

When the recipient address is a smart contract, this transferred btcc may be used to pay for gas when the smart contract executes its code.

### QUERYING BTCC <a href="#querying-ether" id="querying-ether"></a>

Users can query the btcc balance of any account by inspecting the account's `balance` field, which shows btcc holdings denominated in wei.

[Scan(opens in a new tab)](https://scan.bitcoincode.technology/) is a popular tool to inspect address balances via a web-based application.&#x20;

### TOTAL SUPPLY <a href="#further-reading" id="further-reading"></a>

21,000,000 BTCC
