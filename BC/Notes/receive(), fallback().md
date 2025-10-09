**`receive`** and **`fallback`** are special functions used to handle plain Ether transfers and calls to a contract. They are crucial when a contract receives Ether without calling a specific function.

### **1. `receive()` function**

- The `receive()` function is a **special function that executes when a contract receives plain Ether** (without any calldata).
- It was introduced in Solidity 0.6.0.
- **Signature:**
```
receive() external payable {
    // logic when Ether is sent
}
```
- **Rules:**
	- Must be `external`.
	- Must be `payable` (otherwise the contract cannot receive Ether via plain transfers).
	- Cannot take arguments.
	- Cannot return anything.

- **Triggered when:**
    - Someone sends Ether using `send()` or `transfer()` (or `call` without data).
    - No function name is specified in the call.

### 2. `fallback()` function
- The `fallback()` function is executed **when no other function matches the called function signature** or when Ether is sent and there’s no `receive()` function.
- **Signature:**
```
fallback() external [payable] {
    // logic when no function matches
}
```
- **Rules:**
    - Must be `external`.
    - Can optionally be `payable` if you want it to accept Ether.
    - Cannot take arguments.
    - Cannot return anything.
- **Triggered when:**
    1. Someone calls a function that **doesn’t exist** in the contract.
    2. Someone sends Ether **without data** if there’s no `receive()` function.

| Feature             | `receive()`                    | `fallback()`                                           |
| ------------------- | ------------------------------ | ------------------------------------------------------ |
| Trigger             | Plain Ether transfer (no data) | No matching function or Ether sent without `receive()` |
| `payable` required? | Yes                            | Optional                                               |
| Takes arguments?    | No                             | No                                                     |
| Returns?            | No                             | No                                                     |
| Introduced in       | Solidity 0.6.0                 | Before 0.6.0; behavior changed in 0.6.0                |
|                     |                                |                                                        |
### **Flow example when sending Ether:**

1. If `msg.data` is empty:
    - If `receive()` exists → executed.
    - Otherwise, if `fallback()` is payable → executed.
    - Otherwise → transaction reverts.
2. If `msg.data` is not empty:
    - If the function signature exists → called normally.
    - Otherwise, if `fallback()` exists → executed.
    - Otherwise → transaction reverts.