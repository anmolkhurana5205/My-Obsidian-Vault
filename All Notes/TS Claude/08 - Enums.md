#typescript #enums

## Numeric Enum (default)

```typescript
enum Direction {
  Up,    // 0
  Down,  // 1
  Left,  // 2
  Right  // 3
}

let move: Direction = Direction.Up;
console.log(move); // 0
```

## Custom Numeric Values

```typescript
enum Status {
  Active = 1,
  Inactive = 5,
  Pending = 10
}
```

## String Enum

```typescript
enum Color {
  Red = "RED",
  Green = "GREEN",
  Blue = "BLUE"
}
```

## Const Enum (inlined at compile time — no object generated)

```typescript
const enum Sizes { Small, Medium, Large }
let s = Sizes.Medium; // compiled to: let s = 1;
```

## Reverse Mapping (Numeric only)

```typescript
enum Role { Admin = 1, User }
console.log(Role[1]); // "Admin"
```

> [!warning] Prefer `const enum` or union literal types over regular enums for better tree-shaking.

---

← [[07 - Literal Types & Type Narrowing]] | → [[09 - Tuples]]