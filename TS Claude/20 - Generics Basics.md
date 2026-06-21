#typescript #generics

## What are Generics?

Write reusable code that works with **any type**, without losing type safety.

```typescript
function identity<T>(value: T): T {
  return value;
}

identity<string>("hello"); // "hello"
identity<number>(42);      // 42
identity("inferred");      // T inferred as string
```

## Generic Arrays

```typescript
function firstElement<T>(arr: T[]): T {
  return arr[0];
}
firstElement([1, 2, 3]);       // number
firstElement(["a", "b", "c"]); // string
```

## Multiple Type Parameters

```typescript
function pair<K, V>(key: K, val: V): [K, V] {
  return [key, val];
}
pair("name", "Alice"); // [string, string]
pair(1, true);          // [number, boolean]
```

---

