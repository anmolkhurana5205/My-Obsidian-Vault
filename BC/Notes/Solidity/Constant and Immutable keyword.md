## 🔹 1. `constant`

- **Definition:** A variable marked as `constant` must be assigned a value **at the time of declaration**.
- **Value assignment:** Known at **compile-time** (hardcoded).
- **Storage:** Not stored in contract storage → instead, the value is replaced **directly in bytecode** wherever used.
- **Gas efficiency:** Cheapest to use, because no storage read is required.
- **Example:**
``` solidity
uint256 public constant MINIMUM_USD = 50 * 1e18;
```
- The value `50 * 1e18` is fixed forever.
- The compiler replaces every `MINIMUM_USD` with `50000000000000000000` in bytecode.
- Saves gas since it avoids runtime lookups.

## 🔹 2. `immutable`

- **Definition:** A variable marked as `immutable` must be assigned a value either:
    - at the **time of declaration**, OR
    - in the **constructor**.
- **Value assignment:** Known at **deployment-time** (not compile-time).
- **Storage:** Stored once but in a cheaper way (directly in contract’s bytecode, not normal storage).
- **Gas efficiency:** Slightly more expensive than `constant` but much cheaper than regular `storage` variables.
- **Example:**
``` solidity
uint256 public immutable MINIMUM_USD;

constructor(uint256 _usd) {
    MINIMUM_USD = _usd * 1e18;
}
```

- You can set the value dynamically based on constructor input.
- Once set, it cannot be changed again.

| Feature                          | `constant`   | `immutable`                                           |
| -------------------------------- | ------------ | ----------------------------------------------------- |
| When assigned?                   | Compile-time | Deployment-time                                       |
| Can depend on constructor input? | ❌ No         | ✅ Yes                                                 |
| Stored in storage?               | ❌ No         | ❌ No (kept in bytecode)                               |
| Gas usage                        | Cheapest     | Slightly more than constant, but cheaper than storage |
| Flexibility                      | Low          | Higher                                                |
## 🔹 4. Practical Use Cases

- **Use `constant`:** When the value will **never change** and is **known beforehand** (like `PI`, `TOKEN_NAME`, `DECIMALS`, `SECONDS_PER_DAY`).
- **Use `immutable`:** When the value should be fixed **only once at deployment**, but depends on **constructor input** (like `owner`, `oracleAddress`, `minimumPrice`).

