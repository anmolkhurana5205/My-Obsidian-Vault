- (Download the TypeScript compiler from the npm registry.)
```
yarn add typescript --dev
```

- This will create a tsconfig.json — a configuration file that controls how TypeScript compiles your code.
```
npx tsc --init
```

```
{
	"compilerOptions": {
	  "target": "ES6",                // JavaScript version output
	  "module": "commonjs",           // Module system (ESNext, CommonJS, etc.)
	  "rootDir": "./src",             // Source TS files
	  "outDir": "./dist",             // Compiled JS output
	  "strict": true,                 // Enable all strict type checking
	  "esModuleInterop": true,        // Allow default imports from CommonJS modules
	  "forceConsistentCasingInFileNames": true,
	  "skipLibCheck": true
	}
}
```

- Then create two folders:
```
mkdir src dist
```

- Inside `src`, create a file `index.ts`:
```
function greet(name: string): string {
  return `Hello, ${name}!`;
}

let user = "Anmol";
console.log(greet(user));
```
Notice how we **specify types**:

- `name: string` → means this function only accepts strings.
- The function returns a `string`.

- Compile TypeScript to JavaScript
```
npx tsc
```
Now open the `dist` folder — you’ll see a file named `index.js`.

- Run it with Node:
```
node dist/index.js
```

- Auto-Compile with Watch Mode
	- Instead of running `npx tsc` every time, use:
```
npx tsc --watch
```

- Running TypeScript Directly (Optional)
	- You can also run TypeScript files directly (without compiling manually) using **ts-node**:
	- ts-node - **TypeScript execution engine** for Node.js.
	- Normally, Node.js can only run JavaScript. To run TypeScript, you’d first have to **compile `.ts` → `.js`** using `tsc`.  
	- But with `ts-node`, you can **run TypeScript files directly** without manually compiling them first.
```
npm install -D ts-node
```

