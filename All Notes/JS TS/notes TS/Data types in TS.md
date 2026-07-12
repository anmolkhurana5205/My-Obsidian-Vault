## Primitive Types
|Type|Example|Description|
|---|---|---|
|`string`|`"Anmol"`|Text values|
|`number`|`42`, `3.14`|Integers & floats both|
|`boolean`|`true`, `false`|True or false|
|`null`|`null`|Empty value (intentional absence)|
|`undefined`|`undefined`|Not assigned yet|
|`bigint`|`9007199254740991n`|Large integers beyond `Number.MAX_SAFE_INTEGER`|
|`symbol`|`Symbol('id')`|Unique identifiers (rarely used)|
## Special Types
| Type      | Example                                                 | Description                                |
| --------- | ------------------------------------------------------- | ------------------------------------------ |
| `any`     | `let data: any = "hello";`                              | Turns off type checking for that variable  |
| `unknown` | `let value: unknown = 10;`                              | Like `any`, but must be checked before use |
| `never`   | `function error(): never { throw new Error("Error"); }` | Function that never returns                |
| `void`    | `function log(): void { console.log("Hi"); }`           | No return value (like `void` in Java)      |

## Object Types
Objects can have specific structures:
```
let user: { name: string; age: number } = {
  name: "Anmol",
  age: 21
};
```
- You can also define reusable structures using **interface** or **type**:
```
interface User {
  name: string;
  age: number;
}
```

## Array
```
let numbers: number[] = [1, 2, 3];
let names: Array<string> = ["Anmol", "Khurana"];
```

## Tuple
```
let person: [string, number] = ["Anmol", 21];
```

## Enum
```
enum Direction {
  Up,
  Down,
  Left,
  Right
}
let move: Direction = Direction.Up;
```

## Union & Intersection
```
let value: string | number; // union
interface A { a: number }
interface B { b: string }
type AB = A & B; // intersection
```

## Literal Types
```
let direction: "up" | "down" | "left" | "right";
direction = "up";
```

## Function Types
You can type both parameters and return values:
```
function add(a: number, b: number): number {
  return a + b;
}
```

## Generics
Used to make functions reusable while keeping type safety:
```
function identity<T>(value: T): T {
  return value;
}
let num = identity<number>(5);
```
Similar to **C++ templates** or **Java generics**.

## Summary
✅ **Core Types**: string, number, boolean, null, undefined, bigint, symbol  
✅ **Advanced Types**: any, unknown, void, never  
✅ **Data Structures**: object, array, tuple, enum  
✅ **Type Combinations**: union, intersection, literal, generics

