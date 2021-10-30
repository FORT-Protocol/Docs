# FORT: A DeFi Development and Application System with Unlimited Liquidity

> James Zhao, September 9, 2021

---

## Application Examples

FORT has a wide range of applications, covering almost all financial services and different
trading structures (including peer-to-peer, multi-dollar, etc.). It is a landmark design
in the history of blockchain development, as it covers almost all financial services and
different transaction structures (including peer-to-peer, many-to-many, etc.), and can
lock in various off-chain economic relationships.

### Options and Options Coins

Options issuance is made very simple by simply entering an expiration date and an
exercise price to obtain a call or put option whose cost is determined by a discounted
function, although this formula is not a risk-neutral measure when DCU prices are not
quoted, so care needs to be taken to understand the implications. If the DCU price is
quoted it is the same as traditional options, except that the interaction becomes much
simpler and there is not much brokering to consider.

A better model is to issue the options as a token, i.e., the same token for a given
expiration date and strike price, regardless of when the issue starts. The advantage of
this model is that it allows traditional derivatives exchanges to dispense with the issue
and settlement issues: in order to meet the issue demand, they either need to do a lot
of aggregation or find a market maker, and in order to settle, they often need margin
management. And market makers also need to develop a hedging strategy, which is a
huge financial auxiliary system, although traditional finance is happy to do so, but its cost
is much higher than the FORT model, because with the latter issuance and settlement,
exchanges only need to solve the problem of secondary market trading of derivatives.

### Perpetual Contracts, Leveraged Trading and Leveraged Coins

Perpetual contracts or leveraged trading can also be very simple, as it is a dynamic settlement model and a basic revenue function. We can also develop perpetual or leveraged
transactions into a model called a leveraged coin: dynamically changing the balance of
its tokens based on price, which is also practiced in current algorithmic stablecoins.

### Transactions, Price Coins and Stablecoins

A native asset is actually equal to a price coin ∗ DCU denomination unit, which is
equivalent to splitting an asset into a dynamic price and a fixed settlement unit, except
that this model can only be effectively implemented in a fully decentralized world: the
traditional centralized world has the credit risk of cashing out. Thus, trading is equivalent
to exchanging DCUs for various price coins, or settling out of DCUs with various price
coins, or using the native asset to correspond to price coins 1 to 1 (which is actually
slightly off, due to the bias of the price prediction machine). By analogy, a stablecoin
pegged to a fiat currency such as the US dollar is a USDT price coin.

### Exponential and Logarithmic Coins

A new paradigm is the index coin, where the percentage of price fluctuations feeds into
the growth of returns in an exponential manner. Compared to leveraged coins, index coins have good properties: they never need to be closed, they grow faster, they can
be transferred to each other, they can be freely stacked at the same address, etc. For
example, when the price doubles, the index coin with e as the bottom can grow 7.4 times,
and when the price doubles, the index coin grows 20 times.

### Revenue Swaps

Various future revenue swaps are nothing but cost swaps, as they are all equivalent to
discounted future revenue flow.

### Borrowing and Lending

Borrowing is made simpler by pledging an asset recognized by the FORT contract to
receive the corresponding DCU, repaying it to receive the pledged asset, and then being
liquidated when the liquidation line is hit, where the core parameters are the liquidation
line, pledge rate, interest rate, etc.

### Insurance

Based on the tail characteristics of the event, a price insurance can be made to swap the
tail loss with the premium.

### Interest Rate Derivatives

Various interest rate derivatives are designed based on the base interest rate. It is possible
to design various derivatives similar to those under its price information flow simply by
having the information flow of the interest rate oracle.

### Probability Coin

Design a token that gets a DCU at a given moment with a predetermined probability. For
example, a 1-in-10 probability coin, each probability coin can have a 1-in-10 probability
of getting 10 DCUs.

### NFT Application

It is possible to lock any off-chain game or economic relationship designed by NFT based
on DCU, i.e. all game assets can correspond to some probability coin or some derivative
of the above. In this way no matter in which game, its game assets corresponding to
NFT can be cashed in FORT, regardless of the existence of that game, thus building a
consistent variable in the game world.

### Multi-Way Trading

To design a transaction between two or more participants: A and B can make a contract
based on FORT, each paying a certain amount of DCU at the current moment and
receiving the corresponding DCU in the future, so that FORT can participate in the
allocation between the two, thus realizing a multiplayer competition and game structure.