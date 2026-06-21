#typescript #types

## Custom Type Guard (`is`)

```typescript
interface Cat { meow(): void }
interface Dog { bark(): void }

function isCat(pet: Cat | Dog): pet is Cat {
  return (pet as Cat).meow !== undefined;
}

function interact(pet: Cat | Dog) {
  if (isCat(pet)) pet.meow();
  else pet.bark();
}
```

## `as` Type Assertion

```typescript
const input = document.getElementById("name") as HTMLInputElement;
input.value = "Alice";
```

## Non-null Assertion (`!`)

```typescript
const el = document.getElementById("app")!; // guaranteed non-null
```

> [!warning] Avoid overusing `as` and `!`. They bypass the type system.

## `satisfies` Operator (TS 4.9+)

```typescript
const palette = {
  red: [255, 0, 0],
  green: "#00ff00"
} satisfies Record<string, string | number[]>;

palette.red.map(n => n); // still typed as number[], not (string | number[])
```

---

