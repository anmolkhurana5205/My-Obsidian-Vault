#typescript #types #narrowing

## Literal Types

Restrict to exact values.

```typescript
type Direction = "north" | "south" | "east" | "west";
let dir: Direction = "north"; // OK
dir = "up"; // ❌ Error

type DiceRoll = 1 | 2 | 3 | 4 | 5 | 6;
```

## Type Narrowing

TypeScript narrows types inside conditionals.

### `typeof` guard

```typescript
function process(val: string | number) {
  if (typeof val === "string") {
    console.log(val.toUpperCase()); // string
  } else {
    console.log(val.toFixed(2));    // number
  }
}
```

### `instanceof` guard

```typescript
class Dog { bark() {} }
class Cat { meow() {} }

function speak(animal: Dog | Cat) {
  if (animal instanceof Dog) animal.bark();
  else animal.meow();
}
```

### `in` operator guard

```typescript
type Fish = { swim(): void };
type Bird = { fly(): void };

function move(pet: Fish | Bird) {
  if ("swim" in pet) pet.swim();
  else pet.fly();
}
```

### Truthiness narrowing

```typescript
function greet(name: string | null) {
  if (name) console.log("Hello " + name);
  else console.log("Hello stranger");
}
```

### Equality narrowing

```typescript
function check(x: string | number, y: string | boolean) {
  if (x === y) {
    console.log(x.toUpperCase()); // x is string here
  }
}
```

---

← [[06 - Union & Intersection Types]] | → [[08 - Enums]]