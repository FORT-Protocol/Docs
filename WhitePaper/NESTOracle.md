# FORT: A DeFi Development and Application System with Unlimited Liquidity

> James Zhao, September 9, 2021

---

## NEST Oracle

NEST oracle is the only truly decentralized oracle on the market today: given an off-chain price stream, how to design a decentralized game such that the game equilibrium can output a price stream with the smallest possible deviation from the off-chain price stream. NEST oracle solves this problem with quotation mining, two-way options, validation cycles, price chains and β factors. NEST provides a price sequence that does not change the distribution of asset prices, but approaches a discrete sampling model, which is determined by the structure of the decentralized game, where the quote deviation and quotation density depend on the depth of the arbitrage market and the price of the NEST token. Overall, NEST provides an efficient decentralized oracle that maintains the fundamental traits of asset prices.

In FORT, we tend to use highly efficient market prices, and hence choose the most liquid underlying assets such as BTC and ETH, etc. The basic price model follows the Geometric Brownian Motion (GBM) model. Considering the characteristics of prices deviation and discrete time, we correct the prices using the k-factor.

$$K= \left ( 0.00002T+4\sigma  \right)\ast \gamma \left ( \sigma  \right )$$

where $$\gamma$$ is volatility in seconds and T is the time delay derived from the difference between the height of the successfully packed block and the height of the block where the most recent valid NEST price multiplied by the block time interval, and γ takes a value satisfying:

$$\gamma =\begin{cases}
1 & \text{ for } \sigma \leq 0.0003 \\ 
1.5 & \text{ for } 0.0003< \sigma < 0.0005 \\ 
2 & \text{ for } \sigma > 0.0005 
\end{cases}$$

## Time Domain

The time domain is denoted by $$T_{i}$$ and can be moments or intervals. A moment can be a definite moment or a random moment (e.g., a stoppage), and in finance, an interval is often used to determine some mean or stoppage. Although the time on the blockchain is discrete, these discrete differences can be ignored for a longer period and compensated for in a shorter period based on the k-factor, and thus can be interpreted approximately in terms of continuous time intervals.