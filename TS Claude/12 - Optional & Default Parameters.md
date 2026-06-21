## Optional Parameters

```typescript
function greet(name: string, greeting?: string): string {
  return `${greeting ?? "Hello"}, ${name}`;
}
greet("Alice");           // "Hello, Alice"
greet("Alice", "Hi");     // "Hi, Alice"
```

## Default Parameters

```typescript
function createUser(name: string, role: string = "user") {
  return { name, role };
}
```

