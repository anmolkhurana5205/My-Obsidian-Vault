## ✅ `slice()`

- **Does not change** the original array.
    
- Returns a **new array**.
    
- Used to **extract** a portion of an array.
```
array.slice(start, end)
```

- `start` = index to begin (inclusive).
    
- `end` = index to stop (exclusive).

```
const arr = [1, 2, 3, 4, 5];

console.log(arr.slice(1, 4)); // [2, 3, 4]
console.log(arr);             // [1, 2, 3, 4, 5] (unchanged)
```

## ✅ `splice()`

- **Changes** (mutates) the original array.
    
- Can **add, remove, or replace** elements.

```
array.splice(start, deleteCount, item1, item2, ...)
```

- `start` = index where changes begin.
    
- `deleteCount` = how many items to remove.
    
- `item1, item2...` = items to insert (optional).

```
const arr = [1, 2, 3, 4, 5];

// Remove 2 elements starting from index 1
console.log(arr.splice(1, 2)); // [2, 3] (removed items)
console.log(arr);              // [1, 4, 5] (original mutated)

// Insert elements
arr.splice(1, 0, 100, 200);
console.log(arr); // [1, 100, 200, 4, 5]

// Replace elements
arr.splice(2, 1, 300);
console.log(arr); // [1, 100, 300, 4, 5]
```

