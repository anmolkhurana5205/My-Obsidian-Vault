### 🗺️ `map()`

**Purpose:** To transform every element of an array and return a **new array** of the same length.

**Syntax:**
```
const newArray = array.map((element, index, array) => {
  return newValue;
});
```

### 🔍 `filter()`

**Purpose:** To filter elements based on a condition and return a **new array** containing only elements that satisfy the condition.

**Syntax:**
```
const newArray = array.filter((element, index, array) => {
  return condition;
});
```

### ➕ `reduce()`

**Purpose:** To **accumulate** all array elements into a single value (like sum, product, object, etc.)

**Syntax:**
```
const result = array.reduce((accumulator, currentValue, index, array) => {
  return updatedAccumulator;
}, initialValue);
```
Example 1 (Sum of all numbers):
```
const numbers = [1, 2, 3, 4];
const total = numbers.reduce((acc, num) => acc + num, 0);
console.log(total); // 10
```
Example 2 (Count occurrences):
```
const fruits = ['apple', 'banana', 'apple', 'orange', 'banana'];
const count = fruits.reduce((acc, fruit) => {
  acc[fruit] = (acc[fruit] || 0) + 1;
  return acc;
}, {});
console.log(count);
// { apple: 2, banana: 2, orange: 1 }
```

### 🔁 Summary
|Method|Purpose|Returns|Changes Original?|
|---|---|---|---|
|`map()`|Transform each element|New array|❌ No|
|`filter()`|Keep elements that pass a test|New array|❌ No|
|`reduce()`|Combine all elements into one value|Any value (number, string, object)|❌ No

