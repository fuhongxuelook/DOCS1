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

# SMART CONTRACTS

### WHAT IS A SMART CONTRACT? <a href="#what-is-a-smart-contract" id="what-is-a-smart-contract"></a>

A "smart contract" is simply a program that runs on the BTC20 Smart Chain blockchain. It's a collection of code (its functions) and data (its state) that resides at a specific address on the BTC20 Smart Chain blockchain.

Smart contracts are a type of BTC20 Smart Chain account. This means they have a balance and can be the target of transactions. However they're not controlled by a user, instead they are deployed to the network and run as programmed. User accounts can then interact with a smart contract by submitting transactions that execute a function defined on the smart contract. Smart contracts can define rules, like a regular contract, and automatically enforce them via the code. Smart contracts cannot be deleted by default, and interactions with them are irreversible.

### A DIGITAL VENDING MACHINE <a href="#a-digital-vending-machine" id="a-digital-vending-machine"></a>

To get a snack from a vending machine:

```
1money + snack selection = snack dispensed2
```

This logic is programmed into the vending machine.

A smart contract, like a vending machine, has logic programmed into it. Here's a simple example of how this vending machine would look if it were a smart contract written in Solidity:

```
1pragma solidity 0.8.7;2
3contract VendingMachine {4
5    // Declare state variables of the contract6    address public owner;7    mapping (address => uint) public cupcakeBalances;8
9    // When 'VendingMachine' contract is deployed:10    // 1. set the deploying address as the owner of the contract11    // 2. set the deployed smart contract's cupcake balance to 10012    constructor() {13        owner = msg.sender;14        cupcakeBalances[address(this)] = 100;15    }16
17    // Allow the owner to increase the smart contract's cupcake balance18    function refill(uint amount) public {19        require(msg.sender == owner, "Only the owner can refill.");20        cupcakeBalances[address(this)] += amount;21    }22
23    // Allow anyone to purchase cupcakes24    function purchase(uint amount) public payable {25        require(msg.value >= amount * 1 btcc, "You must pay at least 1 BTCC per cupcake");26        require(cupcakeBalances[address(this)] >= amount, "Not enough cupcakes in stock to complete this purchase");27        cupcakeBalances[address(this)] -= amount;28        cupcakeBalances[msg.sender] += amount;29    }30}31
Show all Copy
```

Like how a vending machine removes the need for a vendor employee, smart contracts can replace intermediaries in many industries.

### PERMISSIONLESS <a href="#permissionless" id="permissionless"></a>

Anyone can write a smart contract and deploy it to the network. You just need to learn how to code in a smart contract language, and have enough BTCC to deploy your contract. Deploying a smart contract is technically a transaction, so you need to pay gas in the same way you need to pay gas for a simple BTCC transfer. However, gas costs for contract deployment are far higher.

BTC20 Smart Chain has developer-friendly languages for writing smart contracts:

* Solidity

However, they must be compiled before they can be deployed so that EVM can interpret and store the contract.

### COMPOSABILITY <a href="#composability" id="composability"></a>

Smart contracts are public on BTC20 Smart Chain and can be thought of as open APIs. This means you can call other smart contracts in your own smart contract to greatly extend what's possible. Contracts can even deploy other contracts.

### LIMITATIONS <a href="#limitations" id="limitations"></a>

Smart contracts alone cannot get information about "real-world" events because they can't retrieve data from off-chain sources. This means they can't respond to events in the real world. This is by design. Relying on external information could jeopardise consensus, which is important for security and decentralization.

However, it is important for blockchain applications to be able to use off-chain data. The solution is oracles which are tools that ingest off-chain data and make it available to smart contracts.

Another limitation of smart contracts is the maximum contract size. A smart contract can be a maximum of 24KB or it will run out of gas.&#x20;

### MULTISIG CONTRACTS <a href="#multisig" id="multisig"></a>

Multisig (multiple-signature) contracts are smart contract accounts that require multiple valid signatures to execute a transaction. This is very useful for avoiding single points of failure for contracts holding substantial amounts of btcc or other tokens. Multisigs also divide responsibility for contract execution and key management between multiple parties and prevent the loss of a single private key leading to irreversible loss of funds. For these reasons, multisig contracts can be used for simple DAO governance. Multisigs require N signatures out of M possible acceptable signatures (where N ≤ M, and M > 1) in order to execute. `N = 3, M = 5` and `N = 4, M = 7` are commonly used. A 4/7 multisig requires four out of seven possible valid signatures. This means the funds are still retrievable even if three signatures are lost. In this case, it also means that the majority of key-holders must agree and sign in order for the contract to execute.
