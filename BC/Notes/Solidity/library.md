- A **library** in Solidity is a special type of smart contract that contains **reusable functions**.  
- It is similar to a normal contract but with **some restrictions** that make it suitable only for utility/helper logic.

## 🔹 Rules of Libraries in Solidity

1. **Libraries cannot hold Ether**
    - They are not designed to store funds.    
    - No `payable` fallback or `receive` function allowed.
2. **Libraries cannot have state variables (storage)**
    - You cannot declare variables like `uint public count;` inside a library.
    - They are supposed to be **stateless utility code**.
3. **Libraries cannot inherit or be inherited**
    - You cannot extend (`is`) a library like you do with contracts.
4. **Libraries can have functions**
    - Functions can be `internal`, `public`, or `external`.
    - If **internal** → their code gets embedded in the calling contract at compile time.
    - If **public/external** → the library is deployed as a separate contract, and other contracts call it using `delegatecall`.
5. **Libraries cannot self-destruct**
    - `selfdestruct` is not allowed, because libraries should be permanent utility contracts.
6.  **'Using' 'for'**
- You can attach library functions to specific data types using:
- ```
  using LibraryName for DataType;
  ```
- This makes the code look object-oriented (`x.add(y)` instead of `LibraryName.add(x, y)`).

## 🔹 Example Library
``` solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

library MathLibrary {
    function add(uint256 a, uint256 b) internal pure returns (uint256) {
        return a + b;
    }

    function sub(uint256 a, uint256 b) internal pure returns (uint256) {
        require(b <= a, "Underflow!");
        return a - b;
    }
}

contract Test {
    using MathLibrary for uint256;  

    function testOps(uint256 x, uint256 y) public pure returns (uint256, uint256) {
        uint256 sum = x.add(y);   // same as MathLibrary.add(x, y)
        uint256 diff = x.sub(y);  // same as MathLibrary.sub(x, y)
        return (sum, diff);
    }
}
```

## 🔹 Summary of Rules

- ❌ Cannot store Ether
- ❌ Cannot have state variables
- ❌ Cannot inherit / be inherited
- ❌ Cannot use `selfdestruct`
- ✅ Can only have **functions** (utility logic)
- ✅ Functions can be internal (embedded) or external (separate deployment)
- ✅ Can use `using ... for` to attach library functions to types

