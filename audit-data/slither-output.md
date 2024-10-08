```bash

    /*//////////////////////////////////////////////////////////////
                                  RED
    //////////////////////////////////////////////////////////////*/
INFO:Detectors:
PoolFactory.s_pools (src/PoolFactory.sol#27) is never initialized. It is used in:
        - PoolFactory.createPool(address) (src/PoolFactory.sol#47-58)
        - PoolFactory.getPool(address) (src/PoolFactory.sol#63-65)
PoolFactory.s_tokens (src/PoolFactory.sol#28) is never initialized. It is used in:
        - PoolFactory.getToken(address) (src/PoolFactory.sol#67-69)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#uninitialized-state-variables


    /*//////////////////////////////////////////////////////////////
                                 YELLOW
    //////////////////////////////////////////////////////////////*/
INFO:Detectors:
TSwapPool.revertIfZero(uint256) (src/TSwapPool.sol#80-85) uses a dangerous strict equality:
        - amount == 0 (src/TSwapPool.sol#81)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#dangerous-strict-equalities



    /*//////////////////////////////////////////////////////////////
                                 GREEN
    //////////////////////////////////////////////////////////////*/
INFO:Detectors:
PoolFactory.constructor(address).wethToken (src/PoolFactory.sol#40) lacks a zero-check on :
                - i_wethToken = wethToken (src/PoolFactory.sol#41)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#missing-zero-address-validation
INFO:Detectors:
Reentrancy in TSwapPool._swap(IERC20,uint256,IERC20,uint256) (src/TSwapPool.sol#385-414):
        External calls:
        - outputToken.safeTransfer(msg.sender,1_000_000_000_000_000_000) (src/TSwapPool.sol#402)
        Event emitted after the call(s):
        - Swap(msg.sender,inputToken,inputAmount,outputToken,outputAmount) (src/TSwapPool.sol#404-410)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3
INFO:Detectors:
3 different versions of Solidity are used:
        - Version constraint >=0.6.2 is used by:
                ->=0.6.2 (lib/forge-std/src/interfaces/IERC20.sol#2)
        - Version constraint ^0.8.20 is used by:
                -^0.8.20 (lib/openzeppelin-contracts/contracts/interfaces/draft-IERC6093.sol#3)
                -^0.8.20 (lib/openzeppelin-contracts/contracts/token/ERC20/ERC20.sol#4)
                -^0.8.20 (lib/openzeppelin-contracts/contracts/token/ERC20/IERC20.sol#4)
                -^0.8.20 (lib/openzeppelin-contracts/contracts/token/ERC20/extensions/IERC20Metadata.sol#4)
                -^0.8.20 (lib/openzeppelin-contracts/contracts/token/ERC20/extensions/IERC20Permit.sol#4)
                -^0.8.20 (lib/openzeppelin-contracts/contracts/token/ERC20/utils/SafeERC20.sol#4)
                -^0.8.20 (lib/openzeppelin-contracts/contracts/utils/Address.sol#4)
                -^0.8.20 (lib/openzeppelin-contracts/contracts/utils/Context.sol#4)
        - Version constraint 0.8.20 is used by:
                -0.8.20 (src/PoolFactory.sol#15)
                -0.8.20 (src/TSwapPool.sol#15)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#different-pragma-directives-are-used
INFO:Slither:. analyzed (13 contracts with 91 detectors), 6 result(s) found
```