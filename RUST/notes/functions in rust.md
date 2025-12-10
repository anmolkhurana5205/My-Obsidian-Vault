### Basic Function
```
fn greet() {
    println!("Hello!");
}
```
Call it like this:
```
greet();
```

### Functions with Parameters
```
fn add(a: i32, b: i32) {
    println!("Sum = {}", a + b);
}
```
Call:
```
add(5, 10);
```


### Functions with Return Value
Rust functions return a value using the **last expression (no semicolon)**.
```
fn add(a: i32, b: i32) -> i32 {
    a + b  // implicit return
}
```
Using `return` also works:
```
fn add(a: i32, b: i32) -> i32 {
    return a + b;
}
```


### Explicit Return vs Implicit Return
Implicit (preferred):
```
a + b
```
Explicit
```
return a + b;
```
Important:  
❗ If you put a semicolon (`;`) after the last value, it becomes a **statement**, not a return value.


### Function with no return (`()`)
```
fn hello() {
    println!("Hi!");
    // returns unit type ()
}
```

### Multiple parameters with types
Every parameter needs a type:
```
fn display(name: &str, age: u32) {
    println!("{} is {} years old", name, age);
}
```


### Functions returning multiple values (tuples)
```
fn stats() -> (i32, i32) {
    (10, 20)
}
```
Usage:
```
let (x, y) = stats();
println!("x={}, y={}", x, y);
```


### Functions with ownership (`String`)
```
fn take_string(s: String) {
    println!("{}", s);
}
```
This **moves** the string.


### Borrowing (`&str` or `&String`)
```
fn borrow_string(s: &str) {
    println!("{}", s);
}
```
This does **not** take ownership.


### Mutable references
```
fn change(value: &mut i32) {
    *value += 1;
}

let mut x = 5;
change(&mut x);
println!("{}", x); // 6
```


### Function with generics
```
fn print_any<T: std::fmt::Debug>(value: T) {
    println!("{:?}", value);
}
```


### Closures (functions stored in variables)
```
let add = |a: i32, b: i32| a + b;

println!("{}", add(3, 4));
```


## Summary
Functions in Rust:
- Use `fn` keyword
- Parameters need types
- Return type goes after `->`
- Last expression (no `;`) returns value
- Ownership rules apply
- Can return tuples, use generics, and support closures

