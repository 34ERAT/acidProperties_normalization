## What is prisma

prisma is and open-source _ORM_ . it consists of the following parts

- **Prisma client:** Auto-generated and type-safe builder for nodejs and Typescript
- **Prisma migration System:** migration System
- **Prisma studio:** GUI to view and edit you database

### HOW prisma works?

#### The prisma schema

every prisma project must have a prisma schema file , The schema allows devs to define their application
contains and database define the Auto-generator

```prisma
datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

generator client {
  provider = "prisma-client-js"
}

model Post {
  id        Int     @id @default(autoincrement())
  title     String
  content   String?
  published Boolean @default(false)
  author    User?   @relation(fields: [authorId], references: [id])
  authorId  Int?
}

model User {
  id    Int     @id @default(autoincrement())
  email String  @unique
  name  String?
  posts Post[]
}
```

### 1. In this schema, you configure three things:

- **Data source:** Specifies your database connection (via an environment variable)
- **Generator:** Indicates that you want to generate Prisma Client
- **Data model:** Defines your application models

### 2. accessing your database with prisma client

#### Generation Prisma Client

- installing prisma client

```bash
npm install prisma --save-dev
npm install @prisma/client
```

Then you can run Prisma generator

```bash
npx prisma generate
```

the command above reads your schema and generates a prisma cleint file in the `nodemodules/` folder

### usingning prisma client

**import and instantiate prismaclient:**

```ts
import { PrismaClient } from "@prisma/client";

const prisma = new PrismaClient();
```

**Retrive all user recodes from database:**

```ts
// Run inside `async` function
const allUsers = await prisma.user.findMany();
```

**include the post relation on each return User object:**

```ts
// Run inside `async` function
const allUsers = await prisma.user.findMany({
  include: { posts: true },
});
```

**Filter all Post records that contain "prisma"**

```ts
// Run inside `async` function
const filteredPosts = await prisma.post.findMany({
  where: {
    OR: [
      { title: { contains: "prisma" } },
      { content: { contains: "prisma" } },
    ],
  },
});
```

**Create a new User and a new Post record in the same query**

```ts
// Run inside `async` function
const user = await prisma.user.create({
  data: {
    name: "Alice",
    email: "alice@prisma.io",
    posts: {
      create: { title: "Join us for Prisma Day 2020" },
    },
  },
});
```

**Update an existing Post record**

```ts
// Run inside `async` function
const post = await prisma.post.update({
  where: { id: 42 },
  data: { published: true },
});
```
