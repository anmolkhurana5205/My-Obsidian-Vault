#typescript #modules

## Named Exports

```typescript
// math.ts
export function add(a: number, b: number): number { return a + b; }
export const PI = 3.14;

// main.ts
import { add, PI } from "./math";
```

## Default Export

```typescript
// greet.ts
export default function greet(name: string) {
  return `Hello, ${name}`;
}

// main.ts
import greet from "./greet";
```

## Re-exporting

```typescript
export { add, PI } from "./math";
export * from "./helpers";
```

## Import Types

```typescript
import type { User } from "./types"; // erased at compile time
```

---

