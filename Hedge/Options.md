# Options

---

## Introduction to Options

Hedge options are standard European-style options, European-style options with fixed risks and variable returns, which cannot be exercised in advance. When settling, if it is a in-the-money option, the return will be calculated based on the spread between the spot price and the strike price; if it is a out-of-money option, the return will be 0. 

DAO acts as the seller of the option and the user acts as the buyer of the option, and can choose 2 directions: call and put; the user can buy its option in the trading pair supported by the system and settle the option after it expires. Unlike traditional financial markets the premium for opening a position and the proceeds for settlement are both DCU.

## Buying Options

An option consists of the following four elements.

**Option direction**: 2 directions of calls/puts.

**Trading pairs**: Currently the first version of the Hedge system only supports support for ETH/USDT.

**Exercise time**: the user manually selects the date and time, and the system will calculate the block number to.

**Exercise price**: user-set exercise price, can be set to higher or lower than the current price.

### Position opening formula

After the user selects the option currency element and enters the amount to be bought, the system calculates the number of option shares the user expects to receive, the user deposits the DCU into the DAO contract, and at the time of exercise, the user can settle with the system. With a given exercise price and expiration date, the cost per option is obtained according to the following formula.

$$V_{c}=S_{0}e^{\mu T}(1-\phi (\frac{d_{1}}{\sqrt{T}}-\sigma \sqrt{T}))-K(1-\phi \frac{d_{1}}{\sqrt{T}})$$

$$V_{p}=K\phi(\frac{d_{1}}{\sqrt{T}})-S_{0}e^{\mu T}\phi(\frac{d_{1}}{\sqrt{T}}-\sigma \sqrt{T})$$

where:

- $$V_{c}$$ is the cost of one call option;
- $$V_{p}$$ is the cost of one put option;
- $$\phi(X)$$ is the standard normal distribution function;$$d_{1}=\frac{1}{\sigma }[inK/S_{0}+(\frac{\sigma ^{2}}{2}-\mu )T]$$;
- K is the strike price;
- $$\sigma$$ is the volatility, obtained from the NEST oracle;
- $$S_{0}$$ is the current price;
