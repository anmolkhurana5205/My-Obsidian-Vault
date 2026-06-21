#typescript #arrays

## Array Types

```typescript
let nums: number[] = [1, 2, 3];
let strs: Array<string> = ["a", "b"]; // generic syntax
```

## Multidimensional

```typescript
let matrix: number[][] = [[1, 2], [3, 4]];
```

## Readonly Arrays

```typescript
const arr: readonly number[] = [1, 2, 3];
arr.push(4); // ❌ Error

// or
const arr2: ReadonlyArray<number> = [1, 2, 3];
```

## Array of Objects

```typescript
interface User { name: string; age: number }
const users: User[] = [
  { name: "Alice", age: 30 },
  { name: "Bob", age: 25 }
];
```

## Common Array Methods (typed)

```typescript
const doubled = nums.map((n: number) => n * 2);
const evens = nums.filter((n) => n % 2 === 0);
const sum = nums.reduce((acc, n) => acc + n, 0);
```

---

← [[09 - Tuples]] | → [[11 - Functions & Typing]]