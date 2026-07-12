Ethers.js provides its own **BigNumber class**, especially useful when working with token amounts (like `wei`) and when you need methods instead of native operators:
``` solidity
import { BigNumber } from "ethers";

const a = BigNumber.from("1000000000000000000"); // 1 ETH in wei
const b = BigNumber.from("2000000000000000000"); // 2 ETH in wei

const sum = a.add(b);
console.log(sum.toString()); // "3000000000000000000"
```

- Arithmetic is done with **methods**, not `+` or `*`.
- `.toString()` is required when displaying or logging, because BigNumber objects are objects, not primitives.
### Common BigNumber Methods (Ethers.js):
``` solidity
a.add(b)      // addition
a.sub(b)      // subtraction
a.mul(b)      // multiplication
a.div(b)      // division
a.mod(b)      // modulus
a.toString()  // convert to string
```
- BigNumber is especially needed for **ERC20 token balances**, **wei/ether conversion**, or **large integers from Solidity**.

## When to use BigInt vs BigNumber

- **BigInt**: Modern JS, arithmetic with integers, works well for small Solidity integers in scripts. Example: `0n`, `1n`.
- **BigNumber**: When interacting with blockchain libraries (like Ethers.js v5), or doing arithmetic on balances in **wei/ether**.
- Note: In Ethers.js v6, BigInt is preferred internally for contract integers, but BigNumber is still widely used for token math and older codebases.

### BigInt vs BigNumber

| Feature          | BigInt                                           | BigNumber (Ethers.js / other libs)                                                               |
| ---------------- | ------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| Native JS        | ✅ Built-in                                       | ❌ External library                                                                               |
| Precision        | Arbitrary-size integers                          | Arbitrary-precision decimal or integer, can include fractions                                    |
| Decimal support  | ❌ Only integers                                  | ✅ Supports decimals                                                                              |
| Usage            | JS arithmetic (`+`, `*`)                         | Must use library methods (`.add()`, `.mul()`)                                                    |
| Blockchain usage | ✅ Used in modern JS/Ethers for Solidity uint/int | ✅ Also widely used in older versions of Ethers.js, web3.js, or for decimals (like token amounts) |
