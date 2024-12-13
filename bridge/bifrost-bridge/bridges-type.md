# BRIDGES TYPE?

While there are many [types of bridge designs(opens in a new tab)](https://li.fi/knowledge-hub/blockchain-bridges-and-classification/), three ways to facilitate the cross-chain transfer of assets stand out:

* **Lock and mint –** Lock assets on the source chain and mint assets on the destination chain.
* **Burn and mint –** Burn assets on the source chain and mint assets on the destination chain.
* **Atomic swaps –** Swap assets on the source chain for assets on the destination chain with another party.

Bridges can usually be classified into one of the following buckets:

* **Native bridges –** These bridges are typically built to bootstrap liquidity on a particular blockchain, making it easier for users to move funds to the ecosystem. For example, the Arbitrum Bridge is built to make it convenient for users to bridge from Ethereum Mainnet to Arbitrum. Other such bridges include Polygon PoS Bridge, Optimism Gateway, etc.
* **Validator or oracle based bridges –** These bridges rely on an external validator set or oracles to validate cross-chain transfers. Examples: Multichain and Across.
* **Generalized message passing bridges –** These bridges can transfer assets, along with messages and arbitrary data across chains. Examples: Nomad and LayerZero.
* **Liquidity networks –** These bridges primarily focus on transferring assets from one chain to another via atomic swaps. Generally, they don’t support cross-chain message passing. Examples: Connext and Hop.

### Why Are There Different Types Of Bridges?

Bridges essentially enable communication between different blockchains. And, just like with complex math problems, when you take a look at different bridging solutions in the crypto ecosystem, you will find that there is no one way of enabling communication between blockchains. Bridges have different designs with unique strengths and trade-offs, and thus, there are a plethora of options when it comes to which bridge can be used to communicate between two blockchain networks. Let’s dig a little deeper into how communication works.

Bridges work by establishing communication channels between two blockchains. In an ideal world, blockchains would just talk to each other but in reality, that’s not possible because one blockchain doesn’t store the state of the other.
