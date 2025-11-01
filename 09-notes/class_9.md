# JavaScript Runtime Environment Components

## 1. Mother Process & Child Process
- **Mother Process**: The main Node.js process that manages the entire application
- **Child Process**: Spawned processes created by the mother process for parallel execution
- Used for CPU-intensive tasks to avoid blocking the main thread

## 2. setTimeout API
- Browser/Node.js API for scheduling function execution after a delay
- Not part of JavaScript engine - provided by the runtime environment
- Example: `setTimeout(() => console.log("Hello"), 1000)`

## 3. Browser
- Provides the runtime environment for JavaScript in web applications
- Includes Web APIs, DOM manipulation, and other browser-specific features
- Manages the JavaScript engine execution

## 4. JS Engine
- Core component that parses, compiles, and executes JavaScript code
- Examples: V8 (Chrome/Node.js), SpiderMonkey (Firefox), Chakra (Edge)
- Handles memory management, garbage collection, and code optimization

## 5. Browser Resources
- Web APIs provided by the browser (DOM, Fetch, Geolocation, etc.)
- Hardware access (camera, microphone, storage)
- Network capabilities and file system access

## 6. APIs
- Application Programming Interfaces that provide functionality beyond core JavaScript
- Web APIs in browsers, Node.js APIs in server environment
- Examples: File System API, HTTP API, Database APIs

## 7. Thread Pool
- Collection of worker threads managed by the runtime
- Handles I/O operations and other blocking tasks
- Allows JavaScript to remain single-threaded while leveraging multi-threading for system operations

## 8. Heap
- Memory area where objects and variables are stored
- Managed by the JavaScript engine's garbage collector
- Stores dynamically allocated memory for objects, arrays, and closures

## 9. Microtask Queue & Callback Queue
- **Microtask Queue**: High-priority queue for promises, process.nextTick()
- **Callback Queue**: Regular queue for setTimeout, setInterval, I/O callbacks
- Microtasks are processed before callbacks in the event loop

## 10. Event Loop
- Core mechanism that manages the execution of asynchronous code
- Continuously checks the call stack and queues
- Ensures non-blocking behavior by processing callbacks when the call stack is empty

## 11. Decision: JavaScript is Single-threaded but Still Fast
- **Single-threaded**: Only one piece of code executes at a time in the main thread
- **Fast execution**: Due to:
  - Efficient V8 engine with JIT compilation
  - Non-blocking I/O operations
  - Event-driven architecture
  - Optimized garbage collection
  - Asynchronous processing with callbacks and promises
