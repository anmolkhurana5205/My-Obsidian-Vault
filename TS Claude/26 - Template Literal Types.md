#typescript #advanced-types

```typescript
type Greeting = `Hello, ${string}`;
let g: Greeting = "Hello, Alice"; // OK

type EventName = "click" | "focus";
type Handler = `on${Capitalize<EventName>}`;
// "onClick" | "onFocus"
```

## With Unions

```typescript
type Axis = "x" | "y";
type PosNeg = "positive" | "negative";
type Combined = `${Axis}_${PosNeg}`;
// "x_positive" | "x_negative" | "y_positive" | "y_negative"
```

---

