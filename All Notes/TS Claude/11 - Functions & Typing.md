#typescript #functions

## Basic Function Typing

```typescript
function add(a: number, b: number): number {
  return a + b;
}
```

## Function Type Expression

```typescript
type Callback = (event: string) => void;

function listen(cb: Callback) {
  cb("click");
}
```

## Void vs Never

```typescript
function log(): void { console.log("hi"); }       // returns undefined
function crash(): never { throw new Error("!"); } // never returns
```

