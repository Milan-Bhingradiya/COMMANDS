# Prisma Complete Guide

## Introduction
Prisma is a next-generation ORM (Object-Relational Mapping) for Node.js and TypeScript. It provides a type-safe database toolkit for working with SQL databases.

---

## Installation

### Install Prisma CLI
```sh
npm install prisma --save-dev
```

### Initialize Prisma
```sh
npx prisma init
```
This creates a `prisma` folder with a `schema.prisma` file.

### Install Database Client (Example: PostgreSQL)
```sh
npm install @prisma/client
```

---

## Configuring the Database
Edit `.env` file to set the database URL:
```env
DATABASE_URL="postgresql://USER:PASSWORD@localhost:5432/mydb"
```

Update `schema.prisma`:
```prisma
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}
```

---

## Defining Models
Modify `schema.prisma` to define tables:
```prisma
model User {
  id    Int     @id @default(autoincrement())
  name  String
  email String  @unique
  posts Post[]
}

model Post {
  id       Int    @id @default(autoincrement())
  title    String
  content  String?
  userId   Int
  user     User   @relation(fields: [userId], references: [id])
}
```

---

## Migrations
After defining models, generate and apply migrations:
```sh
npx prisma migrate dev --name init
```

Check the database structure:
```sh
npx prisma studio
```

---

## Using Prisma Client

### Import Prisma Client in Code
```ts
import { PrismaClient } from '@prisma/client';
const prisma = new PrismaClient();
```

### Create a User
```ts
const newUser = await prisma.user.create({
  data: { name: "John", email: "john@example.com" },
});
```

### Fetch Users
```ts
const users = await prisma.user.findMany();
```

### Update a User
```ts
const updatedUser = await prisma.user.update({
  where: { id: 1 },
  data: { name: "John Doe" },
});
```

### Delete a User
```ts
await prisma.user.delete({ where: { id: 1 } });
```

---

## Seeding Database
Create `prisma/seed.ts`:
```ts
import { PrismaClient } from '@prisma/client';
const prisma = new PrismaClient();

async function main() {
  await prisma.user.create({ data: { name: "Alice", email: "alice@example.com" } });
}

main().catch(console.error).finally(() => prisma.$disconnect());
```
Run the seeding script:
```sh
npx prisma db seed
```

---

## Deployment Considerations
- Use `prisma migrate deploy` for production.
- Ensure `DATABASE_URL` is correctly set in the production environment.
- Use `prisma generate` if using Prisma Client in a deployed app.

---

## Additional Features
- **Prisma Middleware**: Run logic before/after database queries.
- **Raw SQL Queries**: `prisma.$queryRaw` for executing raw SQL.
- **Database Introspection**: `npx prisma db pull` to reflect existing database structure.

---

This guide provides a structured approach to using Prisma efficiently in projects. 🚀

