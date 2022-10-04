# @p12/contracts-lib

A set of smart contracts library


# Get started

```shell
npm i @p12/contracts-lib --save
```

import contract in your solidity files.

```solidity
import '@p12/contracts-lib/contracts/access/SafeOwnableUpgradeable.sol';
```

# Feature

## SafeOwnable

For openzepplin Ownable contract, the owner transfer the ownership in one transaction. Once you transfer the ownership to wrong address, there is no way back.

SafeOwnable recommend a two-step ownership transfer pattern.

- First Step: The owner send a transaction to storage the address of `_pendingOwner` while the true ownership not changed.
- Second Step: The pending owner call the contract to claim the ownership. At this time, the ownership changes.

In this pattern, if you transfer ownership to a wrong address, you still have the right to edit the transfer rather than lay down.

## UUPS admin slot

the openzepplin uups is not standard uups as it doesn't save admin address in admin slot but use more flexible permission control to upgrade implementation.

While the hardhat-deploy not officially support this yet, we choose to save the admin address in `SafeOwnableUpgradeable`. A upgradable contract which inherits both `SafeOwnableUpgradeable` and `UUPSUpgradable` will be successfully upgraded in hardhat-deploy


# Special thanks to 

[@yosriady](https://github.com/yosriady)

# Disclaimer

This repo has no audit report now. **Do your own research**.