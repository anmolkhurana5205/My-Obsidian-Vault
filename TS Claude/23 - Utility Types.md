#typescript #utility-types

> [!info] Built-in generic types that transform existing types. No imports needed.

## `Partial<T>` — all properties optional

```typescript
interface User { name: string; age: number; }
type PartialUser = Partial<User>;
// { name?: string; age?: number }
```

## `Required<T>` — all properties required

```typescript
type RequiredUser = Required<PartialUser>;
// { name: string; age: number }
```

## `Readonly<T>` — all properties readonly

```typescript
type ReadonlyUser = Readonly<User>;
// { readonly name: string; readonly age: number }
```

## `Record<K, V>` — map of keys to values

```typescript
type Roles = Record<string, boolean>;
const perms: Roles = { admin: true, guest: false };

type PageMap = Record<"home" | "about", string>;
```

## `Pick<T, K>` — select properties

```typescript
type NameOnly = Pick<User, "name">;
// { name: string }
```

## `Omit<T, K>` — exclude properties

```typescript
type NoAge = Omit<User, "age">;
// { name: string }
```

## `Exclude<T, U>` — exclude from union

```typescript
type T = Exclude<"a" | "b" | "c", "a">;
// "b" | "c"
```

## `Extract<T, U>` — keep matching union members

```typescript
type T = Extract<"a" | "b" | "c", "a" | "c">;
// "a" | "c"
```

## `NonNullable<T>` — remove null & undefined

```typescript
type T = NonNullable<string | null | undefined>;
// string
```

## `ReturnType<T>` — get function return type

```typescript
function getUser() { return { name: "Alice", age: 30 }; }
type User = ReturnType<typeof getUser>;
// { name: string; age: number }
```

## `Parameters<T>` — get function parameter types

```typescript
function add(a: number, b: number): number { return a + b; }
type Params = Parameters<typeof add>; // [number, number]
```

## `InstanceType<T>` — get class instance type

```typescript
class Logger {}
type L = InstanceType<typeof Logger>;
```

## `Awaited<T>` — unwrap Promise type

```typescript
type T = Awaited<Promise<string>>; // string
type T2 = Awaited<Promise<Promise<number>>>; // number
```

---

← [[20 - Generics]] | → [[24 - Conditional Types]]