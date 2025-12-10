### Rust has **no Garbage Collector**
- Languages like Java, Python, JS use a **GC** that runs in the background and frees unused memory.
- Rust does **not** use a GC.

Instead, Rust uses:
> **Ownership + Borrowing + Lifetimes**  
> to manage memory at compile time.

This makes Rust:
- **Fast like C++**
- **Safe like Java/Python**
- **Zero runtime overhead**

### Ownership — the core rule
#### Rule 1: Every value has exactly **one owner**
```
let s = String::from("hello"); // s owns the string
```

#### Rule 2: When the owner goes out of scope → memory is freed
```
{
    let s = String::from("hello"); // allocated
} // s is dropped automatically here
```

#### Rule 3: Assigning a value **moves** (not copies) it
```
let s1 = String::from("hello");
let s2 = s1; // s1 is moved to s2
```
Now `s1` is INVALID.
This prevents double free.

### Borrowing — references (&)
You can **borrow** data without taking ownership.
#### Immutable borrow:
```
fn show(s: &String) {
    println!("{}", s);
}
```
You can have **many immutable borrows**.

#### Mutable borrow:
```
fn change(s: &mut String) {
    s.push_str(" world");
}
```
But:  
❗ **Only ONE mutable reference at a time**
This prevents data races.


### Lifetimes — how long references are valid
Rust tracks reference lifetimes **at compile time**.
Example:
```
fn get_ref<'a>(x: &'a i32) -> &'a i32 {
    x
}
```
Lifetimes prevent **dangling pointers**.
Compiler ensures:  
✔ reference never outlives the data  
✔ memory-safe without runtime checks


### Stack vs Heap
#### Stack
- Fast
- Fixed size
- Stores simple values (`i32`, `bool`, etc.)
```
let x = 10; // stored on stack
```
#### Heap
- Slow but flexible
- Stores dynamic data (`String`, `Vec`, etc.)
```
let s = String::from("hello"); // data on heap
```
Rust handles heap allocation using:
- `Box<T>` → put value on heap
- `Vec<T>` → dynamic array
- `String` → growable string


### RAII — automatic cleanup
Rust automatically frees memory when a variable goes out of scope.

This is called:  
**RAII (Resource Acquisition Is Initialization)** — same idea as C++ smart pointers.


### Smart Pointers
Rust has powerful smart pointers:
#### `Box<T>` – heap allocation
```
let b = Box::new(5);
```

#### `Rc<T>` – reference counting (shared ownership)
```
use std::rc::Rc;

let a = Rc::new(5);
let b = Rc::clone(&a);
```
### `RefCell<T>` – mutable borrow checked at runtime

Allows mutation in immutable contexts.


### No memory leaks?
Rust prevents:  
✔ dangling pointers  
✔ double free  
✔ use-after-free  
✔ data races

but **memory leaks are possible** (rare) using:

- `Rc` cycles
    
- `std::mem::forget()`
    

Rust prevents unsafe memory issues unless you use `unsafe`.