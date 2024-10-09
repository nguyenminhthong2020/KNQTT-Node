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