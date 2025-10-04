# Node.js Modules and Express Setup - Classes 11-14

## Classes 11-13: Node.js Modules

### 1. Module Wrapper Function

Node.js wraps all modules in a wrapper function that provides:

- `exports` - Object to export module functionality
- `module` - Reference to current module
- `require` - Function to import modules
- `__filename` - Absolute path of current module file
- `__dirname` - Directory name of current module

### 2. Custom Modules

Creating your own modules for reusable code.

### 3. Built-in Modules

#### OS Module

```js
const os = require('os');

os.cpus()        // Get CPU information
os.freemem()     // Get free memory
os.totalmem()    // Get total memory
```

#### Path Module

```js
const path = require('path');

path.resolve()   // Resolve absolute path
path.join()      // Join path segments
path.parse()     // Parse path into components
```

#### EventEmitter Module

```js
const EventEmitter = require('events');

const emitter = new EventEmitter();

emitter.on('event_name', callback);    // Listen for events
emitter.emit('event_name');           // Emit events
```

#### File System Module

```js
const fs = require('fs');

fs.readFile()      // Asynchronous file reading
fs.readFileSync()  // Synchronous file reading
fs.writeFileSync() // Synchronous file writing
```

#### HTTP Module

```js
const http = require('http');

http.createServer()  // Create HTTP server
server.listen()      // Start listening on port
```

### 4. HTTP as EventEmitter

HTTP module extends EventEmitter, allowing event-driven programming.

### 5. Express Framework

Express is built on top of Node.js HTTP module.

### 6. Node.js Frameworks

- **Express** - Most popular web framework
- **Nest.js** - Enterprise-grade framework

---

## Class 14: Express Setup and Project Structure

### Team Structure

- **Business** → Product Manager (PM)
- **Engineering** → Senior Engineer / Team Lead / Software Engineer
- **Engineering Knowledge** → Intern, Junior Engineer, Software Engineer
- **Programming** → University
- **Programming Knowledge** → University

### Express Setup Steps

1. **Initialize Project**

   ```bash
   npm init -y  # Create package.json file
   ```

2. **Install Express**

   ```bash
   npm install express
   ```

3. **Basic Server Setup**

   ```js
   const express = require('express');
   const app = express();
   
   app.get('/', (req, res) => {
       res.send('Hello World!');
   });
   
   app.listen(3000, () => {
       console.log('Server running on port 3000');
   });
   ```

4. **Development Setup**

   ```bash
   npm install -g nodemon  # Install globally
   npm run start          # Start development server
   ```

5. **Access Application**
   - Open browser and navigate to `localhost:3000`

### CRUD Operations Task

Create a complete CRUD API for posts:

1. **POST** `/posts` - Create new post
2. **GET** `/posts` - Get all posts
3. **GET** `/posts/:id` - Get single post
4. **DELETE** `/posts/:id` - Delete single post
5. **PUT** `/posts/:id` - Update single post
