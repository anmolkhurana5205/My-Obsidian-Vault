#typescript #advanced-types

## Syntax: `T extends U ? X : Y`

```typescript
type IsString<T> = T extends string ? true : false;

type A = IsString<string>; // true
type B = IsString<number>; // false
```

## With `infer`

Extract a type from within another type.

```typescript
type UnpackArray<T> = T extends (infer U)[] ? U : T;

type A = UnpackArray<string[]>; // string
type B = UnpackArray<number>;   // number
```

## Distributive Conditional Types

When `T` is a union, the condition is applied to each member.

```typescript
type ToArray<T> = T extends any ? T[] : never;
type R = ToArray<string | number>; // string[] | number[]
```

---

