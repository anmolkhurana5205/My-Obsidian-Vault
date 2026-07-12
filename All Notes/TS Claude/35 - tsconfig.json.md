#typescript #config

```json
{
  "compilerOptions": {
    "target": "ES2020",        // output JS version
    "module": "commonjs",      // module system
    "strict": true,            // enable all strict checks
    "outDir": "./dist",        // output directory
    "rootDir": "./src",        // source directory
    "esModuleInterop": true,   // default imports from CJS modules
    "resolveJsonModule": true, // import JSON files
    "sourceMap": true,         // generate source maps
    "declaration": true        // generate .d.ts files
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules"]
}
```

## Key Compiler Options

|Option|Purpose|
|---|---|
|`strict`|Enables all strict type checks|
|`noImplicitAny`|Error on implicit `any`|
|`strictNullChecks`|`null`/`undefined` are distinct|
|`noUnusedLocals`|Error on unused variables|
|`noImplicitReturns`|All paths must return|
|`paths`|Module path aliases|
|`lib`|Built-in type definitions to include|

---

← [[24 - Advanced Types]] | → [[38 - TypeScript with DOM]]