# Contracts

### Deployments

These are for testing and reference only at this point. They contain a known exploit left in intentionally to be found during audit.

#### Mainnet\(test\)

This is a deployment on mainnet for testing. Not the final version.

BentoBox.sol - 0xb85d305798F3D68D1c0903a89d6070BbD8d27da4  
LendingPair.sol \(master\) - 0xFFC7BDA4925b64dE974769Ba08679b640979743B  
SushiSwapSwapper.sol - 0xB14C3C7F0D0529E5801D6d2160B1e1d33e6Cf3b0  
PeggedOracle.sol - 0x54A3451dD6C33d2D0510E72EfAECEB015b13B042  
CompoundOracle.sol - 0x748AA7f4CeBD01FcE7063bF5625178A2aa4260ab  
ChainlinkOracle.sol - 0xc52DEB5BCEe7e607204299840dC3c028144C744  
SimpleSLPTWAP0Oracle - 0x211FCE75A29AB078410Ed8B6A2EBCe9465Ec7B82  
SimpleSLPTWAP1Oracle - 0x90f2406DfE07f41f5d4777D632C8034adDEb7c11  
CompositeOracle.sol - 0xD001b85046984722868e79435aF678c374056DB3  
BentoHelper.sol - 0x923686F6539F16f83681459863ce1152A404247A

#### Ropsten

This is a deployment on Ropsten for testing. Not the final version.

BentoBox.sol - 0xAac3d83Af05428A2283FB762Ae99C07FF85d7602  
LendingPair.sol \(master\) - 0x2F92B5c6DD9A84090cE68F67e60523078E275E17  
SushiSwapSwapper.sol - 0x0fCb257F2534011f177Fb6dEc020959A2F3694D4  
PeggedOracle.sol - 0x2b9b9d5abCa9f110BFbcC3561d6B938b42562f33  
CompoundOracle.sol - 0xD11cc3F86249df5eAE496322E97AD2949A26618E  
SimpleSLPTWAP0Oracle - 0x72D9D6D2DE34dFB1EBEC5Db4d2E78755e5Bae26b  
SimpleSLPTWAP1Oracle - 0xBBfB2Ac78b4c69d72157cd1579Bd72ed67686860  
BentoHelper.sol - 0xD3d0F71Ea2E395A24DdEc4B65B3E4847a709D8E0  
  
WETH &gt; SUSHI \(PeggedOracle\) LendingPair - 

WETH - 0xc778417E063141139Fce010982780140Aa0cD5Ab  
SUSHI - 0x81DB9C598b3ebbdC92426422fc0A1d06E77195ec  
UniswapV2 Factory - 0x5C69bEe701ef814a2B6a3EDD4B1652CB9cc5aA6f  
UniswapV2 ETH-SUSHI - 0x47e1ce10065636AA989c4BFD19b9ac695785B7f1  
UniswapAnchoredView - 0xBEf4E076A995c784be6094a432b9CA99b7431A3f

  
  


### Units of Value - Amount / Share / Fraction

Throughout the code, not all values are simply token amounts, do to rebasing and accrual of fees and interest. In the BentoBox you will find Amount and Share used. In LendingPair you'll also find Fraction.

#### Amount

This is the amount of actual token units. This unit of value is what you use when interacting directly with the ERC20 token contract functions such as balanceOf, totalSupply and transfer.

#### Share

This represents a share of the tokens in the BentoBox. When a token rebases, the total amount that the BentoBox holds changes, but all the shares stay the same. The BentoBox contract has utility functions to translate amounts to and from shares called toShare and toAmount.

#### Fraction

Any masterContract interacting with BentBox will use shares and not amounts. If the contract has it's own amount to share layer, because for instance, interest is accruing, the new "shares" layer is called fractions.

By sticking to this terminology, units are tracked and named consistantly across the BentoBox and the masterContracts.



BentoBox is in BETA, the contracts are UNAUDITED and probably have security issues and bugs. They are deployed on Mainnet for testing only \(because some parts are almost impossible to test on Ropsten\). These contracts will not be used in the future. New audited and fixed versions will be deployed at a later date.

BentoBox

LendingPair \(Medium Risk\)

The first masterContract released is a LendingPair for medium risk assets, with the following parameters set:

| Parameter | Value |
| :--- | :--- |
| Collaterization Rate | 75% |
| Collaterization Rate \(open\) | 77% |
| Target utilization | 70%-80% |
| Minimum Interest Rate | approx 0.25% APR |
| Maximum Interest Rate | approx 1000% APR |
| Liquidation Bonus | 12% |
| Protocol Fee | 9% |
| Developer Fee | 1% |
| Borrow Opening Fee | 0.05% |

