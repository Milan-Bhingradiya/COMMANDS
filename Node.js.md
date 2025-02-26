# Node.js Complete Guide

## Installing Node.js
```sh
# Check if Node.js is installed
node -v

# Install Node.js via package manager
# macOS (Homebrew)
brew install node

# Ubuntu/Debian
sudo apt install nodejs npm

# Windows (Using Chocolatey)
choco install nodejs
```

## Initializing a Node.js Project
```sh
npm init -y  # Creates package.json
```

## Running a Node.js File
```sh
node app.js
```

## Importing Modules (ES Modules - Supported in Node.js 12+)
```js
import fs from 'fs';
import path from 'path';
import { fileURLToPath } from 'url';
```
* To use ES Modules, add `"type": "module"` in `package.json` or use `.mjs` file extension.

## Installing Dependencies
```sh
npm install express  # Install a package
npm install --save-dev nodemon  # Install as a dev dependency
```

## Managing Dependencies
```sh
npm list  # List installed packages
npm outdated  # Check outdated packages
npm update  # Update all packages
```

## Creating a Simple HTTP Server
```js
import http from 'http';
const server = http.createServer((req, res) => {
    res.writeHead(200, { 'Content-Type': 'text/plain' });
    res.end('Hello, World!');
});
server.listen(3000, () => console.log('Server running on port 3000'));
```

## Using Express.js
```sh
npm install express
```
```js
import express from 'express';
const app = express();
app.get('/', (req, res) => res.send('Hello, Express!'));
app.listen(3000, () => console.log('Server running on port 3000'));
```

## Environment Variables
```sh
# Using dotenv
npm install dotenv
```
```js
import dotenv from 'dotenv';
dotenv.config();
console.log(process.env.PORT);
```

## Running Scripts
```sh
node index.js  # Run script
npm run start  # Run npm script
```

## Debugging
```sh
node --inspect-brk app.js
```

## Working with File System (fs module)
```js
import fs from 'fs';
fs.writeFileSync('test.txt', 'Hello Node.js');
console.log(fs.readFileSync('test.txt', 'utf8'));
```

## Asynchronous Programming
```js
import fs from 'fs/promises';
async function readFile() {
    const data = await fs.readFile('test.txt', 'utf8');
    console.log(data);
}
readFile();
```

## Handling Errors
```js
try {
    throw new Error('Something went wrong');
} catch (error) {
    console.error(error.message);
}
```

## Exiting a Process
```js
process.exit(1);
```

This guide covers essential Node.js concepts and commands.

