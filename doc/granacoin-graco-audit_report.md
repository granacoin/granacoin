# Granacoin (GRACO) audit report.


# Summary

This is the report from a security audit performed on [Token Granacoin](https://github.com/granacoin/granacoin/blob/main/gracocoin.sol) by [Blockchain Technology SAS](https://github.com/blockchaintechnologysas/audit/blob/main/doc/granacoin-graco-audit_report.md). This contracts are a version of [OpenZeppelin Contracts v4.4.0](https://github.com/OpenZeppelin/openzeppelin-contracts).

The audit mainly focused on the security of the funds and the fault tolerance of the token. The main intention of this token is the commercialization of the company's products UNIVERSO DE LOS COSMETICOS S.A.S. of Cali-Colombia

# In scope

1. [gracocoin.sol](https://github.com/granacoin/granacoin/blob/main/gracocoin.sol)

# Findings

In total, **7 issues** were reported including:

- 2 medium severity issues.

- 4 low severity issues.

- 1 minor observation.

No critical security issues were found.

## Security issues

### 1. Permanent ownership.

#### Severity: medium

#### Description

Each owner of the multisig wallet is permanent. A mechanism to update a list of owners or claim ownership is not presented. This can result in a permanent loss of funds in some specific circumstances.

Detailed description can be found [here](https://github.com/EthereumCommonwealth/ethereum-classic-multisig/issues/7).

#### Recommendation

Implement a mechanism to manage ownership/ claim ownership.

### 2. Interface function definitions caused Remix compiler error.

#### Severity: medium

#### Description

The definitions of the functions of `Multisig.sol` contract made the Remix compiler unable of generating bytecode of the contract.

This is not a security issue, but a code flaw. This can not affect a deployed contract, but this made compiler behave in unintended way. This hurts contract's reusability property as well.

Detailed description can be found [here](https://github.com/EthereumCommonwealth/ethereum-classic-multisig/issues/6).

#### Recommendation

Change the implementation of empty function definitions.

### 3. Permissive fallback function.

#### Severity: low

#### Description

The fallback function allows any third-party contracts to send calls to a Multisig Wallet contract without any restrictions.

This can not directly affect Multisig wallet state or funds. This can only hurt third-party contracts that will interact with the Multisig Wallet contract.

Detailed description can be found [here](https://github.com/EthereumCommonwealth/ethereum-classic-multisig/issues/1).

### 4. Inner variables visibility.

#### Severity: low

#### Description

Some internal contract variables are hidden. This does not add any security, but can make it difficult to find errors if they occur.

Detailed description can be found [here](https://github.com/EthereumCommonwealth/ethereum-classic-multisig/issues/3).

#### Recommendation

Specify `public` visibility for the contract's inner variables.

### 5. External parameter of a function shadows an existing declaration. 

#### Severity: low

#### Description

`getOwner(uint256 ownerIndex)` function of `Shareable.sol` contract has a parameter that shadows an existing declaration. It is likely a mistyped parameter name.

It is strongly recommended to adhere to the same coding standard when developing important components of blockchain systems such as multisig wallet. Temporary variables and parameters must have a `_` prefix in this case.

Detailed description can be found [here](https://github.com/EthereumCommonwealth/ethereum-classic-multisig/issues/5).

#### Recommendation

Rename `uint256 ownerIndex` parameter to `uint256 _ownerIndex`.

### 6. Missing function visibility specifier.

#### Severity: low

#### Description

`confirm(bytes32 _h)` function of `Multisig.sol` contract has no visibility specifier unlike the other functions of this contract. It is strongly recommended to adhere to the same coding standard when developing important components of blockchain systems such as multisig wallet.

Detailed description can be found [here](https://github.com/EthereumCommonwealth/ethereum-classic-multisig/issues/4).

#### Recommendation

Implement a `public` visibility specifier for `confirm` function of `Multisig.sol` and `MultisigWallet.sol` contracts.

### 7. ERC223 and ERC777 compatibility issue.

#### Severity: not a security issue

#### Description

This wallet does not implement ERC223 receiver or ERC777 receiver interface.

It will still accept token transfers from contracts that implement ERC223 or ERC777 token standards but it will lead to a silent contract execution without proper event logging.

# Specification

The contracts at [EthereumCommonwealth/ethereum-classic-multisig](https://github.com/EthereumCommonwealth/ethereum-classic-multisig/tree/ab77dc77b69ee5d39971d908d3cd01c5a02fea8b) repo are a copy of contracts from the [Open Zeppelin](https://github.com/OpenZeppelin/zeppelin-solidity/blob/v1.2.0/contracts/) repository, with the exclusion of contracts that are not related to a multisig wallet.

These contracts are in ready to use condition. At the time of the audit, the development of this contracts is considered complete. The last fixation was made on July 18, 2017. the last commit was made at 18 Jul 2017: https://github.com/OpenZeppelin/zeppelin-solidity/commit/4f444279661e7c2e6ff7c442c3d13ae45d33b892

Bug Bounties were not conducted.

Any further changes to the contracts will leave them in unaudited state.

# Conclusion

No critical vulnerabilities were detected. The reported issues can not directly hurt the Multisig smart-contract. The multisig smart-contracts can satisfy the main goal and could be used for official development donations storage.

It is highly recommended to complete a bug bounty before use.
