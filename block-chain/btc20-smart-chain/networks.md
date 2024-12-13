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

# NETWORKS

BTC20 Smart Chain networks are groups of connected computers that communicate using the BTC20 Smart Chain protocol. There is only one BTC20 Smart Chain Mainnet, but independent networks conforming to the same protocol rules can be created for testing and development purposes. There are many independent "networks" that conform to the protocol without interacting with each other. You can even start one locally on your own computer for testing your smart contracts and web3 apps.

Your BTC20 Smart Chain account will work across the different networks, but your account balance and transaction history won't carry over from the main BTC20 Smart Chain network. For testing purposes, it's useful to know which networks are available and how to get testnet BTCC to play around with. In general, for security considerations, it's not recommended to reuse mainnet accounts on testnets or vice versa..

### PUBLIC NETWORKS <a href="#public-networks" id="public-networks"></a>

Public networks are accessible to anyone in the world with an internet connection. Anyone can read or create transactions on a public blockchain and validate the transactions being executed. The consensus among peers decides on the inclusion of transactions and the state of the network.

#### BTC20 Smart Chain Mainnet <a href="#ethereum-mainnet" id="ethereum-mainnet"></a>

Mainnet is the primary public BTC20 Smart Chain production blockchain, where actual-value transactions occur on the distributed ledger.

When people and exchanges discuss BTCC prices, they're talking about Mainnet BTCC.

#### BTC20 Smart Chain Testnets <a href="#ethereum-testnets" id="ethereum-testnets"></a>

In addition to Mainnet, there are public testnets. These are networks used by protocol developers or smart contract developers to test both protocol upgrades as well as potential smart contracts in a production-like environment before deployment to Mainnet. Think of this as an analog to production versus staging servers.

You should test any contract code you write on a testnet before deploying to Mainnet. Among dapps that integrate with existing smart contracts, most projects have copies deployed to testnets.

**Mainnet**

| key              | value                                                                            |
| ---------------- | -------------------------------------------------------------------------------- |
| network name     | BTC20 Smart Chain                                                                |
| rpc url          | <p>https://rpc.bitcoincode.technology<br>https://rpc1.bitcoincode.technology</p> |
| chainId          | 963                                                                              |
| currency symbol  | BTCC                                                                             |
| currency decimal | 18                                                                               |
| block explorer   | https://scan.bitcoincode.technology                                              |
