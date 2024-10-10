# KNT-Node

This is a Authentication service using Node.js, Express, and TypeScript.

## Project Structure
```
project-root/
├── dist/                 # Compiled code directory
├── node_modules/         # Dependencies directory
├── prisma/               # Prisma configuration and migrations
├── src/                  # TypeScript source code
│   ├── config/           # Passport and session configuration
│   ├── controllers/      # Business logic handlers
│   ├── middleware/       # Express middleware
│   ├── models/           # Model definitions
│   ├── routes/           # Route definitions
│   ├── services/         # Services
│   ├── utils/            # Utilities
│   ├── views/            # EJS templates
│   └── app.ts            # Application entry point
├── .env                  # Environment variables file
├── .gitignore            # Git ignore configuration
├── package.json          # npm and dependencies configuration
├── package-lock.json     # Lock file for npm dependencies
└── tsconfig.json         # TypeScript configuration
```
## Project Setup Steps

1. Initialize the project:

npm init -y

2. Install TypeScript and necessary dependencies:

npm install

3. Configure TypeScript (create tsconfig.json):

npx tsc --init

4. Create the directory structure as described above.

5. Install and configure Prisma:

npm install prisma --save-dev
npx prisma init

7. Configure scripts in package.json:
```
"scripts": {
    "build": "tsc",
    "start": "node dist/app.js",
    "dev": "nodemon --exec ts-node src/app.ts",
    "watch": "tsc -w"
}
```
8. Set up environment configuration in .env file.
9. Run Prisma migrations and generate Prisma client after adding contents for the schema.prisma file.

npx prisma migrate dev
npx prisma generate

10. Running the project 

Development mode: npm run dev
Build: npm run build
Run production version: npm start

For using the raw query:

1. Add the typedSql preview feature flag to your schema.prisma file:
```
generator client {
  provider = "prisma-client-js"
  previewFeatures = ["typedSql"]
}
```

2. Create a sql directory inside your prisma directory. This is where you'll write your SQL queries.

3. Create a new .sql file in your prisma/sql directory.

mkdir -p prisma/sql

4. Write your SQL queries in your new .sql file

5. Generate Prisma Client with the sql flag to ensure TypeScript functions and types for your SQL queries are created:

prisma generate --sql

6. Now you can import and use your SQL queries in your TypeScript code:

```
import { PrismaClient } from '@prisma/client'
import { getUsersWithPosts } from '@prisma/client/sql'

const prisma = new PrismaClient()

const usersWithPostCounts = await prisma.$queryRawTyped(getUsersWithPosts())
console.log(usersWithPostCounts)
```