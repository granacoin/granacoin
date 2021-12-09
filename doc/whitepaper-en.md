# Whitepaper 1.0.0.1 English Token Graco (Granacoin)

## Binance Smart Chain (BSC)

Our smart contract is BEP-20. For technical details on the BEP-20 standard: https://academy.binance.com/en/glossary/bep-20

Granacoin (GRACO) token developed in Solidity. Be sure to check out his tutorial: https://solidity.readthedocs.io/en/v0.6.9/introduction-to-smart-contracts.html

ERC20 standard implementations

Source code: 

## OpenZeppelin - Implementación segura

Our Smart Contracts are based on safe and reliable [OpenZeppelin ERC-20 Smart Contract](https://docs.openzeppelin.com/contracts/4.x/erc20)

OpenZeppelin code is at the heart of our tokens and we follow their security and implementation practices very carefully.

# Token Granacoin (GRACO) 

This token is a standard implementation of ERC-20 and was deployed on the Binance Smart Chain mainnet with a fixed maximum supply of 15,000,000 SCOL. 

Mainnet Deployed Granacoin (GRACO) Token can be found here: 

Build parameters: Solidity 0.8.10+commit.fc410830. Optimización 200

## Project Granacoin
Our project was born on January 25, 2020 and was stored in the BSC maint network with the contract __, native name Granacoin (GRACO). It evolved with the whitepaper 1.0.0.1 where the investment funds and product marketing began thanks to our allied company Universo de los Cosmeticos SAS.

* Link Whitepaper 1.0.0.1 Granacoin (GRACO).
* Test: https://testnet.bscscan.com/tx/0x202bfed5c1413c871d3294b44d5dfa7b27403b38f5dc56d2da83a922b3034ca8


## Token Granacoin (GRACO) Blockchain 2020 - 2022
The GRACO Trade Project in its creation stage was presented to the community as the Colombian digital asset to achieve leverage based on a trade test, achieving positioning and recognition in Colombia. The tests started on the Ether network in the contract January 25, 2020, smart contract: https://etherscan.io/address/0x2b16d25b75aec74519c0a7487d3c509e74299a8f 

* Link Código Scolcoin blockchain
https://github.com/

## Characteristic GRACO
* name Gracocoin 
* abbreviation GRACO 
* Network: Binance Smart Chain (BSC)
* Network: Maint BSC
* Smart Contrac: S
* Total coin supply: 15,000,000 coins

// contracts/BEP20.sol
Source Code: https://github.com/scolcoin/Token-Scolcoin-SCOL
Link Contract: https://bscscan.com/address/0x703477125bbee6430b2c4968c1ef66701a01359f#code

* /// @custom:security-contact coordinacion@granacoin.com.co
* /***********************************************************
* Granacoin (GRACOL) cryptocurrency backup and investment toke
* ************************************************************/  
* // Copyright (c) 2020-2021 Granacoin (GRACOL)
/*--------------------------------------------------------------- @dev
 * Exclusive premier investment pool for the community GRACOL Token
 * maximum profitability and liquidity. converts GRACOL Token.
*/

/* < Block Genesis Token >
 - Total Supply: 15.000.000 GRACOL token
 - Initial Supply: 15.000.000 GRACOL Token
 
 Details Pool Bep20
 Wallet: 

## Developing:

# 1 Phase:
Creation and Implementation of the GRACOL Token Contract.

# 2 Phase:
Training and Promotion in the GRACOL Community.

# 3 Phase:
Exchange and Payment Processor.

# 4 Phase:
Adoption in local market.

# 5 Phase:
International Launch.

## Roadmap

# Q1 2020
* January 25, 2021: Creation of the Scolcoin Token (Test).

# Q1 2022
* December 2021 - Definitive Token creation.
* January 2022. GRACO Token Launch
* (1 phase)

# Q2 2022
* January to February - Sale of assets through stockbrokers and / or brokers.
* Community training.

# Q3 2022
* March to June - Local adoption.

# Q4 2022
* June - December Phase 3.

# Q1 2023
* January - International Launch.

## Libraries and interfaces

Solidity
pragma solidity ^ 0.8.2;
`` ''
We have deployed Granacoin token to mainnet with solidity ^ 0.8.2.

```Solidity
import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
```
We immediately jump into the heavy use of OpenZeppelin's secure libraries. This is the basic ERC-20 implementation on which GRACO is based.

```Solidity
import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Burnable.sol";
import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Snapshot.sol";
import "@openzeppelin/contracts/access/AccessControl.sol";
import "@openzeppelin/contracts/security/Pausable.sol";
import "@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol";
```
We have already included granacoin.sol, why include the interface? The GRACOL smart contract accepts a _token as one of the build parameters. We will discuss this in the ** constructor ** section below.

## ERC20Burnable
Our Token can perform the Burning Token function, make Repurchases to be able to Burn Tokens.

** _burn(account, amount); **

Code:

```Solidity
/**
 * @dev Extension of {ERC20} that allows token holders to destroy both their own
 * tokens and those that they have an allowance for, in a way that can be
 * recognized off-chain (via event analysis).
 */
abstract contract ERC20Burnable is Context, ERC20 {
    /**
     * @dev Destroys `amount` tokens from the caller.
     *
     * See {ERC20-_burn}.
     */
    function burn(uint256 amount) public virtual {
        _burn(_msgSender(), amount);
    }

    /**
     * @dev Destroys `amount` tokens from `account`, deducting from the caller's
     * allowance.
     *
     * See {ERC20-_burn} and {ERC20-allowance}.
     *
     * Requirements:
     *
     * - the caller must have allowance for ``accounts``'s tokens of at least
     * `amount`.
     */
    function burnFrom(address account, uint256 amount) public virtual {
        uint256 currentAllowance = allowance(account, _msgSender());
        require(currentAllowance >= amount, "ERC20: burn amount exceeds allowance");
        unchecked {
            _approve(account, _msgSender(), currentAllowance - amount);
        }
        _burn(account, amount);
    }
}

// File: contracts/granacoin.sol
```

## ERC20Snapshot
With the Snapshop function, it allows us to obtain token support at any time to have it for consultations for seasons defined by a consecutive one, or to take balances from all holders.

** _snapshot(); **

Code:

```Solidity
abstract contract ERC20Snapshot is ERC20 {
    // Inspired by Jordi Baylina's MiniMeToken to record historical balances:
    // https://github.com/Giveth/minimd/blob/ea04d950eea153a04c51fa510b068b9dded390cb/contracts/MiniMeToken.sol

    using Arrays for uint256[];
    using Counters for Counters.Counter;

    // Snapshotted values have arrays of ids and the value corresponding to that id. These could be an array of a
    // Snapshot struct, but that would impede usage of functions that work on an array.
    struct Snapshots {
        uint256[] ids;
        uint256[] values;
    }

    mapping(address => Snapshots) private _accountBalanceSnapshots;
    Snapshots private _totalSupplySnapshots;

    // Snapshot ids increase monotonically, with the first value being 1. An id of 0 is invalid.
    Counters.Counter private _currentSnapshotId;

    /**
     * @dev Emitted by {_snapshot} when a snapshot identified by `id` is created.
     */
    event Snapshot(uint256 id);

    /**
     * @dev Creates a new snapshot and returns its snapshot id.
     *
     * Emits a {Snapshot} event that contains the same id.
     *
     * {_snapshot} is `internal` and you have to decide how to expose it externally. Its usage may be restricted to a
     * set of accounts, for example using {AccessControl}, or it may be open to the public.
     *
     * [WARNING]
     * ====
     * While an open way of calling {_snapshot} is required for certain trust minimization mechanisms such as forking,
     * you must consider that it can potentially be used by attackers in two ways.
     *
     * First, it can be used to increase the cost of retrieval of values from snapshots, although it will grow
     * logarithmically thus rendering this attack ineffective in the long term. Second, it can be used to target
     * specific accounts and increase the cost of ERC20 transfers for them, in the ways specified in the Gas Costs
     * section above.
     *
     * We haven't measured the actual numbers; if this is something you're interested in please reach out to us.
     * ====
     */
    function _snapshot() internal virtual returns (uint256) {
        _currentSnapshotId.increment();

        uint256 currentId = _getCurrentSnapshotId();
        emit Snapshot(currentId);
        return currentId;
    }

    /**
     * @dev Get the current snapshotId
     */
    function _getCurrentSnapshotId() internal view virtual returns (uint256) {
        return _currentSnapshotId.current();
    }

    /**
     * @dev Retrieves the balance of `account` at the time `snapshotId` was created.
     */
    function balanceOfAt(address account, uint256 snapshotId) public view virtual returns (uint256) {
        (bool snapshotted, uint256 value) = _valueAt(snapshotId, _accountBalanceSnapshots[account]);

        return snapshotted ? value : balanceOf(account);
    }

    /**
     * @dev Retrieves the total supply at the time `snapshotId` was created.
     */
    function totalSupplyAt(uint256 snapshotId) public view virtual returns (uint256) {
        (bool snapshotted, uint256 value) = _valueAt(snapshotId, _totalSupplySnapshots);

        return snapshotted ? value : totalSupply();
    }

    // Update balance and/or total supply snapshots before the values are modified. This is implemented
    // in the _beforeTokenTransfer hook, which is executed for _mint, _burn, and _transfer operations.
    function _beforeTokenTransfer(
        address from,
        address to,
        uint256 amount
    ) internal virtual override {
        super._beforeTokenTransfer(from, to, amount);

        if (from == address(0)) {
            // mint
            _updateAccountSnapshot(to);
            _updateTotalSupplySnapshot();
        } else if (to == address(0)) {
            // burn
            _updateAccountSnapshot(from);
            _updateTotalSupplySnapshot();
        } else {
            // transfer
            _updateAccountSnapshot(from);
            _updateAccountSnapshot(to);
        }
    }

    function _valueAt(uint256 snapshotId, Snapshots storage snapshots) private view returns (bool, uint256) {
        require(snapshotId > 0, "ERC20Snapshot: id is 0");
        require(snapshotId <= _getCurrentSnapshotId(), "ERC20Snapshot: nonexistent id");

        // When a valid snapshot is queried, there are three possibilities:
        //  a) The queried value was not modified after the snapshot was taken. Therefore, a snapshot entry was never
        //  created for this id, and all stored snapshot ids are smaller than the requested one. The value that corresponds
        //  to this id is the current one.
        //  b) The queried value was modified after the snapshot was taken. Therefore, there will be an entry with the
        //  requested id, and its value is the one to return.
        //  c) More snapshots were created after the requested one, and the queried value was later modified. There will be
        //  no entry for the requested id: the value that corresponds to it is that of the smallest snapshot id that is
        //  larger than the requested one.
        //
        // In summary, we need to find an element in an array, returning the index of the smallest value that is larger if
        // it is not found, unless said value doesn't exist (e.g. when all values are smaller). Arrays.findUpperBound does
        // exactly this.

        uint256 index = snapshots.ids.findUpperBound(snapshotId);

        if (index == snapshots.ids.length) {
            return (false, 0);
        } else {
            return (true, snapshots.values[index]);
        }
    }

    function _updateAccountSnapshot(address account) private {
        _updateSnapshot(_accountBalanceSnapshots[account], balanceOf(account));
    }

    function _updateTotalSupplySnapshot() private {
        _updateSnapshot(_totalSupplySnapshots, totalSupply());
    }

    function _updateSnapshot(Snapshots storage snapshots, uint256 currentValue) private {
        uint256 currentId = _getCurrentSnapshotId();
        if (_lastSnapshotId(snapshots.ids) < currentId) {
            snapshots.ids.push(currentId);
            snapshots.values.push(currentValue);
        }
    }

    function _lastSnapshotId(uint256[] storage ids) private view returns (uint256) {
        if (ids.length == 0) {
            return 0;
        } else {
            return ids[ids.length - 1];
        }
    }
}
// File: contracts/granacoin.sol
```

## AccessControl
Access control, meaning "who is allowed to do this", is incredibly important in the world of smart contracts. Your contract's access control can govern who can mint tokens, freeze transfers, and many other things. So understanding how you implement it is critical, lest someone else steal your entire system.

Code:

```Solidity
pragma solidity ^0.8.0;

/**
 * @dev String operations.
 */
library Strings {
    bytes16 private constant _HEX_SYMBOLS = "0123456789abcdef";

    /**
     * @dev Converts a `uint256` to its ASCII `string` decimal representation.
     */
    function toString(uint256 value) internal pure returns (string memory) {
        // Inspired by OraclizeAPI's implementation - MIT licence
        // https://github.com/oraclize/ethereum-api/blob/b42146b063c7d6ee1358846c198246239e9360e8/oraclizeAPI_0.4.25.sol

        if (value == 0) {
            return "0";
        }
        uint256 temp = value;
        uint256 digits;
        while (temp != 0) {
            digits++;
            temp /= 10;
        }
        bytes memory buffer = new bytes(digits);
        while (value != 0) {
            digits -= 1;
            buffer[digits] = bytes1(uint8(48 + uint256(value % 10)));
            value /= 10;
        }
        return string(buffer);
    }

    /**
     * @dev Converts a `uint256` to its ASCII `string` hexadecimal representation.
     */
    function toHexString(uint256 value) internal pure returns (string memory) {
        if (value == 0) {
            return "0x00";
        }
        uint256 temp = value;
        uint256 length = 0;
        while (temp != 0) {
            length++;
            temp >>= 8;
        }
        return toHexString(value, length);
    }

    /**
     * @dev Converts a `uint256` to its ASCII `string` hexadecimal representation with fixed length.
     */
    function toHexString(uint256 value, uint256 length) internal pure returns (string memory) {
        bytes memory buffer = new bytes(2 * length + 2);
        buffer[0] = "0";
        buffer[1] = "x";
        for (uint256 i = 2 * length + 1; i > 1; --i) {
            buffer[i] = _HEX_SYMBOLS[value & 0xf];
            value >>= 4;
        }
        require(value == 0, "Strings: hex length insufficient");
        return string(buffer);
    }
}

// File: @openzeppelin/contracts/access/IAccessControl.sol

```

## Pausable
the ability to perform all system operations with the system administrator, this allows to avoid losses.

Code:

```Solidity
pragma solidity ^0.8.0;

/**
 * @dev Provides information about the current execution context, including the
 * sender of the transaction and its data. While these are generally available
 * via msg.sender and msg.data, they should not be accessed in such a direct
 * manner, since when dealing with meta-transactions the account sending and
 * paying for execution may not be the actual sender (as far as an application
 * is concerned).
 *
 * This contract is only required for intermediate, library-like contracts.
 */
abstract contract Context {
    function _msgSender() internal view virtual returns (address) {
        return msg.sender;
    }

    function _msgData() internal view virtual returns (bytes calldata) {
        return msg.data;
    }
}

// File: @openzeppelin/contracts/security/Pausable.sol
```

