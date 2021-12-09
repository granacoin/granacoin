# Whitepaper 1.0.0.1 Español Token Graco (Granacoin)

## Binance Smart Chain (BSC)

Nuestro contrato inteligente es BEP-20. Para obtener detalles técnicos sobre el estándar BEP-20: https://academy.binance.com/en/glossary/bep-20

Granacoin (GRACO) token desarrollado en Solidity. Asegúrese de consultar su tutorial: https://solidity.readthedocs.io/en/v0.6.9/introduction-to-smart-contracts.html

Implementaciones de estándares ERC20

Source code: 

## OpenZeppelin - Implementación segura

Nuestros Smart Contracts se basan en seguros y confiables [OpenZeppelin ERC-20 Smart Contract](https://docs.openzeppelin.com/contracts/4.x/erc20)

OpenZeppelin el código está en el corazón de nuestros tokens y seguimos sus prácticas de seguridad e implementación con mucho cuidado.

# Token Granacoin (GRACO) 

Este token es una implementación estándar de ERC-20 y se implementó en la red principal de Binance Smart Chain con un suministro máximo fijo de 15,000,000 SCOL. 

Mainnet Deployed Granacoin (GRACO) Token can be found here: 

Parámetros de compilación: Solidity 0.8.10+commit.fc410830. Optimización 200

## Proyecto Granacoin
Nuestro proyecto nació el 25 de enero de 2020  y se almaceno en la red BSC maint con el contrato __ , nombre nativa Granacoin (GRACO). Evolucionó con el whitepaper 1.0.0.1 donde se inicia el fondos de inversión y comercializacion de productos gracias a nuestra empresa aliada Universo de los Cosmeticos SAS.

* Link Whitepaper 1.0.0.1 Granacoin (GRACO).


## Criptomoneda Granacoin (GRACO) Blockchain 2020 - 2022
El Proyecto de Comercio GRACO en su etapa de creación fue presentado a la comunidad como el activo digital colombiano para alcanzar un apalancamiento en base de prueba de comercio, logrando posicionamiento y reconocimiento en Colombia. las pruebas se iniciaron sobre la red de Ether en el contrato 25 de enero 2020, smart contract: https://etherscan.io/address/0x2b16d25b75aec74519c0a7487d3c509e74299a8f 

* Link Código Scolcoin blockchain
https://github.com/

## Característica GRACO
* Nombre  Gracocoin
* Abreviatura GRACO
* Red: Binance Smart Chain (BSC)
* Network: Maint BSC
* Smart Contrac: S
* Total coin supply: 15.000.000 coins

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

## Desarrollo:

# 1 Fase:
Creación e Implementación del Contrato Token GRACOL.

# 2 Fase:
Capacitacion y Promocion en la Comunidad GRACOL.

# 3 Fase:
Intercambio y procesador de Pago.

# 4 Fase:
Adopción en mercado local.

# 5 Fase:
Lanzamiento Internacional.

## Roadmap

# Q1 2020
* Enero 25 de 2021: Creación de Token Scolcoin (Test).

# Q1 2022
* Diciembre de 2021 - Creación Token definitivo.
* Enero 2022. Lanzamiento Token GRACO
* (1 phase)

# Q2 2022
* Enero a febrero - Venta de activos a través de corredores de bolsa y / o corredores.
* Capacitación comunidad.

# Q3 2022
* Marzo a Junio - Adopción local.

# Q4 2022
* Junio - Diciembre Fase 3.

# Q1 2023
* Enero - Lanzamiento Internacional.

## Bibliotecas e interfaces

```Solidity
pragma solidity ^0.8.2;
```
Nosotros hemos desplegado Granacoin token to mainnet with solidity ^0.8.2.

```Solidity
import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
```
De inmediato nos adentramos en el uso intensivo de las bibliotecas seguras de OpenZeppelin. Esta es la implementación básica de ERC-20 en la que se basa GRACO.

```Solidity
import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Burnable.sol";
import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Snapshot.sol";
import "@openzeppelin/contracts/access/AccessControl.sol";
import "@openzeppelin/contracts/security/Pausable.sol";
import "@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol";
```
Ya hemos incluido granacoin.sol, ¿por qué incluir la interfaz? El contrato inteligente de GRACOL acepta un _token como uno de los parámetros de construcción. Discutiremos esto en la sección ** constructor ** a continuación.

## ERC20Burnable
Nuestro Token puede realizar la función de Burning Token, realizar Recompras para poder Quemar Tokens.

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
Con la función Snapshop nos permite obtener soporte del token en cualquier momento para tenerlo para consultas por temporadas definidas por una consecutiva, o tomar saldos de todos los titulares.

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
El control de acceso, es decir, "a quién se le permite hacer esto", es increíblemente importante en el mundo de los contratos inteligentes. El control de acceso de su contrato puede regir quién puede acuñar tokens, congelar transferencias y muchas otras cosas. Por lo tanto, es fundamental comprender cómo lo implementa, no sea que alguien más robe todo su sistema.

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
la capacidad de realizar todas las operaciones del sistema con el administrador del sistema, esto permite evitar pérdidas.

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

