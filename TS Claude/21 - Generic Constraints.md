#typescript #generics

## Using `extends` to constrain

```typescript
function getLength<T extends { length: number }>(val: T): number {
  return val.length;
}
getLength("hello");   // 5
getLength([1, 2, 3]); // 3
getLength(42);         // ❌ Error: number has no length
```

## `keyof` Constraint

```typescript
function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}

const user = { name: "Alice", age: 30 };
getProperty(user, "name"); // "Alice"
getProperty(user, "foo");  // ❌ Error
```

---

