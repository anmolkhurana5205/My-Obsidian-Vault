**CommonJS (CJS)** is the **module system** that Node.js originally used before JavaScript officially introduced the `import`/`export` (ES Modules or ESM).

In CommonJS, every file is treated as a **separate module**, and we use two keywords:

- `require()` → to import things
- `module.exports` → to export things

```
math.js
function add(a, b) {
  return a + b;
}

function subtract(a, b) {
  return a - b;
}

// Export functions
module.exports = { add, subtract };
```

```
app.js
const math = require('./math');

console.log(math.add(10, 5));      // 15
console.log(math.subtract(10, 5)); // 5
```


|Feature|CommonJS (CJS)|ES Modules (ESM)|
|---|---|---|
|Import syntax|`const x = require('x')`|`import x from 'x'`|
|Export syntax|`module.exports = x`|`export default x`|
|File extension|`.js`|`.mjs` or `.js` (with `"type": "module"`)|
|Synchronous or Asynchronous|Synchronous|Asynchronous|
|Supported by default in|Node.js|Modern browsers, Node 14+ with config|
|`__dirname` and `__filename`|✅ available|❌ not available|

