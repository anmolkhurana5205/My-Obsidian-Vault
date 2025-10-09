## What is BigInt?

- BigInt is a **built-in JavaScript primitive** that can represent integers **of arbitrary size**.
    
- Regular JS `Number` can only safely represent integers up to **2^53 − 1** (`9007199254740991`) — beyond that, precision is lost.
    
- BigInt can handle numbers far beyond this limit, which is crucial for blockchain integers like `uint256`.
    

Example:
```
const small = 42;        // Number
const big = 9007199254740992n;  // BigInt (notice the 'n' at the end)
```

## Syntax

### Create BigInt

1. **Literal with `n`**
```
const a = 123n;
```
2. From string or number using `BigInt()`
```
const b = BigInt("123456789012345678901234567890");
const c = BigInt(123);  // from regular number
```

### Important:

- You **cannot mix `Number` and `BigInt` directly** in arithmetic — you must convert:
```
const x = 5n;
const y = 10;

// ❌ Error: Cannot mix BigInt and other types
// const z = x + y;

// ✅ Correct ways:
const z = x + BigInt(y);
const w = Number(x) + y;
```

## Operations on BigInt

BigInt supports most arithmetic:
```
const a = 10n;
const b = 3n;

console.log(a + b); // 13n
console.log(a - b); // 7n
console.log(a * b); // 30n
console.log(a / b); // 3n (floor division)
console.log(a % b); // 1n
console.log(a ** b); // 1000n
```

## Comparison with Number

You **can compare BigInt and Number**, but cannot mix them in math:
```
const x = 10n;
const y = 10;

console.log(x === y);  // false, different types
console.log(x == y);   // true, type coercion allowed
console.log(x > 5);    // true
console.log(x < 20);   // true
```

## Converting BigInt

- **To Number** (careful — may overflow):
```
const big = 900n;
console.log(Number(big)); // 900
```

- **To String**:
```
console.log(big.toString()); // "900"
```

- **To JSON**: BigInt **cannot be directly serialized to JSON**, must convert to string first:
```
const obj = { value: 123n };
JSON.stringify(obj); // ❌ Error

JSON.stringify({ value: obj.value.toString() }); // ✅ Works
```

## BigInt & Ethers.js / Solidity

This is where BigInt becomes **essential** for blockchain:

1. Solidity integers like `uint256`, `int256` are **always returned as BigInt** in Ethers.js.
```
const currentFavNumber = await contract.retriver();
console.log(currentFavNumber); // 0n
```

2. Arithmetic must use BigInt:
```
const newFav = currentFavNumber + 1n;
await contract.store(newFav); // if store expects uint256
```

3. If you need to log or display for humans, convert:
```
console.log(Number(currentFavNumber)); // only if small enough
console.log(currentFavNumber.toString()); // safe for any size
```

### BigInt limits
- BigInt **does not support decimals**. Only integers.
- Cannot use methods like `Math.sqrt()` or `Math.pow()` (use `**` operator instead).
- Cannot mix with regular `Number` in arithmetic directly.

