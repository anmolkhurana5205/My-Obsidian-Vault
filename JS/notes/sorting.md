## 🔢 **1. Numeric Sorting (numbers or numeric-like strings)**

```
👉 Use subtraction:
const items = [
  { name: "apple", price: 100 },
  { name: "banana", price: 20 },
  { name: "cherry", price: 70 },
  { name: "mango", price: "50" } // numeric string
];

// Ascending numeric sort
items.sort((a, b) => a.price - b.price);
console.log("Numeric Ascending:", items);

// Descending numeric sort
items.sort((a, b) => b.price - a.price);
console.log("Numeric Descending:", items);
✅ Works because `"50"` gets coerced to number `50`.
```

## 🔤 **2. String Sorting (alphabetical order)**

```
👉 Use `localeCompare`:
const items2 = [
  { name: "Banana" },
  { name: "apple" },
  { name: "cherry" }
];

// Case-sensitive alphabetical
items2.sort((a, b) => a.name.localeCompare(b.name));
console.log("Alphabetical:", items2);

// Case-insensitive alphabetical
items2.sort((a, b) => a.name.toLowerCase().localeCompare(b.name.toLowerCase()));
console.log("Alphabetical (case-insensitive):", items2);
✅ `localeCompare` handles alphabets, accents, case-sensitivity, and even locale-specific sorting (like `ä` vs `a`).
```

## 🔑 Rule Recap

- **Numeric sort** → `a.prop - b.prop`
    
- **String sort** → `a.prop.localeCompare(b.prop)`

## ⚡ Bonus: 
You can **combine both** (e.g., sort by price first, then by name if prices are equal):
```
items.sort((a, b) => a.price - b.price || a.name.localeCompare(b.name));
```

