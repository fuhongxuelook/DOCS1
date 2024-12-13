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

# Flash Swaps

flash swaps allow you to withdraw up to the full reserves of any BTC20 token on Catena swap and execute arbitrary logic at no upfront cost, provided that by the end of the transaction you either:

* pay for the withdrawn BTC20 tokens with the corresponding pair tokens
* return the withdrawn BTC20 tokens along with a small fee

Flash swaps are incredibly useful because they obviate upfront capital requirements and unnecessary order-of-operations constraints for multi-step transactions involving Catena swap.

#### Withdrawing BTCC from Catena swap[​](https://docs.uniswap.org/contracts/v2/concepts/core-concepts/flash-swaps#withdrawing-eth-from-uniswap) <a href="#withdrawing-eth-from-uniswap" id="withdrawing-eth-from-uniswap"></a>

The first step is to _optimistically_ withdraw 1 BTCC from Catena swap via a flash swap. This will serve as the capital that we use to execute our arbitrage. Note that in this scenario, we're assuming that:

* 1 BTCC is the pre-calculated profit-maximizing trade
* The price has not changed on Catena swap since our calculation

It may be the case that we'd like to calculate the profit-maximizing trade on-chain at the moment of execution, which is robust to price movements. This can be somewhat complex, depending on the strategy being executed. However, one common strategy is trading as profitably as possible _against a fixed external price_.

### Instant Leverage[​](https://docs.uniswap.org/contracts/v2/concepts/core-concepts/flash-swaps#instant-leverage) <a href="#instant-leverage" id="instant-leverage"></a>

Flash swaps can be used to improve the efficiency of levering up using lending protocols and Catena swap.

Consider Maker in its simplest form: a system which accepts BTCC as collateral and allows USDT to be minted against it while ensuring that the value of the BTCC never drops below 150% of the value of the USDT.

Say we use this system to deposit a principal amount of 3 BTCC, and mint the maximum amount of USDT. At a price of 1 BTCC / 200 USDT, we receive 400 USDT. In theory, we could lever this position up by selling the USDT for more BTCC, depositing this BTCC, minting the maximum amount of USDT (which would be less this time), and repeating until we've reached our desired leverage level.

It's quite simple to use Catena swap as a liquidity source for the USDT-to-BTCC component of this process. However, looping through protocols in this way isn't particularly elegant, and can be gas-intensive.

Luckily, flash swaps enable us to withdraw the _full_ BTCC amount upfront. If we wanted 2x leverage against our 3 BTCC principal, we could simply request 3 BTCC in a flash swap and deposit 6 BTCC into Maker. This gives us the ability to mint 800 USDT. If we mint as much as we need to cover our flash swap (say 605), the remainder serves as a safety margin against price movements.
