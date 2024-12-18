# Pricing

## How are prices determined?

As we learned in Protocol Overview, each pair on Catena swap is actually underpinned by a liquidity pool. Liquidity pools are smart contracts that hold balances of two unique tokens and enforces rules around depositing and withdrawing them. The primary rule is the constant product formula. When a token is withdrawn (bought), a proportional amount must be deposited (sold) to maintain the constant. The ratio of tokens in the pool, in combination with the constant product formula, ultimately determine the price that a swap executes at.

## Pricing Trades

When swapping tokens on Catena swap, it's common to want to receive as many output tokens as possible for an _exact input amount_, or to pay as few input tokens as possible for an _exact output amount_. In order to calculate these amounts, a contract must look up the _current reserves_ of a pair, in order to understand what the current price is. However, it is _not safe to perform this lookup and rely on the results without access to an external price_.

Say a smart contract naively wants to send 10 USDT to the USDT/WBTCC pair and receive as much WBTCC as it can get, given the current reserve ratio. If, when called, the naive smart contract simply looks up the current price and executes the trade, it is _vulnerable to front-running and will likely suffer an economic loss_. To see why, consider a malicious actor who sees this transaction before it is confirmed. They could execute a swap which dramatically changes the USDT/WBTCC price immediately before the naive swap goes through, wait for the naive swap to execute at a bad rate, and then swap to change the price back to what it was before the naive swap. This attack is fairly cheap and low-risk, and can typically be performed for a profit.

To prevent these types of attacks, it's vital to submit swaps _that have access to knowledge about the "fair" price their swap should execute at_. In other words, swaps need access to an _oracle_, to be sure that the best execution they can get from  Catena swap is close enough to what the oracle considers the "true" price. While this may sound complicated, the oracle can be as simple as an _off-chain observation of the current market price of a pair_. Because of arbitrage, it's typically the case that the ratio of the intra-block reserves of a pair is close to the "true" market price. So, if a user submits a trade with this knowledge in mind, they can ensure that the losses due to front-running are tightly bounded. This is how, for example, the  Catena swap frontend ensure trade safety. It calculates the optimal input/output amounts given observed intra-block prices, and uses the router to perform the swap, which guarantees the swap will execute at a rate no less that `x`% worse than the observed intra-block rate, where `x` is a user-specified slippage tolerance (0.5% by default).

### Exact Input[​](https://docs.uniswap.org/contracts/v2/concepts/advanced-topics/pricing#exact-input) <a href="#exact-input" id="exact-input"></a>

If you'd like to send an exact amount of input tokens in exchange for as many output tokens as possible, you'll want to use getAmountsOut.&#x20;

### Exact Output[​](https://docs.uniswap.org/contracts/v2/concepts/advanced-topics/pricing#exact-output) <a href="#exact-output" id="exact-output"></a>

If you'd like to receive an exact amount of output tokens for as few input tokens as possible, you'll want to use getAmountsIn.&#x20;
