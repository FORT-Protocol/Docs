# FORT: A DeFi Development and Application System with Unlimited Liquidity

> James Zhao, September 9, 2021

---

## Application Examples

FORT has a wide range of applications, covering almost all financial services and different trading
structures (including peer-to-peer, many-to-many, etc.). It is a revolutionary design in the history
of blockchains, and having the ability of lock-in various off-chain economic relationships.

### Options and Options Coins

Options products become pretty simple: giving an expiration date and an exercise price, users can obtain a call or put option whose cost is determined by discount functions. Although this formula is not a risk-neutral measure when DCU price is not quoted, so care needs to be taken to understand the implications. When the DCU price is quoted, it is the same as traditional options, except that the interaction becomes much simpler and there is not much brokering to consider.

A better model is to issue the options as a token, i.e., the same token for a given expiration date and strike price, regardless of when the issue starts. The advantage of this model is that it allows traditional derivatives exchanges to dispense with the issue and settlement. In order to meet the issue demand, they either need to do a lot of matchmaking or find a market maker, and in order to settle, they often need margin management. Market makers also need to develop a hedging strategy, which is a huge financial auxiliary system. Although traditional finance is happy to do so, but its cost is much higher than the FORT model. Because the issuance and settlement of the FORT model, exchanges only need to solve the problem of secondary market trading of derivatives.

### Perpetual Contracts, Leveraged Trading and Leveraged Coins

Perpetual contracts or leveraged trading can also be very simple, which is a dynamic settlement model based on basic revenue functions. We can develop perpetual or leveraged transactions into a model called a leveraged coin: dynamically changing the balance of its tokens based on prices, which has been practiced in current algorithmic stablecoins.

### Trading, Price Coins and Stablecoins

A native asset is actually equal to a price coin ∗ DCU, which is equivalent to splitting an asset into a dynamic price and a fixed settlement unit. This model can only be effectively implemented in a fully decentralized world: the traditional centralized world has the credit risk of cashing out. Thus, trading is equivalent to exchanging DCUs for various price coins, or settling out of DCUs with various price coins. Or using the native asset to exchange the corresponding price coin at a ratio of 1 to 1 (which is actually slightly off, due to the price deviation of oracles). By analogy, a stablecoin pegged to a fiat currency such as the US dollar is a USDT price coin.

### Exponential and Logarithmic Coins

A new paradigm is the exponential coin, where the percentage of price fluctuations feeds into the growth of returns in an exponential manner. Compared to leveraged coins, exponential coins have many advantages: no need to close positions, faster growth, interchangeable transfers, free stacking at the same address, etc. For example, when the price doubles, the exponential coin with the e base can grow 7.4 times, and when the price triples, the exponential coin grows 20 times.

### Revenue Swaps

Revenue swaps are cost swaps, as they are all equivalent to discounted of revenue streams.

### Lending

Lending becomes much easier by pledging asset accepted by FORT to receive the corresponding DCUs, repaying it to receive the collateralized asset, and then being liquidated when the liquidation ratio is exceeded, where the core parameters are the liquidation ratio, collateral rate, interest rate, etc.

### Insurance

Based on the characteristics at the end of the event, a price insurance can be made to swap the loss with the premium.

### Interest Rate Derivatives

It is possible to design various interest rate derivatives through price information of the base interest rate oracle.

### Probability Coins

Design probability coins that get DCUs at a given moment with a predetermined probability. For example, coins with 1/10 probability, each probability coin have a 1/10 probability of getting 10 DCUs.

### NFT Applications

It is possible to lock in all economic relationships in off-chain games or NFTs based on DCU,
i.e. all game assets can be designed to some probability coins or derivatives above. In this way, its game assets corresponding to NFT can be cashed in FORT, regardless of the existence of that game, thus building a consistent variable in the game world.

### Multi-Party Trading

To design a transaction between two or more participants: A and B can create a contract based on FORT, each paying a certain amount of DCUs at the current moment and receiving the corresponding DCUs in the future, so that FORT can participate in the allocation between them, which realizes a multi-player competition and game structure.