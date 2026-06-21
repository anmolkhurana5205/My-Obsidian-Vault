#typescript #advanced-types

## `keyof` — get keys of a type

```typescript
type User = { name: string; age: number };
type Keys = keyof User; // "name" | "age"
```

## `typeof` — get type of a value

```typescript
const config = { port: 3000, host: "localhost" };
type Config = typeof config;
// { port: number; host: string }

function add(a: number, b: number) { return a + b; }
type AddFn = typeof add; // (a: number, b: number) => number
```

## Combined

```typescript
function getValue<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}
```

---

