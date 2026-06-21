## Rest Parameters

```typescript
function sum(...nums: number[]): number {
  return nums.reduce((a, b) => a + b, 0);
}
sum(1, 2, 3, 4); // 10
```

## Function Overloads

Define multiple signatures, one implementation.

```typescript
function format(val: string): string;
function format(val: number): string;
function format(val: string | number): string {
  return val.toString();
}
```

---

← [[10 - Arrays & Readonly]] | → [[12 - Optional & Default Parameters]]