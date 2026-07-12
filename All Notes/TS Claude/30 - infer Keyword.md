#typescript #advanced-types

Used inside conditional types to **infer** (extract) a type.

```typescript
// Get the return type of a function
type ReturnType<T> = T extends (...args: any[]) => infer R ? R : never;

// Get the first argument type
type FirstArg<T> = T extends (first: infer F, ...rest: any[]) => any ? F : never;

type F = FirstArg<(x: string, y: number) => void>; // string
```

## Unwrap Promise

```typescript
type UnwrapPromise<T> = T extends Promise<infer U> ? U : T;
type R = UnwrapPromise<Promise<number>>; // number
```

---

← [[23 - Utility Types]] | → [[31 - Modules]]