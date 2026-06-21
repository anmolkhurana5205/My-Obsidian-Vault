#typescript #advanced-types

## Basic Mapped Type

```typescript
type Optional<T> = {
  [K in keyof T]?: T[K];
};
```

## Readonly Mapped Type

```typescript
type Frozen<T> = {
  readonly [K in keyof T]: T[K];
};
```

## Remapping Keys with `as`

```typescript
type Getters<T> = {
  [K in keyof T as `get${Capitalize<string & K>}`]: () => T[K];
};

type User = { name: string; age: number };
type UserGetters = Getters<User>;
// { getName: () => string; getAge: () => number }
```

---

