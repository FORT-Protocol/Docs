# Bug bounty program

### Rewards by Threat Level
Rewards for Smart Contract vulnerabilities are distributed according to the impact of the vulnerability based on the [Immunefi Vulnerability Severity Classification System](https://immunefi.com/severity-system/). This is a simplified 4-level scale, with separate scales for websites/apps and smart contracts/blockchains, encompassing everything from consequence of exploitation to privilege required to likelihood of a successful exploit.

To determine the final reward amount, the likelihood to have a meaningful impact on availability, integrity, and/or loss of funds is considered. The final decision on the payout amount will be determined by the Fort DAO at its discretion.

Payouts are handled by the Fort DAO directly and are denominated in DCU. 

#### Smart Contracts and Blockchain
|Level|Payout|
|---|---|
|Critical|10000 - 50000 DCU|
|High|5000 - 10000 DCU|
|Medium|1000 - 5000 DCU|
|Low|100 - 1000 DCU|

### Prioritized Vulnerabilities
We are especially interested in receiving and rewarding vulnerabilities of the following types:

- Re-entrancy
- Logic errors
- Solidity/EVM details not considered
    - including integer over-/under-flow
    - including unhandled exceptions
- Trusting trust/dependency vulnerabilities
    - including composability vulnerabilities
- Oracle failure/manipulation
- Novel governance attacks
- Economic/financial attacks
    - including flash loan attacks
- Congestion and scalability
    - including running out of gas
    - including block stuffing
- Cryptography problems

### Out of Scope & Rules

The following vulnerabilities are excluded from the rewards for this bug bounty program:

- Attacks that the reporter has already exploited themselves, leading to damage
- Attacks requiring access to leaked keys/credentials
- Attacks requiring access to privileged addresses (governance)
- Incorrect data supplied by third party oracles
    - Not to exclude oracle manipulation/flash loan attacks
- Basic economic governance attacks (e.g. 51% attack)
- Lack of liquidity
- Sybil attacks

#### Rules

The rules of this bug bounty are as follows:

- Bug has not been publicly disclosed.
- Vulnerabilities that have been previously submitted by another contributor or already known by the Fort DAO are not eligible for rewards.
- The size of the bounty payout depends on the assessment of the severity of the exploit. Please refer to the rewards section below for additional details.
- Bugs must be reproducible in order for us to verify the vulnerability.
- Rewards and the validity of bugs are determined by the Fort DAO and any payouts are made at their sole discretion.
- Terms and conditions of the Bug Bounty program can be changed at any time at the discretion of Fort.
- Details of any valid bugs may be shared with complementary protocols utilized in the Fort ecosystem in order to promote ecosystem cohesion and safety.

### Contact information
Email: fortdao@fortprotocol.com