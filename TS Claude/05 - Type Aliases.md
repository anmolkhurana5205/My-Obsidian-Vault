#typescript #types

## Defining a Type Alias

```typescript
type ID = string | number;
type Point = { x: number; y: number };

let userId: ID = "abc123";
let pos: Point = { x: 1, y: 2 };
```

## Aliases for Functions

```typescript
type MathFn = (a: number, b: number) => number;

const add: MathFn = (a, b) => a + b;
```

## Extending via Intersection

```typescript
type Animal = { name: string };
type Pet = Animal & { owner: string };
```

> [!tip] Interface vs Type Alias Use **interface** for objects/classes. Use **type** for unions, primitives, and complex compositions.

---

← [[04 - Interfaces]] | → [[06 - Union & Intersection Types]]