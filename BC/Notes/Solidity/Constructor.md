The constructor is like a **setup function** that runs once at deployment, useful for assigning initial values (e.g., owner, supply, addresses, etc.).
### 🔹 Key Points about Constructor:

1. **Special Function**
    - Defined using the keyword `constructor`.
    - It does **not have a function name** (unlike other functions).
2. **Runs Only Once**
    - Executes automatically when the contract is deployed.
    - Cannot be called again after deployment.
3. **Visibility**
    - It can be declared `public` or `internal`.
    - In Solidity ^0.7.0 and above, visibility (`public`) is optional and discouraged — default is internal.
4. **Parameters**
    - Constructors can take arguments.
    - While deploying the contract, you must provide these arguments.
5. **Inheritance Behavior**
    - If a contract inherits another contract with a constructor, you must pass arguments up to the parent constructor as well.
6. **If Not Defined**
    - If you don’t define a constructor, Solidity automatically creates a default constructor with no parameters.

### 🔹 Example 1: Simple Constructor
``` solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract MyContract {
    address public owner;

    // Constructor
    constructor() {
        owner = msg.sender;  // set contract deployer as the owner
    }
}
```

### 🔹 Example 2: Constructor with Parameters
``` solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Token {
    string public name;
    uint256 public supply;

    // Constructor with arguments
    constructor(string memory _name, uint256 _supply) {
        name = _name;
        supply = _supply;
    }
}
When deploying, you must give name and supply, e.g., "MyToken", 1000.
```

### 🔹 Example 3: Constructor with Inheritance
``` solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Parent {
    uint256 public data;

    constructor(uint256 _data) {
        data = _data;
    }
}

contract Child is Parent {
    constructor(uint256 _data) Parent(_data) {
        // additional logic for child contract
    }
}
The Child constructor calls Parent(_data) when deploying.
```

