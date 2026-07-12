#typescript #patterns

## Pattern

Use a common literal field (`kind`, `type`, `tag`) to distinguish union members.

```typescript
type Circle = { kind: "circle"; radius: number };
type Square = { kind: "square"; side: number };
type Shape = Circle | Square;

function area(shape: Shape): number {
  switch (shape.kind) {
    case "circle": return Math.PI * shape.radius ** 2;
    case "square": return shape.side ** 2;
  }
}
```

## Exhaustiveness Check

```typescript
function assertNever(x: never): never {
  throw new Error("Unhandled case: " + x);
}

// Add default: assertNever(shape) to catch missing cases
```

---

