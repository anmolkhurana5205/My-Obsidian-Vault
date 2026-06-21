#typescript #nodejs

## Setup

```bash
npm install --save-dev @types/node ts-node typescript
```

## tsconfig for Node

```json
{
  "compilerOptions": {
    "target": "ES2020",
    "module": "commonjs",
    "outDir": "dist",
    "rootDir": "src",
    "strict": true,
    "esModuleInterop": true
  }
}
```

## Using Node built-ins

```typescript
import * as fs from "fs";
import * as path from "path";
import * as http from "http";

const content = fs.readFileSync(path.join(__dirname, "data.txt"), "utf8");
```

## Express with TypeScript

```bash
npm install express
npm install --save-dev @types/express
```

```typescript
import express, { Request, Response } from "express";

const app = express();

app.get("/users/:id", (req: Request, res: Response) => {
  const { id } = req.params;
  res.json({ id, name: "Alice" });
});

app.listen(3000, () => console.log("Server running"));
```

---
