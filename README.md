```
MIP#: XX
Title: Volumetric Price Stabilization for Reducing Risk for new Assets
Author(s): Sam Bacha (@sambacha)
Contributors:
Type: Technical
Status: Pre-MIP Discussion
Date Proposed: 2020-12-25
Date Ratified: Pending
Dependencies: N/A
Replaces: n/a
License: SSPL-1.0 / AGPL
```

# Volumetric Price Stabilization for Reducing Risk for new Assets

_Price Stability as a Service for New Asset Onboarding_

This proposal provides a middleware layer for MakerDAO to enable 'almost any' ERC-20 asset to become a **price stable (re: reduced volatility) asset** that can enable it to be used as collateral for CDP's given requirements are met.

**NOTES**: You can read the
**abridged whitepape**r on HackMD at this link:
https://hackmd.io/@sbacha/manifold
**Full whitepaper:**
https://github.com/manifoldfinance/evo
**Reference Implementation:**
https://github.com/manifoldfinance/documentation

Deployment Contract: `0x766291bE965E6Ba5E77892Ac70034f6B264AE7ea` (Rinkeby)

## Elevator Pitch

EVO Protocol calculates an average transfer rate for all holders of an ERC20 asset. Movement of an asset (transfers and withdrawals) that are above the calculated average transfer rate incur a _fee_. This _fee_ is redistributed to all holders. Transfers and Withdrawals below the average transfer rate incur no fee.

Think of this is a 'Uber Surchage' or a '401 K Penalty' imposed on _bulge bracket_ transactions. In essence this can serve as a _anti rug pull_ mechanism if so desired.The fees imposed on such transactions can be redistributed to a _Mutual Assurance Fund_ that can act as an insurance vault to further protect the MakerDAO Ecosystem or can be returned to all deposit addresses as a form of _Non Inflationary Staking Rewards_.

Only the period of recalculation, the `Market Period`, is pre-determined. No admin key, no other centralized form of control exists in the EVO Protocol.

## EVO Protocol

**EVO Protocol, short of Embedded Volumetric Optionality, is a price stabilizing (re: accelerating / deacceleralting) middleware protocol that enables almost any ERC-20 asset to reach price stability. It achieves this by managing _volume_.**

The token price is determined dynamically(and individually for each holder) based on the information stored or updated in the smart contract during previous transactions giving us the equation:

<img src="https://render.githubusercontent.com/render/math?math=%24P_%7Bt%2B1%7D(h%2C%20a)%3A%3D%5Csqrt%7B%5Cfrac%7BD_%7Bt%7D%7D%7BS_%7Bt%7D%7D%7D%2BI_%7Bt%2B1%7D%5E%7B%5Cprime%7D(h%2C%20a)%24">

The above equation will compute the price for a holder \[h\] to purchase a certain amount of EVO tokens in exchange for a base deposit in ETH/WETH at the given discrete time - \[t +1\] , where \[Dt\] stands for the deposit of ETH in the smart contract at previous time - point and \[St\] stands for the total supply of EVO tokens so far.

The first component with the token - base ratio \[Dt/St\] under the square root is the indicative price and does not depend on the purchase/transferred amount, $a$.

Ergo, the component \[I\_{t+1}^{\prime}(h, a)\] is called the discounted interest rate and it can grow proportionally to a within a range of \[[0, 0.24]\] of $$a$$.

Higher interest payouts can slow down, decelerate, the price movement. Interest rate determines how fast, or acceleration, such price can change depending on the market demand & supply pressure for EVO-based tokens. Interest[#] is computed individually for each EVO holder.

Total average transfer rate for an address
<img src="https://render.githubusercontent.com/render/math?math=%5Cavg(Rt%20%

![](https://cdn.mathpix.com/snip/images/riJoy07HScO9IfoAwmdyldN_EE0ut90HvtWyHG_L1KQ.original.fullsize.png)

![](https://cdn.mathpix.com/snip/images/5zVJIXSJPgQoAShFaClp2XRdqu2xbrcx-N7hQnYCmvw.original.fullsize.png)

Interest Rate
<img src="https://render.githubusercontent.com/render/math?math=%5C%5B%20P_%7Bt%2B1%7D(h%2C%20a)%3A%3D%5Csqrt%7B%5Cfrac%7BD_%7Bt%7D%7D%7BS_%7Bt%7D%7D%7D%2BI_%7Bt%2B1%7D%5E%7B%5Cprime%7D(h%2C%20a)%20%5C%5D">

Ownership Rate
<img src="https://render.githubusercontent.com/render/math?math=%5C%5Bl_%7Bt%2B1%7D%5E%7B%5Cprime%7D(h%2C%20a)%3A%3D%5Cfrac%7Ba%20%5Ctimes%20%5Csqrt%7Bl%20*%20%5Cmax%20%5Cleft(%5Cmin%20%5Cleft(%5Ctheta%2C%20l%5E%7B2%7D%5Cright)%2C%201%5Cright)%7D%7D%7B100%7D%5C%5D%0A%0A">

Discounted Interest Rate
<img src="https://render.githubusercontent.com/render/math?math=%5C%5BI_%7Bt%2B1%7D%5E%7B%5Cprime%7D(h%2C%20a)%3A%3D%5Cmax%20%5Cleft(I_%7Bt%2B1%7D(h%2C%20a)%2C%20l_%7Bt%2B1%7D%5E%7B%5Cprime%7D(h%2C%20a)%5Cright)-l_%7Bt%2B1%7D%5E%7B%5Cprime%7D(h%2C%20a)%5C%5D">

Price dynamics of equation (1) depends on the transactions volume conducted by all of the involved market participants and bounded by
<img src="https://render.githubusercontent.com/render/math?math=%5CO(sqrt(n))%5C%5D">

Therefore it can be expected that the demand for EVO Protocol based tokens like EVO-[ERC20] will be able to represent the demand for the underlying asset, whereas EVO-[ERC20] represents the value of the underlying asset as a derivative function of the base asset, the ERC-20 asset. (i.e.a fixed unit of account for the ERC-20 asset, e.g. What Gwei is to Ethereum.)

### GitHub Documentation

https://github.com/manifoldfinance/documentation
