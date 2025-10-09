## 1. **Named Exports**

- You can export **multiple values** from a file.
    
- When importing, you must use the **same name** inside curly braces `{ }`.

```
// Named Exports
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;
export const PI = 3.14;
```

```
importing
import { add, subtract, PI } from "./math.js";

console.log(add(2, 3));  // 5
console.log(PI);         // 3.14
```

```
👉 You can also rename while importing:
import { add as sum, PI as circlePI } from "./math.js";
console.log(sum(4, 6));   // 10
```

## 2. **Default Exports**

- Each file can have **only one default export**.
    
- Import name can be anything (no `{ }` needed).

```
// Default Export
export default function logMessage(msg) {
  console.log("LOG:", msg);
}
```

```
Importing:
import log from "./logger.js";
log("Hello JS!"); // LOG: Hello JS!
```

```
import myLogger from "./logger.js";
myLogger("Works the same!");
```

## 3. **Mixing Named + Default**

You can use both in the same file:

```
export const greet = (name) => `Hello, ${name}`;
export const farewell = (name) => `Bye, ${name}`;

export default function saySomething() {
  console.log("Default says something!");
}
```

```
Importing:
import saySomething, { greet, farewell } from "./utils.js";

saySomething();
console.log(greet("Anmol"));
```

