#typescript #advanced

```typescript
const id1 = Symbol("id");
const id2 = Symbol("id");
id1 === id2; // false — every Symbol is unique

// unique symbol (type-level uniqueness)
const KEY: unique symbol = Symbol("KEY");
type KeyType = typeof KEY;
```

## Symbols as Object Keys

```typescript
const sym = Symbol("secret");
const obj = { [sym]: 42 };
console.log(obj[sym]); // 42
```

---

