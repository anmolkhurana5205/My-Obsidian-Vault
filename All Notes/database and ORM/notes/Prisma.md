Prisma is a **modern database ORM** (Object Relational Mapper) for Node.js and TypeScript.

But unlike old ORMs, Prisma is:
1. Type-safe
2. Auto-complete friendly
3. Migration-driven
4. Extremely fast
Prisma acts as a **bridge** between your Node.js backend and your database (PostgreSQL, MySQL, MongoDB, SQLite, etc.).


### Prisma has 3 main parts

1. **Prisma Client**
Auto-generated TypeScript client used in your code.
Example:
```
const user = await prisma.user.findMany();
```
Prisma creates a typed API for every model in your schema.

2. **Prisma Migrate**
Handles migration files and schema changes.
Example:
```
npx prisma migrate dev --name add_user_table
```
It creates SQL migration files automatically.

3. **Prisma Studio**
Beautiful GUI to view and edit database data.
Run it with:
```
npx prisma studio
```

### Prisma Project Structure
Typical files:
```
prisma/
  schema.prisma   <-- main file where models live (User, Post, etc.)
node_modules/
```

### schema.prisma File
This is where you define tables (models).
Example:
```
model User {
  id        Int     @id @default(autoincrement())
  email     String  @unique
  name      String?
  password  String
  createdAt DateTime @default(now())
}
```
When you save this file, Prisma generates TypeScript types.


### How Prisma Works Internally
Step 1 — You define models in `schema.prisma`.
Step 2 — Run migrations → creates real tables in DB.
Step 3 — Prisma generates a typed **Prisma Client**.
Step 4 — You import Prisma Client and interact with DB.

### Prisma Client Example
```
import { PrismaClient } from '@prisma/client';
const prisma = new PrismaClient();

async function main() {
  const newUser = await prisma.user.create({
    data: {
      email: "test@gmail.com",
      name: "Anmol"
    }
  });

  const users = await prisma.user.findMany();
  console.log(users);
}

main();
```


### Prisma Query Examples (Most Used)
Create
```
await prisma.user.create({
  data: {
    email: "hello@gmail.com",
    password: "123456"
  }
})
```

Read
```
await prisma.user.findUnique({
  where: { email: "hello@gmail.com" }
})
```

Update
```
await prisma.user.update({
  where: { id: 1 },
  data: { name: "updated name" }
})
```

Delete
```
await prisma.user.delete({
  where: { id: 1 }
})
```


### Relations
Prisma makes relations very easy.
Example:
```
model User {
  id    Int    @id @default(autoincrement())
  posts Post[]
}

model Post {
  id      Int @id @default(autoincrement())
  title   String
  userId  Int
  user    User @relation(fields: [userId], references: [id])
}
```

Fetching relations:
```
const user = await prisma.user.findUnique({
  where: { id: 1 },
  include: { posts: true },
});
```


### How Prisma Works With Next.js (Most Used Combo)
In Next.js apps:
- put `schema.prisma` in `/prisma`
- create a `prismadb.ts` file:
```
import { PrismaClient } from "@prisma/client";

const prisma = global.prisma || new PrismaClient();

if (process.env.NODE_ENV !== "production") global.prisma = prisma;

export default prisma;
```

Then import anywhere:
```
import prisma from "@/lib/prismadb";

const users = await prisma.user.findMany();
```

### Installing Prisma
```
npm install prisma --save-dev
npm install @prisma/client
npx prisma init
```
This creates the `prisma/` folder and schema.

### Opening Prisma Studio
```
npx prisma studio
```
GUI opens in the browser.


