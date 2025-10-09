## .call() function
### 1️⃣ What is `.call()`?

`.call` is a **low-level function** in Solidity that lets a contract:
- Send Ether to any address.
- Call functions on other contracts **dynamically** (even if you don’t know the ABI at compile time).

It’s the **replacement for `send` and `transfer`** in modern Solidity because it overcomes their 2300 gas limit.

### 2️⃣ Syntax
```
(bool success, bytes memory data) = address.call{value: amount, gas: gasAmount}(encodedFunctionCall);
```

#### Parts:

- `address` → the recipient or target contract.
- `{value: amount, gas: gasAmount}` → optional parameters: how much Ether to send, how much gas to forward.
- `encodedFunctionCall` → the function selector and arguments encoded in bytes (usually via `abi.encodeWithSignature`).
- Returns a **tuple**: `(bool success, bytes memory data)`
    - `success` → true if the call succeeded
    - `data` → returned data from the function

### 3️⃣ Simple Ether Transfer Example
```
(bool sent, ) = payable(msg.sender).call{value: 1 ether}("");
require(sent, "Transfer failed");
```
- Sends 1 Ether to `msg.sender`.
- Forwards all remaining gas (unless specified).
- `""` → no function call, just Ether transfer.

✅ Preferred over `transfer` or `send` because it **works with any recipient**, even contracts needing more than 2300 gas.

# Much left for the call function (will do it later)