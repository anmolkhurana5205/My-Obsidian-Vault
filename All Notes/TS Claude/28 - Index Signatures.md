#typescript #types

```typescript
interface StringMap {
  [key: string]: string;
}

const dict: StringMap = {
  hello: "world",
  foo: "bar"
};
```

## With Known + Dynamic Keys

```typescript
interface Config {
  name: string;            // known key
  [key: string]: unknown;  // dynamic keys (must be compatible)
}
```

---

