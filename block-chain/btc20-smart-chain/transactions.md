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

# TRANSACTIONS

Transactions are cryptographically signed instructions from accounts. An account will initiate a transaction to update the state of the BTC20 Smart Chain network. The simplest transaction is transferring BTCC from one account to another.

### WHAT'S A TRANSACTION? <a href="#whats-a-transaction" id="whats-a-transaction"></a>

BTC20 Smart Chain transaction refers to an action initiated by an externally-owned account, in other words an account managed by a human, not a contract. For example, if Bob sends Alice 1 BTCC, Bob's account must be debited and Alice's must be credited. This state-changing action takes place within a transaction.

[![Diagram showing a transaction cause state change](https://ethereum.org/static/570dedb843948d6bef5e21a6769d5c35/302a4/tx.png)](https://ethereum.org/static/570dedb843948d6bef5e21a6769d5c35/302a4/tx.png)

Transactions, which change the state of the EVM, need to be broadcast to the whole network. Any node can broadcast a request for a transaction to be executed on the EVM; after this happens, a validator will execute the transaction and propagate the resulting state change to the rest of the network.

Transactions require a fee and must be included in a validated block. To make this overview simpler we'll cover gas fees and validation elsewhere.

A submitted transaction includes the following information:

* `from` – the address of the sender, that will be signing the transaction. This will be an externally-owned account as contract accounts cannot send transactions.
* `recipient` – the receiving address (if an externally-owned account, the transaction will transfer value. If a contract account, the transaction will execute the contract code)
* `signature` – the identifier of the sender. This is generated when the sender's private key signs the transaction and confirms the sender has authorized this transaction
* `nonce` - a sequentially incrementing counter which indicates the transaction number from the account
* `value` – amount of BTCC to transfer from sender to recipient (denominated in WEI, where 1 BTCC equals 1e+18wei)
* `input data` – optional field to include arbitrary data
* `gasLimit` – the maximum amount of gas units that can be consumed by the transaction. The EVM specifies the units of gas required by each computational step
* `maxPriorityFeePerGas` - the maximum price of the consumed gas to be included as a tip to the validator
* `maxFeePerGas` - the maximum fee per unit of gas willing to be paid for the transaction (inclusive of `baseFeePerGas` and `maxPriorityFeePerGas`)

Gas is a reference to the computation required to process the transaction by a validator. Users have to pay a fee for this computation. The `gasLimit`, and `maxPriorityFeePerGas` determine the maximum transaction fee paid to the validator.&#x20;

The transaction object will look a little like this:

```
1{2  from: "0xEA674fdDe714fd979de3EdF0F56AA9716B898ec8",3  to: "0xac03bb73b6a9e108530aff4df5077c2b3d481e5a",4  gasLimit: "21000",5  maxFeePerGas: "300",6  maxPriorityFeePerGas: "10",7  nonce: "0",8  value: "10000000000"9}10
Show all Copy
```

But a transaction object needs to be signed using the sender's private key. This proves that the transaction could only have come from the sender and was not sent fraudulently.

BTC20 Smart Chain client will handle this signing process.

Example JSON-RPC call:

```
1{2  "id": 2,3  "jsonrpc": "2.0",4  "method": "account_signTransaction",5  "params": [6    {7      "from": "0x1923f626bb8dc025849e00f99c25fe2b2f7fb0db",8      "gas": "0x55555",9      "maxFeePerGas": "0x1234",10      "maxPriorityFeePerGas": "0x1234",11      "input": "0xabcd",12      "nonce": "0x0",13      "to": "0x07a565b7ed7d7a678680a4c162885bedbb695fe0",14      "value": "0x1234"15    }16  ]17}18
Show all Copy
```

Example response:

```
1{2  "jsonrpc": "2.0",3  "id": 2,4  "result": {5    "raw": "0xf88380018203339407a565b7ed7d7a678680a4c162885bedbb695fe080a44401a6e4000000000000000000000000000000000000000000000000000000000000001226a0223a7c9bcf5531c99be5ea7082183816eb20cfe0bbc322e97cc5c7f71ab8b20ea02aadee6b34b45bb15bc42d9c09de4a6754e7000908da72d48cc7704971491663",6    "tx": {7      "nonce": "0x0",8      "maxFeePerGas": "0x1234",9      "maxPriorityFeePerGas": "0x1234",10      "gas": "0x55555",11      "to": "0x07a565b7ed7d7a678680a4c162885bedbb695fe0",12      "value": "0x1234",13      "input": "0xabcd",14      "v": "0x26",15      "r": "0x223a7c9bcf5531c99be5ea7082183816eb20cfe0bbc322e97cc5c7f71ab8b20e",16      "s": "0x2aadee6b34b45bb15bc42d9c09de4a6754e7000908da72d48cc7704971491663",17      "hash": "0xeba2df809e7a612a0a0d444ccfa5c839624bdc00dd29e3340d46df3870f8a30e"18    }19  }20}21
Show all Copy
```

* the `raw` is the signed transaction in Recursive Length Prefix (RLP) encoded form
* the `tx` is the signed transaction in JSON form

With the signature hash, the transaction can be cryptographically proven that it came from the sender and submitted to the network.

#### The data field <a href="#the-data-field" id="the-data-field"></a>

The vast majority of transactions access a contract from an externally-owned account. Most contracts are written in Solidity and interpret their data field in accordance with the&#x20;

application binary interface (ABI).

The first four bytes specify which function to call, using the hash of the function's name and arguments. You can sometimes identify the function from the selector using [this database(opens in a new tab)](https://www.4byte.directory/signatures/).

The rest of the calldata is the arguments, [encoded as specified in the ABI specs(opens in a new tab)](https://docs.soliditylang.org/en/latest/abi-spec.html#formal-specification-of-the-encoding).

For example, lets look at [this transaction(opens in a new tab)](https://etherscan.io/tx/0xd0dcbe007569fcfa1902dae0ab8b4e078efe42e231786312289b1eee5590f6a1). Use **Click to see More** to see the calldata.

The function selector is `0xa9059cbb`. There are several [known functions with this signature(opens in a new tab)](https://www.4byte.directory/signatures/?bytes4_signature=0xa9059cbb). In this case [the contract source code(opens in a new tab)](https://etherscan.io/address/0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48#code) has been uploaded to btccscan, so we know the function is `transfer(address,uint256)`.

The rest of the data is:

```
10000000000000000000000004f6742badb049791cd9a37ea913f2bac38d012792000000000000000000000000000000000000000000000000000000003b0559f43
```

According to the ABI specifications, integer values (such as addresses, which are 20-byte integers) appear in the ABI as 32-byte words, padded with zeros in the front. So we know that the `to` address is [`4f6742badb049791cd9a37ea913f2bac38d01279`(opens in a new tab)](https://etherscan.io/address/0x4f6742badb049791cd9a37ea913f2bac38d01279). The `value` is 0x3b0559f4 = 990206452.

### TYPES OF TRANSACTIONS <a href="#types-of-transactions" id="types-of-transactions"></a>

On BTC20 Smart Chain there are a few different types of transactions:

* Regular transactions: a transaction from one account to another.
* Contract deployment transactions: a transaction without a 'to' address, where the data field is used for the contract code.
* Execution of a contract: a transaction that interacts with a deployed smart contract. In this case, 'to' address is the smart contract address.

#### On gas <a href="#on-gas" id="on-gas"></a>

As mentioned, transactions cost [gas](https://ethereum.org/en/developers/docs/gas/) to execute. Simple transfer transactions require 21000 units of Gas.

So for Bob to send Alice 1 BTCC at a `baseFeePerGas` of 190 gwei and `maxPriorityFeePerGas` of 10 gwei, Bob will need to pay the following fee:

```
1(190 + 10) * 21000 = 4,200,000 gwei2--or--30.0042 BTCC4
```

Bob's account will be debited **-1.0042 BTCC** (1 BTCC for Alice + 0.0042 BTCC in gas fees)

Alice's account will be credited **+1.0 BTCC**

The base fee will be burned **-0.00399 BTCC**

Validator keeps the tip **+0.000210 BTCC**

Gas is required for any smart contract interaction too.

[![Diagram showing how unused gas is refunded](https://ethereum.org/static/c3638b26a1210d2c73a7ec2335c57351/302a4/gas-tx.png)](https://ethereum.org/static/c3638b26a1210d2c73a7ec2335c57351/302a4/gas-tx.png)

Any gas not used in a transaction is refunded to the user account.

### TRANSACTION LIFECYCLE <a href="#transaction-lifecycle" id="transaction-lifecycle"></a>

Once the transaction has been submitted the following happens:

1. A transaction hash is cryptographically generated: `0x97d99bc7729211111a21b12c933c949d4f31684f1d6954ff477d0477538ff017`
2. The transaction is then broadcasted to the network and added to a transaction pool consisting of all other pending network transactions.
3. A validator must pick your transaction and include it in a block in order to verify the transaction and consider it "successful".
4. As time passes the block containing your transaction will be upgraded to "justified" then "finalized". These upgrades make it much more certain that your transaction was successful and will never be altered. Once a block is "finalized" it could only ever be changed by a network level attack that would cost many billions of dollars.

\
