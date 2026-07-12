It is used when you, as a developer, are **certain that a variable is not null or undefined**, even if TypeScript thinks it might be.

- To tell TypeScript “I know this value is definitely not null or undefined here,” you can use the **non-null assertion operator** `!`.

### Key Points:

- The operator is `!` after the variable.
- Use it **carefully**, because if the value **is actually null or undefined at runtime**, it will throw an error.

Example:
```
let name: string | null = getNameFromUser();
console.log(name!.length); // using '!' tells TypeScript it's not null
```
Here, `name!` asserts that `name` is **not null**. Without the `!`, TypeScript would give an error because `name` could be `null`.