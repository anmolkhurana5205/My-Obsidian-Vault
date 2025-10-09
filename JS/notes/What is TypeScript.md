**TypeScript (TS)** is a **superset of JavaScript**.

- “Superset” means **all JavaScript code is valid TypeScript**, but TypeScript adds **extra features**.
- The most important feature is **static typing** — you can define **types** for variables, function arguments, and return values.

In short:
TypeScript = JavaScript + Types + Extra Features

### ⚡ Key Features of TypeScript

1. **Static Types** – Helps catch errors **before running the code**.
    `let age: number = 25; age = "hello"; // ❌ Error: Type 'string' is not assignable to type 'number'`
2. **Type Inference** – TS can automatically figure out the type if you don’t specify.
3. **Interfaces & Types** – Define the shape of objects clearly.
    `interface User {   name: string;   age: number; }  const user: User = { name: "Anmol", age: 20 };`
4. **Classes & OOP Support** – TypeScript supports modern object-oriented programming features.
5. **ES6+ Features** – TS supports modern JavaScript features and compiles them down for older browsers.
6. **Tooling & Autocomplete** – IDEs like VS Code give you **intelligent suggestions, error checking, and autocomplete** with TypeScript.

### 🧩 Example Comparison

**JavaScript**
```
function add(a, b) {
  return a + b;
}
console.log(add(5, "10")); // Outputs "510" (oops!)
```

TypeScript
```
function add(a: number, b: number): number {
  return a + b;
}
console.log(add(5, "10")); // ❌ Error at compile time
✅ TypeScript prevents bugs like this **before running your code**.
```

### 🔹 How it Works

- TypeScript code (`.ts`) is **compiled/transpiled** into plain JavaScript (`.js`) using the **TypeScript compiler (`tsc`)**.
- Browsers or Node.js **run only the compiled JavaScript**, because they don’t understand TypeScript natively.

### 🔥 Why Developers Use TypeScript

- Catches errors early
- Makes large projects **more maintainable**
- Works perfectly with **React, Node.js, Angular, Vue, and more**
- Makes **collaboration on big projects safer**

