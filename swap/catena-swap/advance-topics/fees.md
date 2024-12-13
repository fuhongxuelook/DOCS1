# Fees

### Liquidity provider fees[​](https://docs.uniswap.org/contracts/v2/concepts/advanced-topics/fees#liquidity-provider-fees) <a href="#liquidity-provider-fees" id="liquidity-provider-fees"></a>

There is a **0.3%** fee for swapping tokens. **This fee is split by liquidity providers proportional to their contribution to liquidity reserves.**

Swapping fees are immediately deposited into liquidity reserves. This increases the value of liquidity tokens, functioning as a payout to all liquidity providers proportional to their share of the pool. Fees are collected by burning liquidity tokens to remove a proportional share of the underlying reserves.

Since fees are added to liquidity pools, the invariant increases at the end of every trade. Within a single transaction, the invariant represents `token0_pool / token1_pool` at the end of the previous transaction.

### Protocol Fees[​](https://docs.uniswap.org/contracts/v2/concepts/advanced-topics/fees#protocol-fees) <a href="#protocol-fees" id="protocol-fees"></a>

At the moment there are no protocol fees. However, it is possible for a 0.05% fee to be turned on in the future.

### Protocol Charge Calculation[​](https://docs.uniswap.org/contracts/v2/concepts/advanced-topics/fees#protocol-charge-calculation) <a href="#protocol-charge-calculation" id="protocol-charge-calculation"></a>

In the future, it is possible that a protocol-wide charge of 0.05% per trade will take effect. This represents ⅙th (16.6̅%) of the 0.30% fee. The fee is in effect if feeTo is not `address(0)` (`0x0000000000000000000000000000000000000000`), indicating that feeTo is the recipient of the charge.

This amount would not affect the fee paid by traders, but would affect the amount received by liquidity providers.
