#typescript #types

## What is Type Inference?

TypeScript automatically deduces the type from the assigned value — no annotation needed.

```typescript
let score = 100;       // inferred as number
let title = "Hello";   // inferred as string
let active = true;     // inferred as boolean
```

## Inference in Functions

```typescript
function add(a: number, b: number) {
  return a + b; // return type inferred as number
}
```

## Contextual Typing

```typescript
const nums = [1, 2, 3]; // number[]
nums.push("hi");         // ❌ Error
```

> [!tip] Always annotate function parameters. Let TS infer return types when obvious.

---

← [[02 - Types & Type Annotations]] | → [[04 - Interfaces]]