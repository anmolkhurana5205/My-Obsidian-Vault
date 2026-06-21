#typescript #types

## Primitive Types

```typescript
let name: string = "Alice";
let age: number = 30;
let isAdmin: boolean = true;
let nothing: null = null;
let undef: undefined = undefined;
let big: bigint = 100n;
let sym: symbol = Symbol("id");
```

## `any` Type

Disables type checking. **Avoid when possible.**

```typescript
let data: any = 42;
data = "now a string"; // OK
data = true;           // OK
```

## `unknown` Type

Safer alternative to `any`. Must narrow before use.

```typescript
let input: unknown = getUserInput();
if (typeof input === "string") {
  console.log(input.toUpperCase()); // safe
}
```

## `void` Type

Used for functions that return nothing.

```typescript
function log(msg: string): void {
  console.log(msg);
}
```

## `never` Type

For functions that **never return** (throw or infinite loop).

```typescript
function fail(msg: string): never {
  throw new Error(msg);
}
```

## `object` Type

```typescript
let user: object = { name: "Alice" };
```

> [!warning] `object` is very broad. Prefer specific types or interfaces.

## Type Summary Table

|Type|Use Case|
|---|---|
|`string`|Text|
|`number`|Numbers (int + float)|
|`boolean`|true/false|
|`any`|Opt-out of typing|
|`unknown`|Safe untyped input|
|`void`|No return value|
|`never`|Unreachable code|
|`null` / `undefined`|Absence of value|

---

← [[01 - Introduction & Setup]] | → [[03 - Type Inference]]