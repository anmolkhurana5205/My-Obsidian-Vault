### `loop` (infinite loop)
Runs forever unless you `break`.
```
loop {
    println!("This prints forever!");
    break; // stop the loop
}
```

With a counter:
```
let mut x = 0;

loop {
    x += 1;
    println!("x = {}", x);

    if x == 5 {
        break;
    }
}
```


### `while` loop
Runs while the condition is true.
```
let mut n = 0;

while n < 5 {
    println!("n = {}", n);
    n += 1;
}
```


### `for` loop — most common
Rust’s `for` loop iterates over anything iterable (ranges, arrays, strings, etc.)

Iterate over a range
```
for i in 0..5 { // 0 to 4
    println!("{}", i);
}
```

Inclusive range:
```
for i in 0..=5 { // 0 to 5
    println!("{}", i);
}
```


### Looping over an array
```
let nums = [10, 20, 30];

for num in nums {
    println!("{}", num);
}
```


### Looping over characters
```
for c in "hello".chars() {
    println!("{}", c);
}
```


### Using `break` and `continue
`break` stops the loop:`
```
for i in 1..10 {
    if i == 5 {
        break;
    }
    println!("{}", i);
}
```

`continue` skips one iteration:
```
for i in 1..10 {
    if i % 2 == 0 {
        continue; // skip even numbers
    }
    println!("{}", i);
}
```


### Labeled loops (Rust feature)
Useful when you have nested loops and want to break the outer loop.
```
'outer: for i in 1..5 {
    for j in 1..5 {
        if j == 3 {
            break 'outer; // break the outer loop
        }
    }
}
```


### Returning a value from `loop`
Rust allows loops to return a value:
```
let mut counter = 0;

let result = loop {
    counter += 1;

    if counter == 5 {
        break counter * 2; // loop returns 10
    }
};

println!("Result = {}", result);
```


