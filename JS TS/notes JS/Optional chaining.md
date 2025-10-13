(?.)
This is basically for safety purpose.
### The problem this functions deals with
```
const user = {};
console.log(user.address.city); // ❌ Error: Cannot read properties of undefined
```
### And how it helps
```
const user = {};
console.log(user?.address?.city); // ✅ undefined (no error)
```
- The `?.` operator **stops** and returns `undefined` if the value before it is `null` or `undefined`.
- No crash, no error.