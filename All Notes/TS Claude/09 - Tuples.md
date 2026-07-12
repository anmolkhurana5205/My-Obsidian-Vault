#typescript #types

## What is a Tuple?

A fixed-length array with **known types at each position**.

```typescript
let person: [string, number] = ["Alice", 30];
console.log(person[0]); // "Alice"
console.log(person[1]); // 30
```

## Optional Tuple Elements

```typescript
let data: [string, number?] = ["hello"];
```

## Rest in Tuples

```typescript
type StringAndNumbers = [string, ...number[]];
let t: StringAndNumbers = ["Alice", 1, 2, 3];
```

## Named Tuple Elements (TS 4.0+)

```typescript
type Range = [start: number, end: number];
```

## Destructuring Tuples

```typescript
const [name, age] = ["Bob", 25];
```

## Readonly Tuple

```typescript
const point: readonly [number, number] = [1, 2];
point[0] = 5; // ❌ Error
```

---

← [[08 - Enums]] | → [[10 - Arrays & Readonly]]