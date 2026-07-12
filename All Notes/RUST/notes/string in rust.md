## `&str` — String Slice (Fixed, read-only)
```
let s: &str = "hello";
```
### Properties:

- Stored in **read-only memory**
    
- **Immutable** (cannot be changed)
    
- Fast, lightweight
    
- Commonly used for string literals
    

Think of it as:  
✔ "a view into a string"  
✔ "borrowed string"


## `String` — Growable, heap-allocated
```
let mut s = String::from("hello");
```

### Properties:

- Stored in **heap**
    
- **Growable** (push, append, modify)
    
- Owned type (`String` owns its data)
    
- Used for dynamic text


## Create a String
```
let s1 = String::from("hello");
let s2 = "hello".to_string();
let s3 = String::new(); // empty string
```


## Add to String
```
let mut s = String::from("hello");

s.push('!');      // add one char
s.push_str(" world"); // add a string slice
```


## Concatenation
Using `+`
```
let s1 = String::from("Hello ");
let s2 = String::from("World");
let s3 = s1 + &s2;  // s1 is moved
```

Using `format!` (recommended)
```
let name = "anmol";
let age = 20;

let msg = format!("{} is {} years old", name, age);
```


## Length of String
```
let s = String::from("hello");
println!("{}", s.len()); // 5
```

## Slicing Strings (careful!)
Rust strings are UTF-8, so slicing must follow character boundaries:
```
let s = "Hello";
let slice = &s[0..3]; // works for ASCII
```


## Looping through characters
```
for c in "hello".chars() {
    println!("{}", c);
}
```


## Looping through bytes
```
for b in "hello".bytes() {
    println!("{}", b);
}
```


## Convert between `&str` and `String`
`&str` → `String`
```
let s = "hello".to_string();
```

`String` → `&str`
```
let s = String::from("hello");
let slice: &str = &s;
```


## Why Rust has two types?
Rust separates them for:
- **Memory safety**
- **Speed**
- **No runtime GC**
- **Clear ownership rules**
You use:

| Use case                 | Type     |
| ------------------------ | -------- |
| static text, literals    | `&str`   |
| user input, dynamic text | `String` |

## Compare Strings
```
let a = String::from("hello");
let b = "hello";

println!("{}", a == b); // true
```


## Summary
### Rust has **two string types**:
- **`&str`** → fixed, read-only
- **`String`** → growable, heap-allocated
### You can:
- Create
- Append
- Slice
- Convert
- Iterate
- Format