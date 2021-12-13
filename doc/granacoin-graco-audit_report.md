# Granacoin (GRACO) audit report.


# Summary

This is the report from a security audit performed on [Token Granacoin](https://github.com/granacoin/granacoin/blob/main/gracocoin.sol) by [Blockchain Technology SAS](https://github.com/blockchaintechnologysas/audit/blob/main/doc/granacoin-graco-audit_report.md). This contracts are a version of [OpenZeppelin Contracts v4.4.0](https://github.com/OpenZeppelin/openzeppelin-contracts).

The audit mainly focused on the security of the funds and the fault tolerance of the token. The main intention of this token is the commercialization of the company's products UNIVERSO DE LOS COSMETICOS S.A.S. of Cali-Colombia

# In scope

1. [gracocoin.sol](https://github.com/granacoin/granacoin/blob/main/gracocoin.sol)

# Findings Processes

In total, **12** were reported including:

- 2 event.

- 10 funcion.

It is reported that it has no errors (No critical security issues were found).

## Event

### 1. Event Transfer(address indexed from, address indexed to, uint tokens)

#### Severity: LOW

#### Description

This event is emitted when the number of tokens (value) is sent from the from address to the to address.

### 2. Event Approval(address indexed tokenOwner, address indexed spender, uint tokens)

#### Severity: LOW

#### Description

This event is emitted when the amount of tokens (value) is approved by the owner to be used by spender (End User).

## Funcion

### 1. ERC20Burnable.

#### Severity: LOW

#### Description

You can perform the Burning Token function, make Repurchases to be able to Burn Tokens.
** _burn (account, amount); **

#### Recommendation

According to the code, only the administrator with the authorized Role can perform this action.

### 2. ERC20Snapshot.

#### Severity: LOW

#### Description

The definitions of the functions of `gracocoin.sol`.

With the Snapshop function, it allows us to obtain token support at any time to have it for consultations for seasons defined by a consecutive one, or to take balances from all holders.

** _snapshot (); **

Writing:
• <Snapshot> Write (creates a copy are consecutive)
Reading:
• <TotalSupplyAt> <Snapshotld>
• <BalanceOf> (Address) and (Snapshotld)

#### Recommendation

prolonged use of backups generates the cost of higher memory and this generates higher Cost in Gas

### 3. AccessControl.

#### Severity: lOW

#### Description

El control de acceso, es decir, "a quién se le permite hacer esto", es increíblemente importante en el mundo de los contratos inteligentes. El control de acceso de su contrato puede regir quién puede acuñar tokens, congelar transferencias y muchas otras cosas. Por lo tanto, es fundamental comprender cómo lo implementa, no sea que alguien más robe todo su sistema.
Escritura:
•	< Grant Role >
•	< Renounce Role>
•	< Revoke Role >

Lectura:
•	< Get Role Admin >
•	< Hash Role >
  
#### Recommendation  
  
Use with caution only the administered  

### 4. Pausable

#### Severity: low

#### Description

the ability to perform all system operations with the system administrator, this allows to avoid losses.
Writing:
• <Paused> Enable or Disable

Reading:
• <Paused> Boolean (true and false)

#### Recommendation

Specify `public` visibility for the contract's inner variables.

### 5. TotalSupply 

#### Severity: low

#### Description

Shows the total token created..

### 6. BalanceOf(address)

#### Severity: low

#### Description

Returns the number of tokens that an address (account) owns. This function is a getter and does not change the status of the contract.

### 7. allowance(address tokenOwner, address spender)

#### Severity: not a security issue

#### Description

The ERC-20 standard allows one address to assign an assignment to another address in order to retrieve tokens from it. This getter returns the remaining number of tokens that spenderse will allow you to spend on behalf of owner. This function is a getter and does not modify the state of the contract and should return 0 by default.

### 8. transfer(address to, uint tokens)

#### Severity: not a security issue

#### Description

Moves the number tokens from the address of the caller to the function (msg.sender) to the address of the recipient. This function issues the Transfer. Returns true if the transfer was possible.
 
### 9. approve(address spender, uint tokens)

#### Severity: not a security issue

#### Description

Set the amount of token that allows the transfer of the balance call function (msg.sender). This function emits the approval event. The function returns whether the mapping was successful.
  
### 10. transferFrom(address from, address to, uint tokens)

#### Severity: not a security issue

#### Description

Move the amount of tokens to the recipient address using the allocation mechanism. the amount is deducted after the caller's allowance. This function issues the Transfer event.  
  
# Specification

The contracts at [EthereumCommonwealth/ethereum-classic-multisig](https://github.com/EthereumCommonwealth/ethereum-classic-multisig/tree/ab77dc77b69ee5d39971d908d3cd01c5a02fea8b) repo are a copy of contracts from the [Open Zeppelin](https://github.com/OpenZeppelin/zeppelin-solidity/blob/v1.2.0/contracts/) repository, with the exclusion of contracts that are not related to a multisig wallet.

These contracts are in ready to use condition. At the time of the audit, the development of this contracts is considered complete. The last fixation was made on July 18, 2017. the last commit was made at 18 Jul 2017: https://github.com/OpenZeppelin/zeppelin-solidity/commit/4f444279661e7c2e6ff7c442c3d13ae45d33b892

Bug Bounties were not conducted.

Any further changes to the contracts will leave them in unaudited state.

# Conclusion

No critical vulnerabilities were detected. The reported issues can not directly hurt the Multisig smart-contract. The multisig smart-contracts can satisfy the main goal and could be used for official development donations storage.

It is highly recommended to complete a bug bounty before use.
