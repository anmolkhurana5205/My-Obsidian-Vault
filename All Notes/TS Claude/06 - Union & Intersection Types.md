#typescript #types

## Union Types (`|`)

A value can be **one of** several types.

```typescript
let id: string | number;
id = "abc"; // OK
id = 42;    // OK
id = true;  // ❌ Error

function printId(id: string | number) {
  console.log(id.toString());
}
```

## Intersection Types (`&`)

A value must satisfy **all** the types.

```typescript
type A = { name: string };
type B = { age: number };
type C = A & B;

const person: C = { name: "Alice", age: 30 };
```

## Union with Objects

```typescript
type Cat = { meow(): void };
type Dog = { bark(): void };

function makeSound(pet: Cat | Dog) {
  if ("meow" in pet) pet.meow();
  else pet.bark();
}
```

> [!info] Use `in` operator or discriminant fields to narrow union types.

---

← [[05 - Type Aliases]] | → [[07 - Literal Types & Type Narrowing]]