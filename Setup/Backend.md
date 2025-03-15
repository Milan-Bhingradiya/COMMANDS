# Setting up Node.js Backend with Express and TypeScript

## Step 1: Initialize Project

```sh
mkdir node-express-ts-backend && cd node-express-ts-backend
npm init -y
```

## Step 2: Install Dependencies

```sh
npm install express dotenv cors helmet morgan compression express-rate-limit multer jsonwebtoken bcryptjs winston
npm install --save-dev typescript ts-node @types/node @types/express @types/cors @types/helmet @types/morgan @types/compression @types/express-rate-limit @types/multer @types/jsonwebtoken @types/bcryptjs nodemon
```

## Step 3: Configure TypeScript

Create `tsconfig.json`:

```json
{
  "compilerOptions": {
    "outDir": "./dist",
    "rootDir": "./src",
    "module": "CommonJS",
    "target": "ES6",
    "strict": true,
    "esModuleInterop": true
  }
}
```

## Step 4: Create Express Server

Create `src/index.ts`:

```ts
import express from "express";
import dotenv from "dotenv";
import cors from "cors";
import helmet from "helmet";
import morgan from "morgan";
import compression from "compression";
import rateLimit from "express-rate-limit";
import multer from "multer";
import jwt from "jsonwebtoken";
import bcrypt from "bcryptjs";
import winston from "winston";

dotenv.config();

const app = express();
const PORT = process.env.PORT || 5000;

// Middleware
app.use(express.json());
app.use(cors());
app.use(helmet());
app.use(morgan("dev"));
app.use(compression());
app.use(rateLimit({ windowMs: 15 * 60 * 1000, max: 100 }));

// Logger setup
const logger = winston.createLogger({
  transports: [new winston.transports.Console()],
});

// Multer setup for file uploads
const upload = multer({ dest: "uploads/" });

app.get("/", (req, res) => {
  res.send("Hello, TypeScript with Express!");
});

// File upload route
app.post("/upload", upload.single("file"), (req, res) => {
  res.send("File uploaded successfully");
});

// Authentication Middleware
const authenticateToken = (req: any, res: any, next: any) => {
  const token = req.header("Authorization");
  if (!token) return res.status(401).send("Access Denied");

  try {
    const verified = jwt.verify(token, "secret");
    req.user = verified;
    next();
  } catch (err) {
    res.status(400).send("Invalid Token");
  }
};

// Protected route
app.get("/protected", authenticateToken, (req, res) => {
  res.send("Protected route accessed");
});

// Password Hashing Example
app.post("/register", async (req, res) => {
  const salt = await bcrypt.genSalt(10);
  const hashedPassword = await bcrypt.hash(req.body.password, salt);
  res.send({ hashedPassword });
});

app.listen(PORT, () => {
  logger.info(`Server running on port ${PORT}`);
});
```

## Step 5: Add Scripts in `package.json`

```json
"scripts": {
  "dev": "nodemon src/index.ts",
  "build": "tsc",
  "start": "node dist/index.js"
}
```

## Step 6: Run the Server

```sh
npm run dev
```

---

# Important Node.js Interview Questions with Code Examples

## 1. Explain Middleware in Express

**Answer:** Middleware functions have access to `req`, `res`, and `next()`.

```ts
app.use((req, res, next) => {
  console.log(`Request received: ${req.method} ${req.url}`);
  next();
});
```

## 2. How to Handle Async Errors in Express?

**Answer:** Use a wrapper function.

```ts
const asyncHandler = (fn: Function) => (req: any, res: any, next: any) => {
  Promise.resolve(fn(req, res, next)).catch(next);
};
```

## 3. What is CORS and How to Enable it?

**Answer:** CORS allows cross-origin requests.

```ts
import cors from "cors";
app.use(cors());
```

## 4. How to Use Environment Variables in Node.js?

**Answer:** Use `dotenv`.

```ts
import dotenv from "dotenv";
dotenv.config();
console.log(process.env.PORT);
```

## 5. How to Secure an Express App?

**Answer:** Use Helmet, Rate Limiting, and CORS.

```ts
import helmet from "helmet";
import rateLimit from "express-rate-limit";
app.use(helmet());
app.use(rateLimit({ windowMs: 15 * 60 * 1000, max: 100 }));
```

## 6. Explain JWT Authentication in Node.js

**Answer:** JWT is used for authentication.

```ts
import jwt from "jsonwebtoken";
const token = jwt.sign({ userId: "123" }, "secret", { expiresIn: "1h" });
```

## 7. How to Handle File Uploads in Express?

**Answer:** Use `multer`.

```ts
import multer from "multer";
const upload = multer({ dest: "uploads/" });
app.post("/upload", upload.single("file"), (req, res) => {
  res.send("File uploaded");
});
```

## 8. How to Optimize Performance in Express?

**Answer:** Use compression and caching.

```ts
import compression from "compression";
app.use(compression());
```

## 9. How to Handle Logging in Node.js?

**Answer:** Use `winston`.

```ts
import winston from "winston";
const logger = winston.createLogger({
  transports: [new winston.transports.Console()],
});
logger.info("Logging in Node.js");
```

## 10. How to Connect Node.js with PostgreSQL?

**Answer:** Use `pg`.

```ts
import { Pool } from "pg";
const pool = new Pool({
  user: "dbuser",
  host: "localhost",
  database: "testdb",
  password: "password",
  port: 5432,
});
```

---

This document covers setting up a Node.js backend with TypeScript and important backend interview questions.
