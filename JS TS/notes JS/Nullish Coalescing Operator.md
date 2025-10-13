(??)
### 🔹 What it is

The **`??`** operator is used to provide a **default value** when a variable is either `null` or `undefined`.

But `||` treats **falsy values** like `0`, `""`, or `false` as empty.

`??` is smarter:
```
const username = userInput ?? "Guest";
```
Now only `null` or `undefined` triggers the default — not other falsy values.
