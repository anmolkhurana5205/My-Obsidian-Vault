ORM = Object Relational Mapping

It is a technique (or tool/library) that lets you interact with your database **using objects and code**, instead of writing raw SQL queries manually.

Without ORM (Raw SQL):
```
SELECT * FROM users WHERE id = 1;
```

With ORM (JavaScript example – Prisma/Sequelize):
```
const user = await prisma.user.findUnique({ where: { id: 1 } });
```
ORM automatically **maps your database tables to programming-language objects**.


### Why ORM Exists?
Because writing SQL manually for everything is:
- repetitive
- error-prone
- not type-safe
- difficult to scale
- difficult to maintain in big projects

ORM makes interacting with the DB:
easier  
- safer
- easier
- faster to develop
- predictable
- readable

### How ORM Works Internally
Imagine your database has a table:

| id  | name | email |
| --- | ---- | ----- |
ORM converts this table into a class:
```
class User {
  id;
  name;
  email;
}
```

When you call:
```
User.create({ name: "Anmol", email: "xyz@gmail.com" })
```

ORM automatically generates SQL:
```
INSERT INTO users (name, email) VALUES ('Anmol', 'xyz@gmail.com');
```
And sends it to the database.

### Features of ORM
1. Model creation
	You define "models", which represent tables.
2. CRUD operations
	Create, Read, Update, Delete without writing SQL.
3. Migrations
	ORM can automatically update database structure when your models change.
4. Schema validation & type-safety
	Modern ORMs like Prisma give compile-time errors if your query is wrong.
5. Relationships
	One-to-One, One-to-Many, Many-to-Many handled with simple objects.
6. Query building
	ORM converts methods into SQL.
7. Connection pooling
	ORM manages database connections.
8. Security
	Protects against SQL injection automatically.

### Types of ORMs
#### 1. **Active Record ORM**
- Model = table
- Methods inside the model perform DB operations

Examples:
- **Sequelize (Node.js)**
- **Rails ActiveRecord**
- **Laravel Eloquent**

Example:
```
User.findAll()
```

#### 2. **Data Mapper ORM**
- Models are plain objects
- Separate layer handles DB queries

Examples:
- **Prisma (Node.js)**
- **TypeORM (semi-mapper)**

Example:
```
prisma.user.findMany()
```

### ORM Workflow
- Define models
- Run migrations
- ORM creates tables
- Use models in code
- ORM converts your code into SQL
- DB returns results
- ORM converts results into objects

### Popular ORMs by Language
#### JavaScript / Node.js
- Prisma ⭐ (most modern)
- Sequelize
- TypeORM
- Mongoose (MongoDB only)
#### Python
- SQLAlchemy
- Django ORM
#### Java
-  Hibernate (JPA)
#### PHP
- Laravel Eloquent

### Example (Node.js + Prisma)

#### Schema
```
model User {
  id    Int    @id @default(autoincrement())
  name  String
  email String @unique
}
```


#### Query
```
const user = await prisma.user.create({
  data: { name: "Spidy", email: "spidy@gmail.com" }
});
```

#### SQL Generated (internally)
```
INSERT INTO User (name, email) VALUES ('Spidy', 'spidy@gmail.com');
```

