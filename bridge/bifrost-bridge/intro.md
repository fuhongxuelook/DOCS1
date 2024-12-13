# INTRO

### What Is A Blockchain Bridge?

Blockchain bridges work similarly to real bridges in the physical world. However, instead of connecting physical locations, bridges in crypto connect two different blockchains. This connection is important because, without a bridge, blockchains are siloed environments that cannot communicate with each other. This is because each network has its own set of rules, governance mechanisms, native assets, and data that are incompatible with the other blockchains. However, with a bridge between two blockchains, it becomes possible to transfer crypto-assets and arbitrary data between them. Thus, bridges are key for interoperability in the crypto ecosystem and are necessary to make different blockchain networks compatible with each other.

### NEED FOR BRIDGES <a href="#need-for-bridges" id="need-for-bridges"></a>

Bridges exist to connect blockchain networks. They enable connectivity and interoperability between blockchains.

Blockchains exist in siloed environments, meaning there is no way for blockchains to trade and communicate with other blockchains naturally. As a result, while there could be significant activity and innovation within an ecosystem, it is limited by the lack of connectivity and interoperability with other ecosystems.

Bridges offer a way for isolated blockchain environments to connect with each other. They establish a transportation route between blockchains where tokens, messages, arbitrary data, and even smart contract calls can be transferred from one chain to another.

### BENEFITS OF BRIDGES <a href="#benefits-of-bridges" id="benefits-of-bridges"></a>

Put simply, bridges unlock numerous use cases by allowing blockchain networks to exchange data and move assets between them.

Blockchains have unique strengths, weaknesses, and approaches to building applications (such as speed, throughput, costliness, etc.). Bridges help the development of the overall crypto ecosystem by enabling blockchains to leverage the innovations of each other.

For developers, bridges enable the following:

* the transfer of any data, information, and assets across chains.
* unlocking new features and use cases for protocols as bridges expand the design space for what protocols can offer.&#x20;
* the opportunity to leverage the strengths of different blockchains.&#x20;
* collaboration among developers from various blockchain ecosystems to build new products.
* attracting users and communities from various ecosystems to their dapps.

### &#x20;<a href="#how-do-bridges-work" id="how-do-bridges-work"></a>

### &#x20;<a href="#bridge-types" id="bridge-types"></a>

### TRADE-OFFS TO CONSIDER <a href="#trade-offs" id="trade-offs"></a>

With bridges, there are no perfect solutions. Rather, there are only trade-offs made to fulfill a purpose. Developers and users can evaluate bridges based on the following factors:

* **Security –** Who verifies the system? Bridges secured by external validators are typically less secure than bridges that are locally or natively secured by the blockchain’s validators.
* **Convenience –** How long does it take to complete a transaction, and how many transactions did a user need to sign? For a developer, how long does it take to integrate a bridge, and how complex is the process?
* **Connectivity –** What are the different destination chains a bridge can connect (i.e., rollups, sidechains, other layer 1 blockchains, etc.), and how hard is it to integrate a new blockchain?
* **Ability to pass more complex data –** Can a bridge enable the transfer of messages and more complex arbitrary data across chains, or does it only support cross-chain asset transfers?
* **Cost-effectiveness –** How much does it cost to transfer assets across chains via a bridge? Typically, bridges charge a fixed or variable fee depending on gas costs and the liquidity of specific routes. It is also critical to evaluate the cost-effectiveness of a bridge based on the capital required to ensure its security.

At a high level, bridges can be categorized as trusted and trustless.

* **Trusted –** Trusted bridges are externally verified. They use an external set of verifiers (Federations with multi-sig, multi-party computation systems, oracle network) to send data across chains. As a result, they can offer great connectivity and enable fully generalized message passing across chains. They also tend to perform well with speed and cost-effectiveness. This comes at the cost of security, as users have to rely on the security of the bridge.
* **Trustless –** These bridges rely on the blockchains they are connecting and their validators to transfer messages and tokens. They are 'trustless' because they do not add new trust assumptions (in addition to the blockchains). As a result, trustless bridges are considered to be more secure than trusted bridges.

To evaluate trustless bridges based on other factors, we must break them down into generalized message passing bridges and liquidity networks.

* **Generalized message passing bridges –** These bridges excel with security and the ability to transfer more complex data across chains. Typically, they are also good with cost-effectiveness. However, these strengths generally come at the cost of connectivity for light client bridges (ex: IBC) and speed drawbacks for optimistic bridges (ex: Nomad) that use fraud proofs.
* **Liquidity networks –** These bridges use atomic swaps for transferring assets and are locally verified systems (i.e., they use the underlying blockchains’ validators to verify transactions). As a result, they excel with security and speed. Moreover, they are considered comparatively cost-effective and offer good connectivity. However, the major tradeoff is their inability to pass more complex data – as they don’t support cross-chain message passing.

### RISK WITH BRIDGES <a href="#risk-with-bridges" id="risk-with-bridges"></a>

Bridges account for the top three [biggest hacks in DeFi(opens in a new tab)](https://rekt.news/leaderboard/) and are still in the early stages of development. Using any bridge carries the following risks:

* **Smart contract risk –** While many bridges have successfully passed audits, all it takes is one flaw in a smart contract for assets to be exposed to hacks (ex: [Solana’s Wormhole Bridge(opens in a new tab)](https://rekt.news/wormhole-rekt/)).
* **Systemic financial risks** – Many bridges use wrapped assets to mint canonical versions of the original asset on a new chain. This exposes the ecosystem to systemic risk, as we have seen wrapped versions of tokens exploited.
* **Counterparty risk –** Some bridges utilize a trusted design that requires users to rely on the assumption that validators will not collude to steal user funds. The need for users to trust these third-party actors exposes them to risks such as rug pulls, censorship, and other malicious activities.
* **Open issues –** Given that bridges are in the nascent stages of development, there are many unanswered questions related to how bridges will perform in different market conditions, like times of network congestion and during unforeseen events such as network-level attacks or state rollbacks. This uncertainty poses certain risks, the degree of which is still unknown.

### HOW CAN DAPPS USE BRIDGES? <a href="#how-can-dapps-use-bridges" id="how-can-dapps-use-bridges"></a>

Here are some practical applications that developers can consider about bridges and taking their dapp cross-chain:

#### Integrating bridges <a href="#integrating-bridges" id="integrating-bridges"></a>

For developers, there are many ways to add support for bridges:

1. **Building your own bridge –** Building a secure and reliable bridge is not easy, especially if you take a more trust-minimized route. Moreover, it requires years of experience and technical expertise related to scalability and interoperability studies. Additionally, it would require a hands-on team to maintain a bridge and attract sufficient liquidity to make it feasible.
2. **Showing users multiple bridge options –** Many [dapps](https://ethereum.org/en/developers/docs/dapps/) require users to have their native token to interact with them. To enable users to access their tokens, they offer different bridge options on their website. However, this method is a quick fix to the problem as it takes the user away from the dapp interface and still requires them to interact with other dapps and bridges. This is a cumbersome onboarding experience with the increased scope of making mistakes.
3. **Integrating a bridge –** This solution doesn’t require the dapp to send users to the external bridge and DEX interfaces. It allows dapps to improve the user onboarding experience. However, this approach has its limitations:
   * Assessment and maintenance of bridges are hard and time-consuming.
   * Selecting one bridge creates a single point of failure and dependency.
   * The dapp is limited by the bridge’s capabilities.
   * Bridges alone might not be enough. Dapps might need DEXs to offer more functionality such as cross-chain swaps.
4. **Integrating multiple bridges –** This solution solves many problems associated with integrating a single bridge. However, it also has limitations, as integrating multiple bridges is resource-consuming and creates technical and communication overheads for developers—the scarcest resource in crypto.
5. **Integrating a bridge aggregator –** Another option for dapps is integrating a bridge aggregation solution that gives them access to multiple bridges. Bridge aggregators inherit the strengths of all the bridges and thus are not limited by any single bridge’s capabilities. Notably, the bridge aggregators typically maintain the bridge integrations, which saves the dapp from the hassle of staying on top of the technical and operational aspects of a bridge integration.

That being said, bridge aggregators also have their limitations. For instance, while they can offer more bridge options, many more bridges are typically available in the market other than those offered on the aggregator's platform. Moreover, just like bridges, bridge aggregators are also exposed to smart contract and technology risks (more smart contracts = more risks).

\
