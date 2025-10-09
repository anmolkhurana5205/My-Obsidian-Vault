## 1️⃣ Using `transfer`
```
payable(msg.sender).transfer(amount);
```
**Details:**
- Sends `amount` wei to the address.
- If the transfer **fails**, it **reverts the transaction** automatically.
- **Gas limit:** 2300 gas forwarded to the recipient (enough for basic operations, but not for complex contracts).

**Pros:**
- Simple and safe for most cases.

**Cons:**
- Can break if the recipient is a contract needing more than 2300 gas (because of EIP-1884).

## 2️⃣ Using `send`
```
bool sent = payable(msg.sender).send(amount);
require(sent, "Send failed");
```
**Details:**
- Sends `amount` wei.
- Returns **`true` if successful**, `false` otherwise.
- Also forwards **2300 gas** to the recipient.

**Pros:**
- Safer in some ways because you can **handle failure** explicitly.

**Cons:**
- You must check the return value using `require` or `if`, otherwise failure is ignored.

## 3️⃣ Using `call` (recommended in modern Solidity)
```
(bool sent, ) = payable(msg.sender).call{value: amount}("");
require(sent, "Call failed");
```
**Details:**
- Most **flexible and recommended** method now.
- Forwards all available gas by default (can limit gas manually).
- Returns a **bool** indicating success and optional data.

**Pros:**
- Works with any contract, even if it has a complex fallback.
- Avoids problems with `transfer` and `send` gas limit restrictions.

**Cons:**
- Must check the returned bool carefully, otherwise funds can be lost.