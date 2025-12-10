### Basic variable
```
let x = 10;
```
Rust automatically figures out the type (`i32` by default).

### Mutable variable (changeable)
By default variables **cannot** be changed.
To make it changeable:
```
let mut y = 20;
y = 30;
```

### Explicit type
If you want to define the type:
```
let z: i32 = 5;
let name: &str = "anmol";
let pi: f64 = 3.14;
```

### Constants
Constants are always **uppercase**, cannot be `mut`, and must have type:
```
const PI: f64 = 3.14159;
```

### Shadowing
Redefining the same variable (allowed):
```
let a = 5;
let a = a + 1; // now a is 6
```

