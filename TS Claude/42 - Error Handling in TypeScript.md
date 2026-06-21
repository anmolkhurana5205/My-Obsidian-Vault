#typescript #errors

## `unknown` in catch (TS 4.0+)

```typescript
try {
  throw new Error("Oops");
} catch (err) {
  if (err instanceof Error) {
    console.log(err.message);
  }
}
```

## Custom Error Classes

```typescript
class ValidationError extends Error {
  constructor(message: string, public field: string) {
    super(message);
    this.name = "ValidationError";
  }
}

try {
  throw new ValidationError("Required", "email");
} catch (e) {
  if (e instanceof ValidationError) {
    console.log(e.field, e.message);
  }
}
```

## Result Pattern (no exceptions)

```typescript
type Result<T, E = Error> =
  | { success: true; data: T }
  | { success: false; error: E };

function divide(a: number, b: number): Result<number> {
  if (b === 0) return { success: false, error: new Error("Division by zero") };
  return { success: true, data: a / b };
}
```

---

