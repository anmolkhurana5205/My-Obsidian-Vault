**`fs-extra`** is an **extension of Node.js’s native `fs` module**.  
It has **all the methods of `fs`**, plus **extra convenient methods** that make file and directory operations much easier.
- Think of it as `fs` + “superpowers” 💪

## ⚙️ Why use fs-extra?

Node’s built-in `fs` is great, but it sometimes requires a lot of boilerplate code for tasks like:

- Copying directories
- Moving files
- Removing directories recursively

`fs-extra` gives you **simpler, promise-friendly methods** for these common tasks.

---
## ⚡ Basic Usage

### 1️⃣ Import
```
const fs = require('fs-extra');
// or using ES modules
import fs from 'fs-extra';
```

### 2️⃣ Common Methods
| Method                    | Description                            |
| ------------------------- | -------------------------------------- |
| `fs.copy(src, dest)`      | Copy a file or directory               |
| `fs.move(src, dest)`      | Move a file or directory               |
| `fs.remove(path)`         | Delete a file or directory recursively |
| `fs.ensureDir(path)`      | Create a directory if it doesn’t exist |
| `fs.readJson(file)`       | Read JSON file directly into an object |
| `fs.writeJson(file, obj)` | Write an object as JSON file           |
| `fs.pathExists(path)`     | Check if file/directory exists         |
| `fs.emptyDir(path)`       | Delete all contents of a directory     |

### 3️⃣ Example
```
import fs from 'fs-extra';

async function main() {
  // Ensure directory exists
  await fs.ensureDir('./data');

  // Write JSON file
  await fs.writeJson('./data/config.json', { name: "Anmol", age: 20 });

  // Read JSON file
  const config = await fs.readJson('./data/config.json');
  console.log(config);

  // Copy directory
  await fs.copy('./data', './backup');

  // Remove directory
  await fs.remove('./backup');
}

main();
✅ This code is **much cleaner** than doing the same with just Node’s `fs`.
```

## 🧠 Key Points

- `fs-extra` **supports promises** (so you can use `async/await`).
- All original `fs` methods are still available.
- Perfect for **file operations in scripts, build tools, and blockchain projects** (e.g., copying compiled contracts).

