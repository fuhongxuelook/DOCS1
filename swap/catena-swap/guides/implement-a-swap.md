# Implement a Swap

When trading from a smart contract, the most important thing to keep in mind is that access to an external price source is _required_. Without this, trades can be frontrun for considerable loss.

## Using the Router

The easiest way to safely swap tokens is to use the router, which provides a variety of methods to safely swap to and from different assets. You'll notice that there is a function for each permutation of swapping to/from an exact amount of BTCC/tokens.

First you must use an external price source to calculate the safety parameters for the function you'd like to call. This is either a minimum amount received when selling an exact input or the maximum amount you are willing to pay when a buying an exact output amount

It is also important to ensure that your contract controls enough BTCC/tokens to make the swap, and has granted approval to the router to withdraw this many tokens.

### transferFrom[​](https://docs.uniswap.org/contracts/v2/guides/smart-contract-integration/trading-from-a-smart-contract#transferfrom) <a href="#transferfrom" id="transferfrom"></a>

Before swapping, our smart contracts needs to be in control of 50 USDT. The easiest way to accomplish this is by calling `transferFrom` on USDT with the owner set to `msg.sender`:

```
uint amountIn = 50 * 10 ** DAI.decimals();
require(USDT.transferFrom(msg.sender, address(this), amountIn), 'transferFrom failed.');
```

### approve[​](https://docs.uniswap.org/contracts/v2/guides/smart-contract-integration/trading-from-a-smart-contract#approve) <a href="#approve" id="approve"></a>

Now that our contract owns 50 USDT, we need to approve to the router to withdraw this USDT:

```
require(USDT.approve(address(router), amountIn), 'approve failed.');
```

## Safety Considerations

Because BTC20 Smart Chain transactions occur in an adversarial environment, smart contracts that do not perform safety checks _can be exploited for profit_. If a smart contract assumes that the current price on Catena swap is a "fair" price without performing safety checks, _it is vulnerable to manipulation_. A bad actor could e.g. easily insert transactions before and after the swap (a "sandwich" attack) causing the smart contract to trade at a much worse price, profit from this at the trader's expense, and then return the contracts to their original state. (One important caveat is that these types of attacks are mitigated by trading in extremely liquid pools, and/or at low values.)

The best way to protect against these attacks is to use an external price feed or "price oracle". The best "oracle" is simply _traders' off-chain observation of the current price_, which can be passed into the trade as a safety check. This strategy is best for situations _where users initiate trades on their own behalf_.
