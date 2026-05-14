# 📘 Backend Interview Questions (3–5 Years Experience)

A structured collection of **Node.js, Express.js, Database, Security, and System Design questions** for backend interviews.

---

## 🟢 Beginner Level (Core Basics)

### Node.js Fundamentals
- What is Node.js, and how does it work?
- What is the difference between Node.js and JavaScript?
- What kind of API functions are supported by Node.js?
- Is Node.js single-threaded?
- What are the advantages of Node.js?
- What are the main disadvantages of Node.js?

### Modules & Package Management
- What is a module in Node.js?
- What is the difference between CommonJS and ES Modules?
- How do you import a module in Node.js?
- What is `package.json`, and why is it essential?
- What is `npm`, and what are its advantages?
- what is Package.lock.json?
- Diff between carat and tilde?

### Express.js Basics
- What is Express.js, and why is it commonly used with Node.js?
- What is middleware in Express.js?
- How do you handle routing in Express?
- What is the difference between `req.params`, `req.query`, and `req.body`?
- How do you send a JSON response from an Express route?
- How do you handle errors in Express?

### Interactive Environment
- What is REPL in Node.js, and how does it work?

---

## 🟡 Intermediate Level (Asynchronous & Architecture)

### Event Loop & Concurrency
- What is event-driven programming in Node.js?
- What is the Event Loop in Node.js, and what are its phases?
- How does the event loop manage asynchronous operations?
- How does Node.js handle concurrency despite being single-threaded?
- How does Node.js handles CPU-intensive task?

### Asynchronous Programming
- What are callbacks in Node.js?
- What is difference between Synchronous and Async Programming in Node.js?
- What is "callback hell," and how can it be avoided? (3 methods)
- What are Promises, and how do they improve async handling?
- How does `async/await` work?
- What is an error-first callback pattern?

### Streams & Buffers
- What are streams in Node.js, and what are their types?
- How do streams handle large files (backpressure)?
- What is a buffer in Node.js?
- Difference between `fs.readFile()` and `fs.createReadStream()`.

### Middleware & APIs
- What is body-parser in Node.js?
- What is CORS, and why is it important?
- How do you manage authentication & authorization in Node.js?
- How do you protect routes in Express.js?
- How to handle file uploads in Node.js?

### Database Handling
- How do you connect Node.js to a database (MongoDB/MySQL/Postgres)?
- What is connection pooling, and why is it needed?
- How do you handle transactions in Node.js?

---

## 🔴 Advanced Level (Performance, Security, System Design)

### Core Concepts & System Architecture
- Explain the event-driven architecture of Node.js.
- Explain the difference between `process.nextTick()` and `setImmediate()`. Which runs first?
- What happens when Node.js encounters an uncaught exception?
- What exactly happens when we execute `require('module')`?
- What is Libuv, and what role does it play in Node.js?
- What’s the difference between Worker Threads and Child Processes?
- What is the difference between `spawn()` and `fork()`?
- What is a cluster in Node.js, and why is it used?
- How do you scale Node.js horizontally?

### Memory & Performance
- How do you detect and fix memory leaks in Node.js?
- What is the significance of `--max-old-space-size` flag?
- Explain V8 hidden classes and their performance impact.
- How can you implement a graceful shutdown in Node.js?
- What are best practices for performance optimization in Node.js?

### Security
- What are the most common security vulnerabilities in Node.js, and how do you prevent them?
- How Do you Prevent SQL Injection?
- How Do you protect from CSRF and XSS Attack?
- What is prototype pollution, and how can you prevent it?
- How do you implement rate limiting & brute-force protection in Express?
- How do you securely store API keys and secrets in Node.js?
- How do you handle JWT authentication & refresh tokens?

### Advanced Async Handling
- Compare callbacks vs promises vs async/await.
- What happens when a Promise is rejected without a catch handler?
- What is `Promise.all()`, and when can it cause issues?
- How does async/await handle errors differently from Promises?

### Modules & Advanced APIs
- What are ESM modules in Node.js? How do they differ from CommonJS?
- Explain the crypto module in Node.js.
- Explain the timers module (`setTimeout`, `setImmediate`, `process.nextTick`).
- Explain the tls module in Node.js.
- Explain the vm module and its use cases.

### Express.js & Authentication
- What is the passport module in Node.js?
- How to manage sessions in Node.js?
- How to implement JWT-based authentication in Express?

### Deployment & Scaling
- What is clustering in Node.js, and its limitations?
- How do you optimize a Node.js app for production?
- How do you deploy a Node.js app (steps & best practices)?
- What is process management, and which tools (PM2, Docker, Kubernetes) are used?
- How does CI/CD help in Node.js projects?
- How do you manage environment variables
- How do you implement structured logging in Node.js?
- What Monitoring & alerting strategies do you use in production (Grafana, Promothus and loki)?

### Real-Time & Microservices
- What are WebSockets, and how are they implemented in Node.js?
- What is the difference between WebSockets and Socket.IO?
- Explain microservices architecture and how Node.js supports it.
- What are the differences between RESTful APIs and GraphQL in Node.js?
- How do you handle real-time data processing in Node.js?

---

## 🔧 Related Backend Technologies

### MongoDB
- What is `$unwind`, `$facet`, `$merge`, `$bucket` in Aggregation?
- What is the purpose of the `$size` operator?
- Difference between `$in` and `$nin`.
- Advantage of WiredTiger storage engine.

### SQL
- Which clause is used to filter records in SQL?

### Git
- What does `.gitignore` do?
- How do you change the last commit message?
- What is the purpose of Git?

### AWS
- What is AWS Elastic Beanstalk, and its benefits?
- What is S3 versioning?
- What are lifecycle policies in S3?
- Differences between S3 Standard, Glacier, and Glacier Deep Archive.
- How does Intelligent-Tiering optimize storage?
- What is AWS KMS, and how is it used?

---------------------------------------------------------------------------------------------

###  What is Node.js, and how does it work?

Node.js is a JavaScript runtime environment built on the Chrome V8 Engine that allows you to run JavaScript outside the browser, mainly on the server.

#### How Node.js Works (Core Concept)

Node.js follows an event-driven, non-blocking I/O model, which makes it highly efficient and scalable.

1. Single Threaded
 - Node.js uses a single main thread (event loop)
 - It does not create a new thread per request like traditional servers
 - 👉 But it handles concurrency using async operations.

2. Event Loop (Heart of Node.js)
  - The event loop continuously checks:
  - Call stack (synchronous code)
  - Callback queue (async results)

    👉 Flow:
   1. Request comes in
   2. If it’s non-blocking (I/O) → send to system (libuv / OS)
   3. Continue executing next code
   4. When result is ready → callback pushed to queue
   5. Event loop executes it

3. Non-Blocking I/O
   1. Instead of waiting for operations like:
   2. DB calls
   3. File system
   4. API requests
   5. Node.js delegates them and continues execution.

#### Example
```ts
const fs = require('fs');

console.log("Start");

fs.readFile('file.txt', 'utf-8', (err, data) => {
  if (err) throw err;
  console.log("File Content:", data);
});

console.log("End");
```

#### Why Node.js is Fast

- Built on V8 engine (compiles JS to machine code)
- Non-blocking architecture
- No thread overhead (lightweight)

#### When NOT to Use Node.js (Important Insight)

 - CPU-heavy tasks (image processing, heavy calculations)
Because single thread gets blocked

#### Solution 
- Use Worker Threads


### Difference between Node.js and JavaScript
```
JavaScript is the core programming language, while Node.js is a runtime environment that allows us to execute JavaScript on the server. The key difference is the environment and APIs—browser JavaScript works with DOM APIs, whereas Node.js provides system-level APIs like file handling, networking, and process control.
```

#### Where They Run
JavaScript-
- Runs in browsers like Chrome, Firefox
- Used for frontend (UI, DOM manipulation)

Node.js-
- Runs on server (backend)
- Used for APIs, microservices, real-time apps

### What kind of API functions are supported by Node.js?

Node.js provides built-in modules (APIs) that allow you to interact with the system, network, and processes.

```
Node.js provides a rich set of built-in APIs like file system, HTTP, streams, events, and process APIs. These are mostly asynchronous and event-driven, enabling efficient handling of I/O operations and making Node.js suitable for scalable backend systems.
```

1. File System: Used to read/write files
2. HTTP & Network APIs: Used to create servers and handle requests
3. OS APIs: Provides system-level information
4. Path APIs: Used to handle file paths safely
5. Process APIs: Gives info/control over running Node.js process


### Is Node.js single-threaded?

Node.js is single-threaded for executing JavaScript but uses asynchronous, non-blocking I/O and background threads to achieve concurrency.

### What are the advantages of Node.js?

```
Node.js offers high performance due to the V8 engine, and its non-blocking, event-driven architecture allows it to handle a large number of concurrent requests efficiently. It also provides a rich ecosystem via npm, supports real-time and streaming applications.
```

1. High Performance (V8 Engine)
2. Non-Blocking I/O (Async by Default)
3. Event-Driven Architecture
4. Rich Ecosystem (NPM)
5. Cross-Platform

### What are the main disadvantages of Node.js?

```
Node.js has some limitations like being unsuitable for CPU-intensive tasks due to its single-threaded nature, potential callback complexity, and challenges with async error handling. It also heavily relies on npm packages, which can introduce security or maintenance risks. However, most of these can be mitigated using worker threads, async/await, proper architecture, and TypeScript.
```

### What is a module in Node.js?

A module helps you split your code into smaller, maintainable, and reusable parts

Types of Modules
1. Core Modules (Built-in)
2. Local Modules (Custom)
3. Third-Party Modules

Module System in Node.js

1. CommonJS (Default)
2. ES Modules (Modern)

### What is the difference between CommonJS and ES Modules?

#### CommonJS

- Syntax: require / module.exports
- Loading: Synchronous
- Imports: Dynamic
- Default in Node
- this: {}
- Non strict mode

#### ES Modules

- Syntax: import / export
- Loading : Asynchronous
- Imports: Static (top-level)
- Default in Angualr/ React
- this: undefined
- Strict Mode

```
CommonJS and ES Modules are two module systems in Node.js. CommonJS uses require and module.exports with synchronous loading, while ES Modules use import/export with asynchronous and static loading. ES Modules are the modern standard and support features like tree shaking and better tooling, whereas CommonJS is widely used in older Node.js applications.
```

##### Which one should we use?

For new projects, ES Modules are preferred due to standardization and better tooling, but CommonJS is still widely used in existing Node.js ecosystems.

### How do you import a module in Node.js?

1. There are two main ways, depending on the module system:

- Using CommonJS (require)
- Using ES Modules (import)

### What is package.json, and why is it essential?

Package.json is a metadata and configuration file for a Node.js project.

 It Defines

1. Project details
2. Dependencies
3. Scripts
4. Runtime behavior
5. Define Module Type

```
package.json is a core configuration file in a Node.js project that contains metadata, dependency definitions, scripts, and environment settings. It is essential because it enables dependency management, project configuration, and reproducibility across different environments.
```

### What is npm, and what are its advantages?

```
npm is the default package manager for Node.js that allows us to install, manage, and version dependencies. It provides access to a vast ecosystem of reusable libraries, simplifies dependency management
```

#### Advantages of npm

1. Massive Ecosystem
2. Easy Dependency Management
3. Script Automation

### What is package-lock.json

```
package-lock.json is an automatically generated file created by npm that locks the exact versions of all dependencies (including sub-dependencies) used in your project.
```

### Difference between ^ (caret) and ~ (tilde)

1. Caret (^) — More Flexible

👉 Allows updates to:

- Minor version
- Patch version

2. Tilde (~) — More Strict

👉 Allows updates to:

- Only Patch version

### What is Express.js, and why is it commonly used with Node.js?

Express.js is a minimal and flexible web framework for Node.js that helps you build web servers and APIs easily.

```
In my projects, I use Express.js to build REST APIs because it simplifies routing, middleware handling, and request/response processing. It helps structure the application cleanly and speeds up development compared to using the native Node.js HTTP module
```
- Routing Made Easy
- Middleware Support
- Request & Response Handling

### What is Middleware in Express.js?

In Express.js, middleware is a function that runs between the incoming request and the final response.

👉 In simple terms:

“Middleware is a function that has access to req, res, and next, and can modify the request/response or pass control to the next function.”

👉 Flow:

- Request comes
- Middleware runs
- Calls next()
- Route handler executes

Types of Middleware

- Application-Level Middleware

```ts
app.use((req, res, next) => {
  console.log('Global middleware');
  next();
});
```

- Route-Level Middleware
``` ts
app.get('/admin', authMiddleware, (req, res) => {
  res.send('Admin Panel');
});
```
- Built-in Middleware
```ts
app.use(express.json());
```
- Third-Party Middleware: Installed via npm

In my projects, I use middleware extensively for authentication, request validation, logging, and centralized error handling. It helps keep the code modular and separates concerns effectively

### How do you handle routing in Express?

In Express.js, routing means defining how your server responds to different HTTP requests (URL + method).

####  1. Basic Routing

```ts
const express = require('express');
const app = express();

app.get('/users', (req, res) => {
  res.send('Get all users');
});
```

#### 2. Using Express Router
```ts
const express = require('express');
const router = express.Router();

router.get('/', (req, res) => {
  res.send('All users');
});
module.exports = router;

```
“In my projects, I handle routing using Express Router to modularize routes by feature."

### Difference between req.params, req.query, and req.body

All three are used to get data from the client, but from different parts of the request.

#### 1) req.params -> URL Path Parameters

```ts
app.get('/users/:id', (req, res) => {
  console.log(req.params.id);
});
```

✔ Use case:

- Get resource by ID
- RESTful APIs (/users/:id)

#### 2) req.query -> Query String Parameters
- Used for optional data in URL
```ts
app.get('/users', (req, res) => {
  console.log(req.query.page);
});
```

✔ Use case:

- Filtering
- Pagination
- Sorting

#### 3. req.body → Request Body Data

Used to get data sent in request payload

```ts
app.post('/users', (req, res) => {
  console.log(req.body);
});
```

✔ Use case:

- Create/update data (POST, PUT)
- Form submissions
- JSON payloads

### How do you send a JSON response from an Express route?

response.send:- Can send any type of response (string, HTML, JSON)
response.json:- Specifically sends JSON

### How do you handle errors in Express?

In Express.js, error handling is typically done using:

- Try/catch (for sync/async code)
- Error-handling middleware (centralized)

```
Error handling in Express is done using try/catch for synchronous code and passing errors to centralized error-handling middleware using next(err). The middleware processes all errors in one place and returns structured responses with proper status codes.
```

### What is REPL in Node.js, and how does it work?

It is an interactive shell provided by Node.js where you can write and execute JavaScript code line by line.

#### How REPL Works

It follows a simple cycle:

- Read → Takes user input
- Eval → Executes the code using the Chrome V8 Engine
- Print → Displays the result
- Loop → Waits for next input

### What is Event-Driven Programming in Node.js?

Event-driven programming is a pattern where the flow of the application is controlled by events (like user actions, I/O completion, timers, etc.).

```
Event-driven programming in Node.js is a model where the execution flow is based on events and their handlers. Node.js uses an event loop and EventEmitter to listen for events and execute callbacks asynchronously, making it efficient for handling multiple concurrent operations.
```

👉 In Node.js:

“The system listens for events and executes corresponding callbacks when those events occur.”

How it works in Node.js

Node.js uses:

- Event Loop
- Event Emitter
- Non-blocking I/O

👉 Flow:

- Event occurs (e.g., HTTP request, file read)
- Event is emitted
- Listener (callback) handles it

Why Node.js Uses Event-Driven Model

👉 Because it is:

- Non-blocking
- Asynchronous
- Efficient for I/O-heavy operations

### What is the Event Loop in Node.js, and what are its phases?

The event loop in Node.js is a mechanism that allows asynchronous operations to be handled in a single-threaded environment. It processes callbacks in multiple phases like timers, poll, and check. Microtasks like promises and process.nextTick are executed before moving to the next phase.

#### Event Loop Phases

##### 1. Timers Phase

 - setTimeout
 - SetInterval

##### 2. Pending Callbacks Phase

👉 Executes:

- Some system-level callbacks
- Deferred I/O errors

#### 3. Idle / Prepare Phase

👉 Internal use (not important for interviews)

##### 4. Poll Phase (Most Important 🔥)

👉 Handles:

Incoming I/O events (file, DB, network)

##### 5. Check Phase

👉 Executes:

setImmediate() callbacks

##### 6. Close Callbacks Phase

👉 Executes:

socket.on('close', ...)
Cleanup callbacks

###### Timers → Pending → Idle → Poll → Check → Close

#### Special Queues

##### Microtasks (Higher Priority)

Executed before next phase

process.nextTick()
Promises (.then, catch)

### How does the event loop manage asynchronous operations?

```
The event loop manages asynchronous operations by delegating them to the system or thread pool and executing their callbacks once completed. It ensures non-blocking behavior by processing tasks from different queues when the call stack is empty.
```

1. Synchronous code runs first

2. Async task is offloaded
- Operations like:
- File system
- Network calls
- Timers are delegated to the system (libuv/OS)

3. Callback is queued when ready
4. Event Loop picks the callback
Event loop checks:
“Is the call stack empty?”

✔ If yes:

It pushes the callback to the stack
Executes it

### How does Node.js handle concurrency despite being single-threaded?

```
Node.js handles concurrency using its event-driven, non-blocking I/O model. It offloads asynchronous operations to the system or a thread pool and uses the event loop to process callbacks, allowing it to handle multiple requests efficiently on a single thread
```

### What are callbacks in Node.js?

A callback in Node.js is a function passed as an argument to another function and executed after an operation completes. It is commonly used in asynchronous programming to handle non-blocking operations like file handling and API calls.

### What is difference between Synchronous and Async Programming in Node.js?

```
Synchronous programming executes tasks sequentially and blocks the thread, whereas asynchronous programming allows non-blocking execution by handling operations in the background and processing results later. Node.js primarily uses asynchronous programming for better scalability and performance.
```

#### 1. Synchronous Programming (Blocking)

👉 In synchronous code:

- Tasks are executed one after another
- Each operation waits for the previous one to finish

```ts
const fs = require('fs');

const data = fs.readFileSync('file.txt', 'utf-8');
console.log(data);

console.log('Done');
```

👉 Behavior:

- readFileSync blocks execution
- Nothing else runs until it finishes ❌

#### 2. Asynchronous Programming (Non-Blocking)

👉 In async code:

- Tasks are executed without waiting
- Node.js continues execution and handles result later

```ts
const fs = require('fs');

fs.readFile('file.txt', 'utf-8', (err, data) => {
  console.log(data);
});

console.log('Done');
```

### What is "callback hell," and how can it be avoided? (3 methods)

Callback hell is a situation where nested callbacks make code complex and difficult to maintain. It can be avoided using Promises, async/await

1. Use Promises ✅
2. Use async/await

Example of Callback Hell

```ts
getUser(userId, (err, user) => {
  if (err) return handleError(err);

  getOrders(user.id, (err, orders) => {
    if (err) return handleError(err);

    getPayment(orders[0], (err, payment) => {
      if (err) return handleError(err);

      console.log(payment);
    });
  });
});
```

### What are Promises, and how do they improve async handling?
```
A Promise is an object that represents the eventual result of an asynchronous operation. It improves async handling by avoiding callback hell, supporting chaining, and providing better error handling. Promises also serve as the foundation for async/await in modern JavaScript
```

### How does async/await work?

```
Async/await is a modern way to handle asynchronous operations in JavaScript. An async function returns a Promise, and await pauses execution until the Promise resolves. It makes asynchronous code more readable and easier to manage compared to traditional Promise chaining.
```

Key Points (Interview Traps 🚨)
- await works only inside async functions
- It does not block the event loop
- 
It pauses only the current function