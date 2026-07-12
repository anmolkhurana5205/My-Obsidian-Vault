#typescript #modules

Type definitions for JavaScript libraries (no implementation, only types).

```typescript
// myLib.d.ts
declare function greet(name: string): string;
declare const version: string;
declare class Person {
  constructor(name: string);
  sayHello(): void;
}
```

## `@types` packages

```bash
npm install --save-dev @types/node
npm install --save-dev @types/express
```

---

