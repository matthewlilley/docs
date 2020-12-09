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

BentoBox.sol - 0x066b83CE269aa9851704d30Ce7e838a8B772b340  
LendingPair.sol \(master\) - 0x2bc401e64Be212E435339872208E7b07F5eB3Eb6  
SushiSwapSwapper.sol - 0xc870551cbfE40D7Bb272273D156123E18924Bc68  
PeggedOracle.sol - 0xb5C8A2d1C8d393Dace7b3C1D98f35d645A1cD1fc  
CompoundOracle.sol - 0xf1EFAf821B7FE3CCdFA1dC2b7c553B08BC53d707  
SimpleSLPTWAP0Oracle - 0xFDf9eECBC041fa126290108b86527dBA7c8eFC3e  
SimpleSLPTWAP1Oracle - 0xAcf73db053bA1a1DF51bC3BC0BfcA6C2ada5cFeC  
BentoHelper.sol - 0x0a503755021447B82037292EBc38d63c2FfBfEf7  
  
WETH &gt; SUSHI \(PeggedOracle\) LendingPair - 0x5F9A19B1a8CEb48570A4EF7D7290Fa927b598Eaa

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

