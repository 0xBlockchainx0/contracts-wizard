# Snapshot report for `src/erc20.test.ts`

The actual snapshot is saved in `erc20.test.ts.snap`.

Generated by [AVA](https://avajs.dev).

## basic erc20

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    pragma solidity ^0.8.0;␊
    ␊
    import "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    ␊
    contract MyToken is ERC20 {␊
        constructor() ERC20("MyToken", "MTK") {}␊
    }␊
    `

## erc20 with snapshots

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    pragma solidity ^0.8.0;␊
    ␊
    import "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Snapshot.sol";␊
    import "@openzeppelin/contracts/access/Ownable.sol";␊
    ␊
    contract MyToken is ERC20, ERC20Snapshot, Ownable {␊
        constructor() ERC20("MyToken", "MTK") {}␊
    ␊
        function snapshot() public onlyOwner {␊
            _snapshot();␊
        }␊
    ␊
        function _beforeTokenTransfer(address from, address to, uint256 amount)␊
            internal␊
            override(ERC20, ERC20Snapshot)␊
        {␊
            super._beforeTokenTransfer(from, to, amount);␊
        }␊
    }␊
    `

## erc20 burnable

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    pragma solidity ^0.8.0;␊
    ␊
    import "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Burnable.sol";␊
    ␊
    contract MyToken is ERC20, ERC20Burnable {␊
        constructor() ERC20("MyToken", "MTK") {}␊
    }␊
    `

## erc20 burnable with snapshots

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    pragma solidity ^0.8.0;␊
    ␊
    import "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Burnable.sol";␊
    import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Snapshot.sol";␊
    import "@openzeppelin/contracts/access/Ownable.sol";␊
    ␊
    contract MyToken is ERC20, ERC20Burnable, ERC20Snapshot, Ownable {␊
        constructor() ERC20("MyToken", "MTK") {}␊
    ␊
        function snapshot() public onlyOwner {␊
            _snapshot();␊
        }␊
    ␊
        function _beforeTokenTransfer(address from, address to, uint256 amount)␊
            internal␊
            override(ERC20, ERC20Snapshot)␊
        {␊
            super._beforeTokenTransfer(from, to, amount);␊
        }␊
    }␊
    `

## erc20 pausable

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    pragma solidity ^0.8.0;␊
    ␊
    import "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    import "@openzeppelin/contracts/security/Pausable.sol";␊
    import "@openzeppelin/contracts/access/Ownable.sol";␊
    ␊
    contract MyToken is ERC20, Pausable, Ownable {␊
        constructor() ERC20("MyToken", "MTK") {}␊
    ␊
        function pause() public onlyOwner {␊
            _pause();␊
        }␊
    ␊
        function unpause() public onlyOwner {␊
            _unpause();␊
        }␊
    ␊
        function _beforeTokenTransfer(address from, address to, uint256 amount)␊
            internal␊
            whenNotPaused␊
            override␊
        {␊
            super._beforeTokenTransfer(from, to, amount);␊
        }␊
    }␊
    `

## erc20 pausable with roles

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    pragma solidity ^0.8.0;␊
    ␊
    import "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    import "@openzeppelin/contracts/security/Pausable.sol";␊
    import "@openzeppelin/contracts/access/AccessControl.sol";␊
    ␊
    contract MyToken is ERC20, Pausable, AccessControl {␊
        bytes32 public constant PAUSER_ROLE = keccak256("PAUSER_ROLE");␊
    ␊
        constructor() ERC20("MyToken", "MTK") {␊
            _setupRole(DEFAULT_ADMIN_ROLE, msg.sender);␊
            _setupRole(PAUSER_ROLE, msg.sender);␊
        }␊
    ␊
        function pause() public {␊
            require(hasRole(PAUSER_ROLE, msg.sender));␊
            _pause();␊
        }␊
    ␊
        function unpause() public {␊
            require(hasRole(PAUSER_ROLE, msg.sender));␊
            _unpause();␊
        }␊
    ␊
        function _beforeTokenTransfer(address from, address to, uint256 amount)␊
            internal␊
            whenNotPaused␊
            override␊
        {␊
            super._beforeTokenTransfer(from, to, amount);␊
        }␊
    }␊
    `

## erc20 burnable pausable

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    pragma solidity ^0.8.0;␊
    ␊
    import "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Burnable.sol";␊
    import "@openzeppelin/contracts/security/Pausable.sol";␊
    import "@openzeppelin/contracts/access/Ownable.sol";␊
    ␊
    contract MyToken is ERC20, ERC20Burnable, Pausable, Ownable {␊
        constructor() ERC20("MyToken", "MTK") {}␊
    ␊
        function pause() public onlyOwner {␊
            _pause();␊
        }␊
    ␊
        function unpause() public onlyOwner {␊
            _unpause();␊
        }␊
    ␊
        function _beforeTokenTransfer(address from, address to, uint256 amount)␊
            internal␊
            whenNotPaused␊
            override␊
        {␊
            super._beforeTokenTransfer(from, to, amount);␊
        }␊
    }␊
    `

## erc20 burnable pausable with snapshots

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    pragma solidity ^0.8.0;␊
    ␊
    import "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Burnable.sol";␊
    import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Snapshot.sol";␊
    import "@openzeppelin/contracts/access/Ownable.sol";␊
    import "@openzeppelin/contracts/security/Pausable.sol";␊
    ␊
    contract MyToken is ERC20, ERC20Burnable, ERC20Snapshot, Ownable, Pausable {␊
        constructor() ERC20("MyToken", "MTK") {}␊
    ␊
        function snapshot() public onlyOwner {␊
            _snapshot();␊
        }␊
    ␊
        function pause() public onlyOwner {␊
            _pause();␊
        }␊
    ␊
        function unpause() public onlyOwner {␊
            _unpause();␊
        }␊
    ␊
        function _beforeTokenTransfer(address from, address to, uint256 amount)␊
            internal␊
            whenNotPaused␊
            override(ERC20, ERC20Snapshot)␊
        {␊
            super._beforeTokenTransfer(from, to, amount);␊
        }␊
    }␊
    `

## erc20 preminted

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    pragma solidity ^0.8.0;␊
    ␊
    import "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    ␊
    contract MyToken is ERC20 {␊
        constructor() ERC20("MyToken", "MTK") {␊
            _mint(msg.sender, 1000 * 10 ** decimals());␊
        }␊
    }␊
    `

## erc20 premint of 0

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    pragma solidity ^0.8.0;␊
    ␊
    import "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    ␊
    contract MyToken is ERC20 {␊
        constructor() ERC20("MyToken", "MTK") {}␊
    }␊
    `

## erc20 mintable

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    pragma solidity ^0.8.0;␊
    ␊
    import "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    import "@openzeppelin/contracts/access/Ownable.sol";␊
    ␊
    contract MyToken is ERC20, Ownable {␊
        constructor() ERC20("MyToken", "MTK") {}␊
    ␊
        function mint(address to, uint256 amount) public onlyOwner {␊
            _mint(to, amount);␊
        }␊
    }␊
    `

## erc20 mintable with roles

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    pragma solidity ^0.8.0;␊
    ␊
    import "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    import "@openzeppelin/contracts/access/AccessControl.sol";␊
    ␊
    contract MyToken is ERC20, AccessControl {␊
        bytes32 public constant MINTER_ROLE = keccak256("MINTER_ROLE");␊
    ␊
        constructor() ERC20("MyToken", "MTK") {␊
            _setupRole(DEFAULT_ADMIN_ROLE, msg.sender);␊
            _setupRole(MINTER_ROLE, msg.sender);␊
        }␊
    ␊
        function mint(address to, uint256 amount) public {␊
            require(hasRole(MINTER_ROLE, msg.sender));␊
            _mint(to, amount);␊
        }␊
    }␊
    `

## erc20 permit

> Snapshot 1

    `// SPDX-License-Identifier: MIT␊
    pragma solidity ^0.8.0;␊
    ␊
    import "@openzeppelin/contracts/token/ERC20/ERC20.sol";␊
    import "@openzeppelin/contracts/token/ERC20/extensions/draft-ERC20Permit.sol";␊
    ␊
    contract MyToken is ERC20, ERC20Permit {␊
        constructor() ERC20("MyToken", "MTK") ERC20Permit("MyToken") {}␊
    }␊
    `
