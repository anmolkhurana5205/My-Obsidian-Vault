### 🔹 What is Reverting?
In Solidity, **reverting** means **undoing all changes** made by a transaction during execution and returning unused gas to the sender (except the base gas cost for submitting the transaction).

Whenever a contract hits an error condition or explicitly decides execution should not continue, it can **revert**.

Think of it like:  
👉 _“If something goes wrong, roll everything back to the state before this transaction started.”_

### 🔹 When Does a Revert Happen?

A transaction reverts in Solidity if:
1. **`require` fails** → Used for input validation, conditions, permissions.
```
require(balance[msg.sender] >= amount, "Not enough funds");
```

2. **`revert()` is called** → Explicitly revert with an error message.
```
if (amount == 0) {
    revert("Amount cannot be zero");
}
```

3. **`assert` fails** → Used for checking internal logic errors. If this fails, it means a bug.
```
assert(totalSupply == balances[owner] + balances[user]);
```

4. **Out-of-gas** → If execution consumes more gas than provided, the transaction reverts.

5. **Low-level calls fail** → Like `transfer()`, `send()`, or function calls to another contract.

### 🔹 Difference Between `require`, `revert`, and `assert`
| Statement                         | Use case                                                             | Refund gas?                   | Error message                                 |
| --------------------------------- | -------------------------------------------------------------------- | ----------------------------- | --------------------------------------------- |
| **`require(condition, message)`** | Validate inputs/conditions (e.g., user has balance, caller is owner) | ✅ Yes, remaining gas refunded | Yes                                           |
| **`revert(message)`**             | Forcefully stop execution with custom error                          | ✅ Yes                         | Yes                                           |
| **`assert(condition)`**           | Check for internal errors or invariants                              | ❌ Consumes _all_ gas          | No (but from 0.8.0+, it provides panic codes) |