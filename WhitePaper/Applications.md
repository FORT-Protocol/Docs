# FORT: A DeFi Development and Application System with Unlimited Liquidity

---

## Applications

FORT has a wide range of applications, covering almost all financial services and different trading structures (including peer-to-peer, many-to-many, etc.). It is a revolutionary design in the history of blockchains and can lock in various on-chain economic relationships.

The accessible financial products include European options, perpetual contracts and probability coins.

### European Options

At present, the European option smart contract on FORT protocol supports ETH, and the option price and strike price are calculated based on the price of ETH/USDT. Compared with the traditional European option, the buyer of the European option in FORT, namely the option holder, is a participant in the smart contract, while the seller of the option is the smart contract. Participants can buy European options from the system on FORT and then either sell the option to the system or hold the option until exercise time. The main difference between the European option smart contract and the traditional European option is that the option purchase, option sell, and option exercise in the smart contract are settled by DCU and allow participants to buy only one European option share.

Participants are required to select the type of option (call or put), expiration date (at least 30 days from the purchase date), the strike price ($$K$$), and the amount of DCU ($$X_0$$) to be used to purchase the option. $$T$$ is the exact time of a day as the day that the option is purchased ($$t_0=0$$). The system calculates the price of the option based on participant demand and the historical (Used to calculate the historical rate of return of the underlying option. The current price ($$S_0$$) of the underlying asset on the predictor (the price of call option $$c_0$$, put option $$p_0$$) and options share that can be purchased by the participant with $$X_0$$ DCU’s (call option share $$n=\frac{X_0}{c_0}$$, put option shares $$n=\frac{X_0}{p_0}$$). Note that the system considers the DCU to have the same value as the USDT when calculating shares.

The variables involved in this subsection are listed below: 

- $$t_0$$ or $$0$$: The time spot of buying the European option is denoted as time 0
- $$T$$: The time spot when the option is exercised ($$>0$$)
- $$t\in[0,T]$$: The time between the buying and the exercising of the option ($$0\leq t \leq T$$)
- $$S_t$$: The price of the underlying asset at the time $$t$$ ($$>0$$)
- $$\mu$$: The rate of return on the price of the underlying asset
- $$\sigma$$: The volatility of the price of the underlying asset ($$>0$$)
- $$K$$: The strike price of the option ($$>0$$)
- $$n$$: The shares owned by this participant of the option ($$>0$$)
- $$c_t$$: The value of a European call option at $$t$$ ($$\geq0$$)
- $$p_t$$: The value of a European put option at $$t$$ ($$\geq0$$)

At the time the option is exercised, the contract automatically extracts the current price of the last block $$S_T$$ to settle the proceeds of the option exercise. According to the above definition of options, the payoff from the execution of European call options is:

$$\text{Call option: }[S_T-K]^{+},$$$$\text{Put option: }[K-S_T]^{+},$$

where $$[x]^+:=\max[x,0]$$.

Call contracts mint $$n\times[S_T-K]^{+}$$ DCU immediately, and put contracts mint $$n\times[K-S_T]^{+}$$ DCU. After execution time, participants can withdraw the DCU from the contract to their wallet.

We assume the price of the underlying asset $$S_t$$ follows the following Geometric Brownian Motion (GBM):
$$dS_t=\mu S_t dt + \sigma S_t dW_t \text{, } t \in [0,T],$$
where $$W_t$$, $$t\in[0,T]$$ is a standard Wiener process (Brownian Motion), $$\mu$$ is the rate of return on the underlying asset's price, $$\sigma$$ is the volatility of the underlying asset's price. 

According to the initial price of the asset $$S_0$$ we can obtain:

$$S_t=S_0\exp((\mu-\frac{1}{2}\sigma^2)t+\sigma W_t)$$

where $$W_t$$ can be considered as a normally distributed random variable($$W_t\sim N(0,t)$$).

Taking $$t=T$$ and submit ($$t$$) into $$[S_T-K]^{+}$$ and $$[K-S_T]^{+}$$, taking expectation yields to:

$$\mathbb{E}([S_T-K]^{+}|S_0)=S_0 e^{\mu T}\Phi(d_1)-K\Phi(d_2)$$,

$$\mathbb{E}([K-S_T]^{+}|S_0)=K\Phi(-d_2)-S_0 e^{\mu T}\Phi(-d_1)$$,

where:

$$d_1=\frac{1}{\sigma\sqrt{T}}\biggl[\ln\frac{S_0}{K}+(\mu+\frac{\sigma^2}{2})T\biggr],$$

$$d_2=\frac{1}{\sigma\sqrt{T}}\biggl[\ln\frac{S_0}{K}+(\mu-\frac{\sigma^2}{2})T\biggr]=d_1 - \sigma\sqrt{T},$$

While $$\Phi$$ is the cumulative distribution function of the standard normal distribution. The price of the European call option at $$t=0$$ is:

$$c_0=\mathbb{E}([S_T-K]^{+}|S_0),$$

The price of the European put option at $$t=0$$ is:

$$p_0=\mathbb{E}([K-S_T]^{+}|S_0).$$

### Selling European Options

Participants can sell their European options to the system at some time point $$t$$ $$t\in(0,T)$$ before the European option expires. The system will calculate the price of the corresponding option $$c_t$$ (call option) or $$p_t$$ (put option) at this time according to the price $$S_t$$ of the underlying asset:

$$c_t=\mathbb{E}([S_T-K]^{+}|S_t),$$

$$p_t=\mathbb{E}([K-S_T]^{+}|S_t).$$

With the same calculates: 

$$\mathbb{E}([S_T-K]^{+}|S_t)=S_t e^{\mu (T-t)}\Phi(\hat{d_1})-K\Phi(\hat{d_2}),$$

$$\mathbb{E}([K-S_T]^{+}|S_t)=K\Phi(-\hat{d_2})-S_t e^{\mu (T-t)}\Phi(-\hat{d_1}),$$

where:

$$\hat{d_1}=\frac{1}{\sigma\sqrt{(T-t)}}\biggl[\ln\frac{S_t}{K}+(\mu+\frac{\sigma^2}{2})(T-t)\biggr],$$

$$\hat{d_2}=\frac{1}{\sigma\sqrt{(T-t)}}\biggl[\ln\frac{S_t}{K}+(\mu-\frac{\sigma^2}{2})(T-t)\biggr]=\hat{d_1} - \sigma\sqrt{(T-t)}.$$

Depending on the option price at that time, the system mints and pays either $$n\times c_t$$ (call option) or $$n\times p_t$$ (put option) DCU to the participant.  

### Perpetual Contracts

The perpetual contract in FORT is a smart contract acting as a futures exchange, the central counterparty for all participants to trade. However, because DCU is directly burned and minted by the system, and the system directly calls the price information of the underlying asset on the oracle to conduct settlement calculation, the algorithm is different from that of centralized futures. Hence, the perpetual contract in FORT only needs to consider a price time series without considering the convergence of price differences. At present, the smart contract of perpetual contract option on FORT protocol also supports ETH: futures opening, closing, and closing positions are calculated based on the spot price of ETH/USDT.

The variables related to this subsection are listed blow: 

- $$t_0$$ or $$0$$: The time of opening a perpetual position is denoted as $$t_0$$ or $$0$$
- $$T$$: The time spot of closing this perpetual position ($$>0$$)
- $$t\in[0,T]$$: a time spot between the opening time and the closing time of this perpetual position ($$0\leq t \leq T$$)
- $$S_t$$: The spot price of the underlying asset at time $$t$$ ($$>0$$)
- $$\mu$$: The historical rate of return of the price of the underlying asset
- $$\sigma$$: The long-term volatility of the price of the underlying asset ($$>0$$)
- $$\sigma_0$$: Spot volatility of the price of the underlying asset ($$\geq0$$)
- $$t_1$$: The time spot which has an effective price information and nearest to and before time $$t$$ ($$>0$$)
- $$t_2$$: The time spot which has an effective price information and nearest to and before time $$t_1$$ ($$>0$$)
- $$P_{t,1}$$: The effective  price of the underlying asset at time $$t_1$$ ($$>0$$)
- $$P_{t,2}$$: The effective  price of the underlying asset at time $$t_2$$ ($$>0$$)
- $$C(t)$$: The compensatory factor of the price of the underlying asset ($$>0$$)
- $$L$$: The leverage ratio of this future position ($$L=1,2,3,4,5$$)
- $$R(t)$$: The dynamic rate of return of this position at time $$t$$
- $$M(t)$$: The margin balance at time $$t$$ ($$\geq0$$)
- $$M_m (t)$$: The maintenance margin level at time $$t$$ ($$>0$$)
- $$a$$: The minimum retained balance factor ($$=10$$)

As with centralized futures contracts, participants are required to choose which position to open: long or short; You need to determine the leverage ratio (L) at the time of opening, which determines the margin ratio; Finally, he needs to decide how much of the margin to put up ($$M_0$$). Unlike centralized perpetuities, the opening and closing prices of FORT perpetuities are based on the Nest prognostic price sequence rather than the futures market price.

The price sequence on the oracle machine is not always updated in time compared with the price sequence in the exchanges, so the most recent available price information ($$P_ {t, 1} $$) may be accepted by the system a short time ($$t_1 $$) before the participant opening ($$t=0$$) or closing ($$t=T$$) a position. To prevent arbitrage opportunity, we introduce a compensating coefficient ($$C(t)$$) to calculate the opening price ($$S_0 $$) and the closing price ($$S_T $$): 

$$C(t)=\max(\frac{|P_{t,2} - P_{t,1}|}{P_{t,1}},0.002)+\sqrt{t_1}\times\max(\sigma(t),\sigma_0(t)),$$

where, $$P_{t,2}$$ is the effective price before and nearest to $$P_{t,1}$$, the time lag between the time of taking effect of $$P_{t,2}$$ and the time of taking effect of $$P_{t,1}$$ is: $$t_2$$; $$\sigma(t)$$ is the long-term volatility of the price of the underlying asset at time $$t$$; $$\sigma_0(t)$$ is the spot volatility of the price of the underlying asset at time $$t$$ calculated based on $$P_{t,1}$$ and $$P_{t,2}$$: 

$$\sigma_0=|\frac{P_{t,1} - P_{t,2}}{P_{t,2} \sqrt{t_2}}|\;.$$

After the compensatory factor is introduced, the opening and closing prices of participants are defined as: 

$$\text{Long opening price: }S_0=P_{0,1}\times(1+C(0)),$$

$$\text{Long closing price: }S_T=\frac{P_{T,1}}{1+C(T)},$$

$$\text{Short opening price: }S_0=\frac{P_{0,1}}{1+C(0)},$$

$$\text{Short closing price: }S_T=P_{T,1}\times(1+C(T)).$$

Unlike daily and real-time settlement, perpetual contracts in FORT are settled on a per-blockchain basis and are calculated differently from futures market price sequences. In FORT, we defined the dynamic rate of return of this position at a time $$t$$ ($$t\in[0,T]$$):

$$R(t)=L\times\frac{S_t e^{-\mu t}-S_0}{S_0}\;.$$

Where, according to the position, $$S_t$$ is the closing price at time $$t$$, $$S_0$$ is the opening price at time $$0$$, $$L$$ is the leverage ratio, and $$\mu$$ is the historical rate of return of the price of the underlying asset. With the dynamic rate of return of this position, we define the margin balance at $$t$$ as:

$$\text{Long margin balance: }M_t=M_0\times(1+R(t)),$$

$$\text{Short margin balance: }M_t=M_0\times(1-R(t)).$$

After the participant opens a position, he can either close his position or open more positions in the same position or close the position, at any later point in time $$t$$ ($$t\in[0,+\infty)$$). If he chooses to close, he will receive DCU equal to his margin balance. When his margin balance falls below the margin maintenance level: $$M_m (t)$$, another participant can forcibly close his contract and receive DCU equal to his margin balance. The margin maintenance level in the system is defined as:

$$M_m(t)=\max(M_t\times L\times 0.02,a),$$

where $$a$$ is the minimum remaining balance parameter in the system, which we set as 10 at present.

If the participant chooses to open an additional position with the same leverage at time $$t$$, his positions are combined and his equivalent opening price $$S$$ is calculated. If the participant closes his position at time $$T$$ ($$T>t$$), then the margin balance is: 

$$(1\pm L\frac{S_T e^{-\mu T}-S_0}{S_0})M_0+(1\pm L\frac{S_T e^{-\mu(T-t)}-S_t}{S_t})M_t,$$

where all $$\pm$$ takes $$+$$ or $$-$$ at the same time. Suppose another participant opens a position with $$S$$ and posts a margin $$M_0+M_t$$ at time $$t$$. At $$T$$, his margin balance is:  

$$(1\pm L\frac{S_T e^{-\mu (T-t)}-S}{S})(M_0+M_t),$$

where all $$\pm$$ takes $$+$$ or $$-$$ simultaneously as the former formula. We want to make the margin balance of these two participants equal, so from the above two equations, one can be obtained: 

$$(1\pm L\frac{S_T e^{-\mu T}-S_0}{S_0})M_0+(1\pm L\frac{S_T e^{-\mu(T-t)}-S_t}{S_t})M_t=(1\pm L\frac{S_T e^{-\mu (T-t)}-S}{S})(M_0+M_t),$$

The equivalent opening price $$S$$ can be obtained from the above equation:

$$S=\frac{(M_0+M_t)S_0 S_t}{S_0 M_t+S_t M_0 e^{-\mu t}}.$$

The combined initial margin is equal to the sum of the two margin payments.

### Probability Coins (PRC)

The probability coins (PRC) give the holder the right to request the system to mint DCUs for the holder at some moment with a predetermined probability. To exercise a PRC, the holder needs to decide when to exercise and the probability parameter $$N$$. Probability coins with parameter $$N$$ can request the system to mint $$N$$ DCUs when exercising with probability $$\frac{1}{N}$$, or the holder will receive nothing with probability $$1-\frac{1}{N}$$.

One can see that, with parameter $$N$$, the expectation of the outcome of exercising a PRC is equal to $$1$$, and the variation of this outcome is $$N-1$$.

A holder who has $$M$$ PRCs can exercise all the PRC at one time. The holder can receive $$MN$$ DCUs with probability $$\frac{1}{N}$$, or nothing with probability $$1-\frac{1}{N}$$. The expectation of the outcome of exercising a PRC is equal to $$M$$, and the variation of this outcome is $$M^2 (N-1)$$.

Or the holder can exercise them one by one, the outcome of every PRC is independent with each other. With this circumstance, the expectation of the total outcome is equal to $$M$$, but the variation of this outcome is $$M (N-1)$$.

Furthermore, the holder can decide to existence any PRC at a time as long as he still holds some PRC. This will give the holder more complicated probability space of outcome.

### Warrant and Impermanent Loss (IL)

Liquidity provider (LP) in AMM protocol inevitably suffers from IL. In this subsection, we propose, as one application based on FORT protocol, a possible solution for it. 

The AMM protocol of $$\textbf{Uniswap} (V2)$$ adopts one common constant product function, i.e.

$$x_t \cdot y_t=k$$

where $$x_t$$ and $$y_t$$ represent the quantities of numeraire and traded token in the liquidity pool respectively. It is also required that the ratio of the two assets inside the pool always represents the price of the traded token, i.e.

$$p_t = \frac{x_t}{y_t}$$

Assuming individual LP holds $$(x_0, y_0)$$, with in hedge period $T$ (measured by year), he/she can pay following quantity

$$(e^{\mu T} - 2 e^{\frac{\mu T}{2}- \frac{\sigma^2 T}{8}} +1)x_0$$

of DCU to get a derivative where $$\mu$$ and $$\sigma^2$$ represent the mean and variance of price in the liquidity pool. He/She can get following quantity

$$\sqrt{k}(\frac{p_t}{\sqrt{p_0}} + \sqrt{p_0} - 2\sqrt{p_t} )$$

of DCU if exercising the derivative at time $$t \in [0, T]$$ or following quantity

$$\sqrt{k}(\frac{p_T}{\sqrt{p_0}} + \sqrt{p_0} - 2\sqrt{p_T} )$$ 

of DCU if exercising it after $$T$$.

As we can see, the above functions are written as a relatively complicated function with non-linear structure regarding $$p_0$$, $$p_t$$, etc. This makes it practically difficult, although in principle not impossible, for the LP to find the counterparty who is willing to sell the specific derivatives. However, notice that the flexibility of BRF and BDF in FORT protocol allows any function forms for the cash flow in and out; FORT protocol can simply issue one warrant according to above functions. The omnipotent power of ILM is not limited to providing infinite liquidity but all possible types of liquidities based on any function.
