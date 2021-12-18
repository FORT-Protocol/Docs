# Permanent Contracts

---

### Introduction to perpetual contracts

Hedge perpetual contracts currently support ETH/USDT trading pairs, call and put 1~5 times leverage. Users who hold leveraged contracts enjoy multiple leverage gains and bear multiple downside risks. Use DCU to pay for the corresponding perpetual position, with price fluctuations, the net margin assets of the perpetual contract is constantly changing, when the balance is less than the liquidation balance, a third party can initiate liquidation.

### Elements of a perpetual contract

A perpetual contract consists of the following 5 elements.

**Trading pairs**: Currently supported coins are ETH/USDT.

**Direction**: Calls and puts, with calls denoted by "L" and puts denoted by "S".

**Leverage**: Currently supports 5 types of leverage: 1, 2, 3, 4 and 5 times.

**Opening price**: The price at which a position is opened in a perpetual contract, recorded in the contract.

**Margin NAV**: When the change in margin NAV is less than the liquidation balance, a third party can initiate liquidation.

### Perpetual contract prices

Perpetual contract opening, settlement and selling call Nest prophecy machine price. Since on-chain price changes are not timely enough compared to centralized exchanges, a compensation factor (K value) is introduced for Nest prices to prevent arbitrage.

$$K=Max(\frac{|S_{1}-S_{2}|}{S_{2}}, 0.002)+\sqrt{t}*Max(\sigma, \sigma_{0})$$

where:

- Instant Volatility $$\sigma = |\frac{S_{2}-S_{1}}{S_{1}\sqrt{T}}|$$;
- Volatility provided by Nest $$\sigma_{0}$$ (not used for now in the first phase);
- Long-term volatility as defined by Hedge $$\sigma_{0}$$;
- The previous price $$S_{1}$$;
- The current price $$S_{2}$$;
- Two quotes effective interval T;
- Trading time difference t (trading moment and);

Trading with the corrected current price

- **Bullish**: When the position is opened $$P_{t}*(1+K)$$, when it is sold $$P_{t}/(1+K)$$

- **Bearish**: When the position is opened $$P_{t}/(1+K)$$, when it is sold $$P_{t}*(1+K)$$

### Calculation of Margin Net Assets

HEDGE perpetual contracts use margin net assets for liquidation. The current position will generate unsettled profit and loss as the price rises and falls. The dynamic rate of return of the current position is calculated as follows:

$$r=\frac{S_{t}e^{-ut}-S_{0}}{S_{0}}*g$$

where:

- $$S_{1}$$ is the price at the current moment, the price is derived from the NEST oracle machine;
- $$S_{0}$$ is the price at the initial moment;
- g is the leverage multiple;
- u is the current asset historical rate of return, which is uniformly set by the system;
- t is the time interval between the current moment and the opening time;

As the price of the currency fluctuates, the net assets of the margin also change at any time. The calculation formula is:

$$B_{L}=X(1+r)$$

$$B_{S}=X(1-r)$$

where:

- $$B_{L}$$ is the net margin assets in the bullish direction;
- $$B_{S}$$ is is the net margin assets in the bearish direction;
- r is the current position yield;

### Perpetual Contracts Consolidation

When a user buys the same perpetual contract again, the perpetual contract debt positions will be merged.

$$S=\frac{(X_{1}+X_{2})S_{1}S_{2}}{S_{1}X_{2}+S_{2}X_{1}e^{\mu(T_{1}-T_{2})}}$$

where:

- $$S_{1}$$ is the opening price before consolidation;
- $$X_{1}$$ is the amount of margin before the merger;
- $$S_{2}$$ is the price at the time of the new merger;
- $$X_{2}$$ is the number of new margin buys;
- $$\mu-usdt$$ 0.000000025367;

### Perpetual Contract Settlement

Users can sell their positions to DAO and settle with DAO. Hedge will call the NEST oracle to get the latest price and calculate the margin NAV of the current position, and users get the number of DCUs as follows

$$B_{DCU}=B_{level}$$

where:

- $$B_{DCU}$$ is the last DCU available to the user;
- $$B_{level}$$ is the net margin asset of the current position;

Upon completion of settlement, the DAO sends an additional equal amount of DCUs to the user's address.

### Liquidation of perpetual contracts

For positions in perpetual contracts with a leverage factor of 1, the concept of liquidation does not exist because the balance of the net margin assets is always greater than 0. For positions in perpetual contracts with a leverage factor greater than 1, the liquidation conditions are

$$B_{level}<Max(B*g*0.02, a)$$

where:

- $$B_{level}$$ is the current position's margin NAV;
- B is the current position's margin;
- g is the leverage multiple;
- a is the minimum retained balance of the set account, which is currently 10;

Liquidation can be initiated by any third party. After initiating liquidation, the position will be closed and the liquidator will receive the remaining DCU of the liquidated debt position as a reward.