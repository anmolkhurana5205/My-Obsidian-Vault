#typescript #functions

## Arrow Function Syntax

```typescript
const multiply = (a: number, b: number): number => a * b;
```

## `this` Parameter

TypeScript lets you explicitly type `this` as the first (fake) parameter.

```typescript
interface Counter {
  count: number;
  increment(this: Counter): void;
}

const c: Counter = {
  count: 0,
  increment() { this.count++; }
};
```

## Arrow Functions Capture `this`

```typescript
class Timer {
  seconds = 0;

  start() {
    setInterval(() => {
      this.seconds++; // 'this' is Timer, not window
    }, 1000);
  }
}
```

## `noImplicitThis` (tsconfig)

Enables an error when `this` has an implicit `any` type.

---

← [[13 - Rest Parameters & Overloads]] | → [[15 - Classes]]