## 🔹 What is an Interface in Solidity?

An **interface** in Solidity is like a **blueprint** for smart contracts.  
It defines the **function signatures** (name, parameters, and return types) but does **not** provide the implementation.

👉 You can think of it as a **contract skeleton** that other contracts can use to interact with unknown contracts without knowing their full code.

---

## 🔹 Rules of Interfaces

1. Functions in interfaces must be **external**.    
2. They cannot have **implementation** (only declaration).
3. They cannot define **state variables**.
4. They cannot have **constructors**.
5. They can inherit from other interfaces.

## 🔹 Example: Basic Interface
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.7;

interface ICalculator {
    function add(uint256 a, uint256 b) external pure returns (uint256);
    function subtract(uint256 a, uint256 b) external pure returns (uint256);
}
This interface defines two functions but doesn’t say **how** they work.
```

## 🔹 Using an Interface
```
contract Calculator is ICalculator {
    function add(uint256 a, uint256 b) external pure override returns (uint256) {
        return a + b;
    }

    function subtract(uint256 a, uint256 b) external pure override returns (uint256) {
        return a - b;
    }
}
```

- The `Calculator` contract implements the interface.
- We must use the `override` keyword because we’re providing the actual implementation.

## 🔹 Why Interfaces are Useful?

1. **Interacting with Other Contracts**
    - Example: Calling ERC20 token functions like `transfer`, `balanceOf`, etc.
    - You don’t need the full ERC20 code, just the interface.
2. **Standardization**
    - Common standards (ERC20, ERC721, etc.) are defined as interfaces.
3. **Modularity & Upgradability**
    - Interfaces separate **definition** from **implementation**, making systems more flexible.
# Example in my Own  code
```
// Get funds from the users
// Withdraw funds
// Set a minimum funding value in USD
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@chainlink/contracts@1.4.0/src/v0.8/shared/interfaces/AggregatorV3Interface.sol";

contract FundMe {
    uint256 public minimumUsd = 50*1e18;
    address[] public funders;
    mapping (address => uint256) public funderToAmount;
    
    function fund() public payable {
        // Want to be able to set a minimum fund amount in USD
        // 1. How do we send ETH to this contract ?
        require(getConversionRate(msg.value) >= minimumUsd, "Didn't send enough");
        funders.push(msg.sender);
        funderToAmount[msg.sender] += msg.value;
    }
    
    function getPrice() public view returns(uint256) {
        // ABI
        // Address - 0x694AA1769357215DE4FAC081bf1f309aDC325306
        AggregatorV3Interface priceFeed = AggregatorV3Interface(0x694AA1769357215DE4FAC081bf1f309aDC325306);
        (, int256 price,,,) = priceFeed.latestRoundData();
        return uint256(price*1e10);
    }
    
    function getVersion() public view returns(uint256) {
        AggregatorV3Interface priceFeed = AggregatorV3Interface(0x694AA1769357215DE4FAC081bf1f309aDC325306);
        return priceFeed.version();
    }

    function getNumberOfDecimals() public view returns(uint8) {
        AggregatorV3Interface priceFeed = AggregatorV3Interface(0x694AA1769357215DE4FAC081bf1f309aDC325306);
        return priceFeed.decimals();
    }
    
    function getConversionRate(uint256 ethAmount) public view returns(uint256) {
        uint256 ethPrice = getPrice();
        uint256 ethAmountInUsd = (ethPrice * ethAmount) / 1e18;
        return ethAmountInUsd;
    }
    // function withdraw() {}  
}
```

- the **role of the `interface` (AggregatorV3Interface)** is to act like a **blueprint** that tells your contract how it can talk to an already deployed contract on the blockchain (in this case, the Chainlink Price Feed contract).
- In Solidity, if you want to call functions from another contract (like `latestRoundData()` in the Chainlink price feed), you need to know the **function signatures** (their names, inputs, and outputs).
- You don’t need the full source code of that external contract — just the "shape" of it.
- An `interface` provides exactly that shape.

So basically:  
👉 **Interface = ABI written in Solidity**
