# FORT: A DeFi Development and Application System with Unlimited Liquidity

> James Zhao, September 9, 2021

---

## Discounted Computers

We abstract all financial products (services) as a reciprocal of revenue flow and expense
flow, and the revenue flow is represented by a linear combination of the underlying revenue
function, then any financial product development only needs to determine the linear
combination of the underlying revenue function to get its cost (present value) by the
linear combination of the discounted function, such a linear combination is the same as
we use computer programming, therefore we call this module figuratively as discounted
computer, and it is shown as follows.

Any financial product corresponds to a piece of computer programming, so that the
combinable lines of DeFi become program design and program calls in the same framework, reducing the difficulty of understanding and risk management.

## Base Return Function and Discounted Function

The base return function (BRF) can be shown as a deterministic value (e.g., block
13678933 to get 1000dcu) or it can be a random variable after introducing the NEST
oracle price. Here, we consider the basic types of deterministic values, random variables
of NEST price oracle, and pure probability random variables, each of which consists of a
polynomial function domain, exponential function, logarithmic function, absolute value
function, maximum-minimum function, and definite integral operator, while the base
discount function (BDF) contains a positive-terms distribution function as well as poly-nomial functions, exponential functions, logarithmic functions, etc. Here, we consider
that the reality does not need so many return functions as well as the complexity of the
calculation, we have chosen a relatively simple list of functions, which can be gradually
improved.

As mentioned earlier, the basic return function is the basic instructions of the discount computer, a financial product is a program, the program is a combination of these
instructions.

## Discount Rate and Interest Rate Oracle

In principle, the discount rate responds to the risk-free return of the on-chain world, and
we can choose a risk-free interest rate statistic of the chain into the POS yield of ETH
or the interest rate provided by a decentralized interest rate oracle (a design as follows:
given the number of DCU issues per year, anyone who locks DCUs can participate in the
equalization of these issues) as the discount rate. However, this paradigm is considered
in a traditional centralized world. In a decentralized world, in order to make the increase
in DCU issues have deflationary properties and thus ensure a steady rise in DCUs, we
can take the discount rate to a relatively small value, even zero.

## Pricing Unit Transformation

If some kind of fiat or ETH is needed as the unit of measure, in FORT, it is sufficient
to introduce the DCU/USDT or DCU/ETH price, which can be obtained by the NEST
prediction machine. If the liquidity of DCU is large enough that the settlement of a single
financial product has little impact on the price, the financial product with the introduced
price is no different from the traditional financial product, and the pricing based on the
risk-neutral measure can perfectly solve the calculation of the discount function, which
can be used for hedging or asset portfolio management.

$$\mathbb{E}^{Q} [e^{-rt_{i}}BRF_{i}\mid F_{0}]\leq \mathbb{E}^{Q}[e^{-rt_{i}}BDF_{i}\mid F_{0}]$$

where $$\mathbb{E}^{Q}$$ denotes risk-neutral measure.

## Financial Product Development

The financial product development here is the same as writing a smart contract, i.e., a
vector with BRF as the base is found for the target’s return, and that vector represents
this financial product, while the product of that vector and the corresponding BDF base
is the cost of the financial product, i.e., only that cost needs to be paid in the time
domain $$\tau _{0}$$, and that financial product is obtained. And that financial product will get
the DCU incremented by the FORT contract in the time domain $$\tau _{1}$$, and its quantity is
the product of that vector and the BRF.

This process is just as mechanical as writing ordinary smart contract code. This
makes it possible to implement all the financial products you want with the discounted
computer programming of FORT, with uniformity, and without the developer having to
operate the liquidity of the tokens, only the DCUs need to be sufficiently liquid.