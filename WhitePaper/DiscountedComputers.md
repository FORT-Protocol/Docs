# FORT: A DeFi Development and Application System with Unlimited Liquidity

> James Zhao, September 9, 2021

---

## Discounted Computers

We abstract all financial products (services) as an exchange of revenue streams and expenditure streams, and the revenue streams are represented by linear combinations of the basic revenue functions. Then any financial product development only needs to determine the linear combination of basic revenue functions to obtain its cost (present value) by the linear combination of basic discount functions. Such linear combinations are the same as we use computer programming, therefore we call this figuratively as the discounted computer. Any financial product corresponds to a piece of computer programming, so that the composable DeFi become program designing and calling in the same framework, reducing the difficulty of understanding and risk management.

## Base Return Function and Discounted Function

The basic revenue function (BRF) can be a deterministic value (e.g., block 13678933 to get 1000 DCUs) or it can be a random variable after introducing the NEST oracle price information. Here, we consider the basic types of deterministic values, random variables of NEST pricing oracle, and probability random variables, each of which consists of polynomial functions, exponential functions, logarithmic functions, absolute value functions, maximum-minimum functions, and definite integral operators. The base discount function (BDF) contains normal distribution functions, polynomial functions, exponential functions, logarithmic functions, etc. Considering that the reality does not need so many revenue functions as well as the complexity of the calculation, we choose a relatively simple list of functions, which can be gradually improved later. As mentioned earlier, the basic revenue function is the basic instructions of the discounted computer while a financial product is a program which is a combination of these instructions.

## Discount Rate and Interest Rate Oracle

In principle, the discount rate reflects the risk-free return of the on-chain world. We can choose a risk-free interest rate statistic on the chain such as the PoS yield of ETH or the decentralized interest rate oracle (a design as follows: given the number of DCU issues per year, anyone who locks DCUs can share these tokens proportionally) as the discount rate. However, this paradigm is more suitable for a traditional centralized world. In a decentralized world, we can take the discount rate to a relatively small value, even zero, in order to give the DCU deflationary properties and thus ensure a steady rise in the DCU price.

## Pricing Unit Transformation

If a fiat or ETH is required as the numeraire in FORT, it is sufficient to introduce the DCU/USDT or DCU/ETH price, which can be obtained through the NEST oracle. If the liquidity of DCU is large enough that the settlement of a single financial product has little impact on the price, the financial product with the introduced price is no different from the traditional financial product. The pricing based on the risk-neutral measure ($$E_{Q}$$) can perfectly solve the calculation of the discount function, which can be used for hedging or asset portfolio management.

$$\mathbb{E}^{Q} [e^{-rt_{i}}BRF_{i}\mid F_{0}]\leq \mathbb{E}^{Q}[e^{-rt_{i}}BDF_{i}\mid F_{0}]$$

## Financial Product Development

The development of a financial product in FORT is the same as writing smart contracts, i.e., finding a vector with BRF as the base for the target return, and that vector represents this financial product. The product of that vector and the corresponding BDF base is the cost of the financial product, i.e., it is only necessary to pay this cost in the time domain T0 to obtain the financial product. That financial product will get the DCUs minted by the FORT contract in the time domain T1, and its quantity is the product of that vector and the BRF. This process is just like writing smart contracts by which all financial products can be implemented with the discounted computer programming of FORT. Developers do not have to operate the liquidity of tokens, and just need the DCUs to be liquid enough.