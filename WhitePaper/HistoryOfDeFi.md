# FORT: A DeFi Development and Application System with Unlimited Liquidity

> James Zhao, September 9, 2021

---

## History of DeFi

Decentralized finance, as known as DeFi, is the fastest growing application in the blockchain
world and it has found a real demand. The history of DeFi can be traced back to the
early days of orderbook-based on-chain transactions, as well as peer-to-peer lending.
Some applications gained some attention around 2017, but due to the extremely high cost of on-chain brokering and the lack of decentralized oracle, this group of projects did
not grow. Instead, Uniswap based on the AMM mechanism; Compound and MakerDao,
lending protocols based on fund pools and asset prices, grew rapidly and led the wave of
DeFi. Because this type of project better solves the fundamental contradiction of DeFi:
lack of on-chain liquidity.

But no matter AMM or fund pool, its solution to liquidity problems is at the expense
of the seller’s flexibility. The seller needs to fix his own trading strategy and bear the
fluctuations in the external market. Once the price is favorable to the seller, the buyer
may choose to withdraw from the transaction. Once there is arbitrage, the buyers flock in.
The seller has no choice but hope for subsidies from mining and commission or interest
rate equalization. Although this asymmetric design temporarily alleviates the lack of
on-chain liquidity, there are the following problems in the long run. Firstly, waste of
resources due to the large amount of capital occupation. Numerous TVLs but only a
small number of transactions are supported, and most TVLs are still rushing to liquidity
mining; Secondly, the core variables, such as price and interest rate, are related to the
size of the pool, which are easy to be arbitrage on the one hand, and it is difficult to
carry out transactions and lending when the pool is not large enough on the other hand.
Moreover, TVL of different products cannot be shared, resulting in the so-called portfolio
lines being only formally combined, rather than liquidity sharing.

This kind of liquidity created at the expense of one party’s choice is not a perfect idea
under a decentralized architecture. Instead of allowing the seller to make asymmetric
sacrifices, it is better to completely erase this asymmetry. The system only allows a
completely symmetric buyer, and the seller is the system itself. This idea is in line with
the spirit of the blockchain decentralized game. Everyone is in the same position to play
the game with the algorithm, whether it is Bitcoin or Ethereum. Each participant only
needs to pay the system tokens of the consideration to the system to get the financial
products they want, and the income of the financial products will be settled by the system
tokens. This idea frees us from the traditional model of financial transactions and allows
the formation of a new financial paradigm, and ensures that DeFi does not just possess combinability, but is equivalent to a linear transformation in the same framework, with
uniform programmability.