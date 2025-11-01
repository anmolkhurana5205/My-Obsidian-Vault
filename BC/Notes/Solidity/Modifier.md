a **modifier** is like a **special reusable condition or rule** that you can attach to functions. It helps you control **how and when a function can be executed** without rewriting the same code again and again.

## 🔹 Key Points about Modifiers:

1. **Defined with `modifier` keyword**
    - A modifier is written once and can be used on multiple functions.
2. **Used for Preconditions / Restrictions**
    - Example: only the contract owner can call certain functions.
    - Example: check if enough Ether is sent.
3. **`_;` is Very Important**
    - Inside a modifier, the symbol `_;` tells Solidity **where the function’s body should run** after the modifier’s condition is checked.
4. **Can Have Parameters**
    - Modifiers can also accept arguments for flexibility.
5. **Multiple Modifiers**
    - A function can have **more than one modifier**, and they are executed in the order they are listed.

## 🔹 Example 1: Basic Modifier
``` solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract MyContract {
    address public owner;

    constructor() {
        owner = msg.sender; // Deployer is the owner
    }

    // Modifier
    modifier onlyOwner() {
        require(msg.sender == owner, "Not the owner!");
        _; // Continue execution of the function
    }

    // Function using modifier
    function changeOwner(address newOwner) public onlyOwner {
        owner = newOwner;
    }
}
Here, only the owner can call `changeOwner`. If anyone else tries, it will revert.
```

## 🔹 Example 2: Modifier with Parameters
``` solidity
pragma solidity ^0.8.0;

contract Bank {
    mapping(address => uint) public balances;

    modifier minBalance(uint _amount) {
        require(balances[msg.sender] >= _amount, "Not enough balance!");
        _;
    }

    function withdraw(uint _amount) public minBalance(_amount) {
        balances[msg.sender] -= _amount;
        payable(msg.sender).transfer(_amount);
    }
}
The `minBalance` modifier checks if the caller has enough balance before withdrawal.
```

## 🔹 Example 3: Multiple Modifiers
``` solidity
modifier onlyOwner() {
    require(msg.sender == owner, "Not the owner!");
    _;
}

modifier costs(uint price) {
    require(msg.value >= price, "Not enough Ether sent!");
    _;
}

function buy() public payable onlyOwner costs(1 ether) {
    // Function body will only run if both conditions are true
}
```

