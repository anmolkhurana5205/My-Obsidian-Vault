#typescript #basics

## What is TypeScript?

TypeScript is a **statically typed superset of JavaScript** developed by Microsoft. It compiles down to plain JavaScript and adds optional type annotations, interfaces, and advanced OOP features.

> [!tip] Key Benefit Catch errors at **compile time** instead of runtime.

## JS vs TS

|Feature|JavaScript|TypeScript|
|---|---|---|
|Typing|Dynamic|Static (optional)|
|Error detection|Runtime|Compile time|
|IDE support|Basic|Excellent|
|Compilation needed|No|Yes|

## Installation

```bash
npm install -g typescript
tsc --version
```

## Compiling

```bash
tsc hello.ts        # compiles to hello.js
tsc --watch hello.ts  # watch mode
```

## First Program

```typescript
let message: string = "Hello, TypeScript!";
console.log(message);
```

## Init a TS project

```bash
tsc --init   # creates tsconfig.json
```

---

← [[00 - TypeScript MOC]] | → [[02 - Types & Type Annotations]]