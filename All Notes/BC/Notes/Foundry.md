**Foundry** is a **fast**, **modern**, and **developer-friendly toolkit** for building **smart contracts** in Solidity.  
It’s similar to **Hardhat** or **Truffle**, but:
- **Much faster** (written in Rust, not JavaScript)
- **Better debugging & testing tools**
- **Native Solidity Testing** (no JavaScript needed for tests)
- **Command-line focused**, but sleek and powerful

### Foundry Main Components
|Component|Description|
|---|---|
|**forge**|The core tool for **building, testing, debugging** smart contracts.|
|**cast**|A command-line tool to **interact with networks**, contracts, send transactions, decode logs, etc.|
|**anvil**|A **local EVM blockchain** (like Hardhat Network / Ganache) for testing and simulating transactions.|

### Why Developers Love Foundry
|Feature|Explanation|
|---|---|
|**Speed**|Compilation and tests are extremely fast.|
|**Solidity-Based Tests**|You write tests in Solidity, not JS. This feels natural for blockchain devs.|
|**Easy Debugging**|Great stack traces and error messages.|
|**Highly Customizable**|Works well with Ethers, Hardhat, and other stacks.|
|**Gas Profiling**|Shows gas usage per function automatically.|

### How to Install Foundry
``` bash
curl -L https://foundry.paradigm.xyz | bash
foundryup
```
now you can run:
``` bash
forge --version
```

### Create a New Project
``` bash
forge init my-project
cd my-project
```

### Compile Contracts
``` bash
forge build
```

### Run Tests (with gas report)
``` bash
forge test -vvvv --gas-report
```
- `-vvvv` → shows detailed stack traces.

### Writing Tests in Solidity (Example)
**Contract** (`src/Counter.sol`)
``` solidity
pragma solidity ^0.8.13;

contract Counter {
    uint256 public count;

    function increment() public {
        count++;
    }
}
```
**Test** (`test/Counter.t.sol`)
``` solidity
pragma solidity ^0.8.13;
import "forge-std/Test.sol";
import "../src/Counter.sol";

contract CounterTest is Test {
    Counter counter;

    function setUp() public {
        counter = new Counter();
    }

    function testIncrement() public {
        counter.increment();
        assertEq(counter.count(), 1);
    }
}
```
Run the test:
``` bash
forge test
```

## Using Anvil (Local Blockchain)
Start a blockchain:
``` bash
anvil
```

Interact with RPC using **cast**:
```
cast balance <your-address> --rpc-url http://127.0.0.1:8545
```

Send ETH:
```
cast send <to-address> --value 1ether --private-key <key>
```

### Comparison with Hardhat
| Feature            | Foundry                | Hardhat                       |
| ------------------ | ---------------------- | ----------------------------- |
| Language for tests | **Solidity**           | JavaScript / TypeScript       |
| Speed              | **Extremely fast**     | Moderate                      |
| Default blockchain | **anvil**              | Hardhat Network               |
| Debugging          | Very detailed trace    | Good, but slower              |
| Learning curve     | Easy for Solidity devs | JS devs feel more comfortable |
