### Basic Print
```
println!("Hello, world!");
```

### Print variables
Using `{}`:
```
let x = 10;
println!("The value of x is {}", x);
```

### Multiple variables
```
let a = 5;
let b = 10;
println!("a = {}, b = {}", a, b);
```

### Formatted printing (like Python f-strings)
```
let name = "anmol";
let age = 20;

println!("{name} is {age} years old");
```

### Print without new line
```
print!("Hello ");
print!("world");
```

## Bonus: Debug print with `{:?}` (for complex types)
```
let arr = [1, 2, 3];
println!("{:?}", arr);
```
