### function visibility specifiers
1. public
	- Accessible **everywhere**: inside the contract, derived contracts, and externally.
	- under the hood it creates the getter function.
	- If you don’t specify visibility, functions are `public` by default (but since Solidity 0.5.0, you must specify it explicitly).
2. private
	- Accessible **only within the same contract** where it is defined.
	- Not accessible by derived contracts (inherited contracts) or externally.
3. internal
	- Accessible **within the same contract** and also in **derived contracts**.
	- Not directly accessible externally (users cannot call it).
4. external
	- Accessible **only from outside the contract** (via transactions or external calls).
	- Cannot be called internally like `myFunc()`, but can be called using `this.myFunc()`.
	- Slightly more gas-efficient when used for external calls with large data inputs.

| Visibility   | Same Contract       | Derived Contract | External Accounts |
| ------------ | ------------------- | ---------------- | ----------------- |
| **public**   | ✔️                  | ✔️               | ✔️                |
| **private**  | ✔️                  | ❌                | ❌                 |
| **internal** | ✔️                  | ✔️               | ❌                 |
| **external** | ❌ (only via `this`) | ❌                | ✔️                |
### Modifiers
- view
	- The function **reads state** but does **not modify** it.
	- Can read state variables, balance, mappings, etc.
	- Cannot modify storage variables.
```
uint public num = 5;
function getNum() public view returns (uint) {
    return num; // allowed (reading state)
}
```
- pure
	- The function does **not read or modify** blockchain state.
	- It can only use its parameters or do calculations.
```
function add(uint a, uint b) public pure returns (uint) {
    return a + b; // pure calculation
}
```
- payable
	- Special modifier that allows the function to **receive Ether**.
	- Without `payable`, a function cannot accept Ether.
```
function deposit() public payable {
    // Ether sent is stored in contract's balance
}
```
- No Modifier (default)
	- If a function has **no specifier**, it can **both read and modify state**.
```
uint public count;

function increment() public {
    count += 1; // modifies state
}
```

| Modifier    | Reads State | Modifies State | Accepts Ether |
| ----------- | ----------- | -------------- | ------------- |
| **pure**    | ❌           | ❌              | ❌             |
| **view**    | ✔️          | ❌              | ❌             |
| **payable** | Optional    | ✔️ or ❌        | ✔️            |
| **default** | ✔️          | ✔️             | ❌             |
