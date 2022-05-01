## ICEwater report 

By Dhruv Malik and Amit Malik.

### evaluation criteria :
    - checking the basic vulnerabilities from the SWC classifications.
    - Analyzing the errors in the logic ().
        -  then checking the general threats corresponding to the DeFI.
        - or the one like Solcurity.



## General overview: 
- two speculative assets :
    - Ice : an inflation protected asset by keeping the liqPool with the H20 stable.
    - prediction of the supply of H20 done in the controller , which in turn manages  the liquidity pools viz the virtualPool
        - after recovering the rewards, in order to maintain the liquidity pair , we will have to maintain the
    - rewards determined based on the user redeeming the tokens and the interval since last interval (in ERC20rewards)
    - users can either claim their tokens from rewards 
    - seperate pools of ICE<>H20 and H20 <> STM exists .
    - VirtualPool manages the rescaling of the LP pairs  once there has been withdrawl and swap of the assets.


[overall diagram](../overall_callGraph.png)

## general observations :
- the code is written nicely with the explanation , but there has been revert checks only on the controller level , there are various cases (insufficient liquidity etc) that needs further checks (assert and require) in the  




## static testing run of slither :
- 



### 1.RewardsManager : 
    - functions for getting rewards as H20 tokens call `ERC20rewards.claimReward(address account)` (claim reward ) should have the modifier that insures the instantiation of the modifier)  only by the address caller of the above function , thus avoiding the potential version of external state change in the execution.
    - also before minting there is no  functional check regarding whether the liquidity is successful or not .

### 2. Controller :
    - having  
    - 
   
        - 
    - VirtualPool : 
        - swapAB and swapBA should have been similar, 


## 3. VirtualPool:




## 4. libraries :
    - UFixedPoint : 





## External Dependency (Not considered at priority): 
- ERC20Rewards 

## main checks : 
- manipulation of poolLiquidity