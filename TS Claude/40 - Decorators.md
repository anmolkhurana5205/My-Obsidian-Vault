#typescript #advanced

> [!info] Enable with `"experimentalDecorators": true` in tsconfig.

## Class Decorator

```typescript
function sealed(constructor: Function) {
  Object.seal(constructor);
  Object.seal(constructor.prototype);
}

@sealed
class BugReport {
  type = "report";
}
```

## Method Decorator

```typescript
function log(target: any, key: string, descriptor: PropertyDescriptor) {
  const original = descriptor.value;
  descriptor.value = function (...args: any[]) {
    console.log(`Calling ${key} with`, args);
    return original.apply(this, args);
  };
  return descriptor;
}

class Calculator {
  @log
  add(a: number, b: number) { return a + b; }
}
```

## Property Decorator

```typescript
function readonly(target: any, key: string) {
  Object.defineProperty(target, key, { writable: false });
}
```

## Parameter Decorator

```typescript
function logParam(target: any, key: string, index: number) {
  console.log(`Param at index ${index} in ${key}`);
}
```

---

