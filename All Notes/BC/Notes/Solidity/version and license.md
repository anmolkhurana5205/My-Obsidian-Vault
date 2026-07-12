When you write a smart contract in **Solidity**, usually the first two things you see at the top of the file are:

1. **Pragma (Version Directive)**
2. **SPDX License Identifier**

### 1. **Version (Pragma)**

- Written as:
``` solidity
pragma solidity ^0.8.0;
```

- This line tells the compiler which Solidity version should be used to compile the contract.
    
- The `^` means "compatible with this version and any newer version that doesn’t break backward compatibility."  
    Example: `^0.8.0` means it will compile with `0.8.0, 0.8.1, 0.8.19…` but **not 0.9.0 or higher.**
- If you want to lock it to a single version, you can write:
``` solidity
pragma solidity 0.8.20;
```
Purpose: This avoids unexpected behavior if a newer compiler version changes features or introduces bugs.

### 2. **License (SPDX License Identifier)**

- Written as:
``` solidity
// SPDX-License-Identifier: MIT
```

- This is not Solidity code, but a comment recognized by tools.
    
- **SPDX (Software Package Data Exchange)** is a standard way of declaring the license of your code.
    
- Common identifiers:
    
    - `MIT` → Most common open-source license.
        
    - `GPL-3.0` → GNU Public License.
        
    - `UNLICENSED` → If you don’t want to give open usage rights.
- Example:
``` solidity
// SPDX-License-Identifier: GPL-3.0
pragma solidity ^0.8.0;
```

Purpose: Helps make it clear how others can use, modify, or distribute your smart contract. Some blockchain explorers (like Etherscan) require this field to verify and publish your contract.

