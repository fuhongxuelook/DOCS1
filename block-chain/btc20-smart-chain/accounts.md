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

# ACCOUNTS

BTC20 Smart Chain account is an entity with an BTCC balance that can send transactions on BTC20 Smart Chain. Accounts can be user-controlled or deployed as smart contracts.

### ACCOUNT TYPES <a href="#types-of-account" id="types-of-account"></a>

BTC20 Smart Chain has two account types:

* Externally-owned account (EOA) – controlled by anyone with the private keys
* Contract account – a smart contract deployed to the network, controlled by code. Learn about smart contracts

Both account types have the ability to:

* Receive, hold and send BTCC and tokens
* Interact with deployed smart contracts

#### Key differences <a href="#key-differences" id="key-differences"></a>

**Externally-owned**

* Creating an account costs nothing
* Can initiate transactions
* Transactions between externally-owned accounts can only be BTCC/token transfers
* Made up of a cryptographic pair of keys: public and private keys that control account activities

**Contract**

* Creating a contract has a cost because you're using network storage
* Can only send transactions in response to receiving a transaction
* Transactions from an external account to a contract account can trigger code which can execute many different actions, such as transferring tokens or even creating a new contract
* Contract accounts don't have private keys. Instead, they are controlled by the logic of the smart contract code

### AN ACCOUNT EXAMINED <a href="#an-account-examined" id="an-account-examined"></a>

BTC20 Smart Chain accounts have four fields:

* `nonce` – A counter that indicates the number of transactions sent from an externally-owned account or the number of contracts created by a contract account. Only one transaction with a given nonce can be executed for each account, protecting against replay attacks where signed transactions are repeatedly broadcast and re-executed.
* `balance` – The number of wei owned by this address. Wei is a denomination of BTCC and there are 1e+18 wei per BTCC.
* `codeHash` – This hash refers to the _code_ of an account on the EVM. Contract accounts have code fragments programmed in that can perform different operations. This EVM code gets executed if the account gets a message call. It cannot be changed, unlike the other account fields. All such code fragments are contained in the state database under their corresponding hashes for later retrieval. This hash value is known as a codeHash. For externally owned accounts, the codeHash field is the hash of an empty string.
* `storageRoot` – Sometimes known as a storage hash. A 256-bit hash of the root node of a Merkle Patricia trie that encodes the storage contents of the account (a mapping between 256-bit integer values), encoded into the trie as a mapping from the Keccak 256-bit hash of the 256-bit integer keys to the RLP-encoded 256-bit integer values. This trie encodes the hash of the storage contents of this account, and is empty by default.

[![A diagram showing the make up of an account](https://ethereum.org/static/19443ab40f108c985fb95b07bac29bcb/302a4/accounts.png)](https://ethereum.org/static/19443ab40f108c985fb95b07bac29bcb/302a4/accounts.png)

### EXTERNALLY-OWNED ACCOUNTS AND KEY PAIRS <a href="#externally-owned-accounts-and-key-pairs" id="externally-owned-accounts-and-key-pairs"></a>

An account is made up of a cryptographic pair of keys: public and private. They help prove that a transaction was actually signed by the sender and prevent forgeries. Your private key is what you use to sign transactions, so it grants you custody over the funds associated with your account. You never really hold cryptocurrency, you hold private keys – the funds are always on BTC20 Smart Chain's ledger.

This prevents malicious actors from broadcasting fake transactions because you can always verify the sender of a transaction.

If Alice wants to send BTCC from her own account to Bob’s account, Alice needs to create a transaction request and send it out to the network for verification. BTC20 Smart Chain's usage of public-key cryptography ensures that Alice can prove that she originally initiated the transaction request. Without cryptographic mechanisms, a malicious adversary Eve could simply publicly broadcast a request that looks something like “send 5 BTCC from Alice’s account to Eve’s account,” and no one would be able to verify that it didn’t come from Alice.

### ACCOUNT CREATION <a href="#account-creation" id="account-creation"></a>

When you want to create an account most libraries will generate you a random private key.

A private key is made up of 64 hex characters and can be encrypted with a password.

Example:

`fffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd036415f`

The public key is generated from the private key using the [Elliptic Curve Digital Signature Algorithm(opens in a new tab)](https://wikipedia.org/wiki/Elliptic_Curve_Digital_Signature_Algorithm). You get a public address for your account by taking the last 20 bytes of the Keccak-256 hash of the public key and adding `0x` to the beginning.

It is possible to derive new public keys from your private key but you cannot derive a private key from public keys. This means it's vital to keep a private key safe and, as the name suggests, **PRIVATE**.

You need a private key to sign messages and transactions which output a signature. Others can then take the signature to derive your public key, proving the author of the message. In your application, you can use a javascript library to send transactions to the network.

### CONTRACT ACCOUNTS <a href="#contract-accounts" id="contract-accounts"></a>

Contract accounts also have a 42 character hexadecimal address:

Example:

`0x06012c8cf97bead5deae237070f9587f8e7a266d`

The contract address is usually given when a contract is deployed to the BTC20 Smart Chain. The address comes from the creator's address and the number of transactions sent from that address (the “nonce”).

### VALIDATOR KEYS <a href="#validators-keys" id="validators-keys"></a>

There is also another type of key in BTC20 Smart Chain. These are 'BLS' keys and they are used to identify validators. These keys can be efficiently aggregated to reduce the bandwidth required for the network to come to consensus. Without this key aggregation the minimum stake for a validator would be much higher.

### A NOTE ON WALLETS <a href="#a-note-on-wallets" id="a-note-on-wallets"></a>

An account is not a wallet. An account is the keypair for a user-owned BTC20 Smart Chain account. A wallet is an interface or application that lets you interact with your BTC20 Smart Chain account.

\
