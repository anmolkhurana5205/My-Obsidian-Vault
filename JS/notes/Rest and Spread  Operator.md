### **1. Rest Operator (`...`)**

- **Collects values** into a single array or object.
- Used when you want to take multiple elements and pack them together.
- Commonly used in **function parameters**.
```
Example with function arguments:
function sum(...numbers) {
  return numbers.reduce((acc, curr) => acc + curr, 0);
}

console.log(sum(1, 2, 3, 4)); // 10
Here, `...numbers` collects all arguments into an array `[1,2,3,4]`.
```

```
Example with object destructuring:
const person = { name: "Anmol", age: 21, city: "Delhi" };
const { name, ...rest } = person;

console.log(name); // "Anmol"
console.log(rest); // { age: 21, city: "Delhi" }
```

```
Example with arrays destructuring:
const numbers = [10, 20, 30, 40, 50];

const [first, second, ...rest] = numbers;

console.log(first);  // 10
console.log(second); // 20
console.log(rest);   // [30, 40, 50]
```

### **2. Spread Operator (`...`)**

- **Expands values** from an array or object.
- Used when you want to take items out of an array or object and spread them.
```
Example with arrays:
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];

const combined = [...arr1, ...arr2];
console.log(combined); // [1,2,3,4,5,6]
```

```
Example with objects:
const obj1 = { name: "Anmol" };
const obj2 = { age: 21 };

const merged = { ...obj1, ...obj2 };
console.log(merged); // { name: "Anmol", age: 21 }

```
