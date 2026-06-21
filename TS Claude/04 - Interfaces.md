#typescript #interfaces

## Defining an Interface

```typescript
interface User {
  name: string;
  age: number;
}

const alice: User = { name: "Alice", age: 30 };
```

## Optional Properties

```typescript
interface Product {
  id: number;
  name: string;
  discount?: number; // optional
}
```

## Readonly Properties

```typescript
interface Point {
  readonly x: number;
  readonly y: number;
}

const p: Point = { x: 5, y: 10 };
p.x = 1; // ❌ Error: readonly
```

## Function Types in Interface

```typescript
interface Greeter {
  greet(name: string): string;
}

const obj: Greeter = {
  greet: (name) => `Hello, ${name}`
};
```

## Extending Interfaces

```typescript
interface Animal {
  name: string;
}

interface Dog extends Animal {
  breed: string;
}

const d: Dog = { name: "Rex", breed: "Labrador" };
```

## Interface Merging (Declaration Merging)

```typescript
interface Box { width: number; }
interface Box { height: number; }
// merged: Box has both width and height
```

> [!info] Interfaces can be **extended** and **merged**. This is unlike type aliases.

---

← [[03 - Type Inference]] | → [[05 - Type Aliases]]