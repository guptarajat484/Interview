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
- Difference between Promise and async/await?

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

Node.js works on a single-threaded, event-driven architecture. JavaScript code runs on a single main thread using the V8 engine. When asynchronous operations such as file reading, database queries, or API calls occur, Node.js delegates them to Libuv and the operating system. Once completed, their callbacks are placed in the Event Queue. The Event Loop continuously monitors the Call Stack and processes pending callbacks when the stack becomes empty. This non-blocking I/O model enables Node.js to handle thousands of concurrent requests efficiently with minimal resource consumption.

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

### What is an error-first callback pattern?

The error-first callback pattern is a standard convention in Node.js where:

- The first argument of the callback is reserved for an error
- The second argument contains the successful result

In the error-first callback pattern, the first argument of the callback is reserved for an error object, while the second argument contains the successful result. This convention provides a consistent way to handle asynchronous errors in Node.js.

Structure
```ts
(err,result) => {}
```

Basic Example

```ts
const fs = require('fs');

fs.readFile('file.txt', 'utf-8', (err, data) => {
  if (err) {
    return console.error(err);
  }

  console.log(data);
});
```

How it works

```ts
err = Error object
data = undefined
```

If Operation Suceeds:
```ts
err = null
data = actual result
```

Example

```ts
function divide(a, b, callback) {
  if (b === 0) {
    return callback(new Error('Cannot divide by zero'));
  }

  callback(null, a / b);
}

divide(10, 2, (err, result) => {
  if (err) {
    return console.error(err.message);
  }

  console.log(result);
});
```

#### Why Node.js Uses This Pattern
- Consistent error handling
- Easy async flow management
- Prevents uncaught async errors

### Difference between Promise and async/await?

async/await is built on top of Promises and provides cleaner syntax for handling asynchronous operations

1. Promise

A Promise is an object representing the result of an async operation.

Promise Example 

```ts
function fetchData() {
  return new Promise((resolve, reject) => {
    resolve('Data received');
  });
}

fetchData()
  .then(data => console.log(data))
  .catch(err => console.error(err));
```

2. Async/Await 

async/await is syntactic sugar over Promises.

```ts
async function fetchData() {
  return 'Data received';
}

async function process() {
  try {
    const data = await fetchData();
    console.log(data);
  } catch (err) {
    console.error(err);
  }
}

process();
```

Promises handle asynchronous operations using then/catch chaining, whereas async/await provides a cleaner and more readable syntax on top of Promises. async/await simplifies error handling using try/catch and makes asynchronous code look synchronous.


### What are Streams in Node.js?

Streams in Node.js are used to process data piece by piece (chunks) instead of loading the entire data into memory at once.

👉 In simple terms:

“Streams allow handling large amounts of data efficiently.”

Why Streams are Important

#### Without streams:

- Entire file loads into memory ❌
- High memory usage ❌

#### With streams:

- Data processed chunk by chunk ✅
- Better performance ✅
- Memory efficient ✅

```ts
const fs = require('fs');

const readStream = fs.createReadStream('large.txt');

readStream.on('data', chunk => {
  console.log(chunk);
});
```

#### Types of Streams in Node.js

1. Readable Stream

- Used to read data

Examples

File Reading
```ts
const readStream = fs.createReadStream('file.txt');
```
2. Writable Stream

- Used to write data

Examples
- File Writing

```ts
const writeStream = fs.createWriteStream('output.txt');
```

3. Duplex Stream

- Can read and write both

Examples:
- TCP Sockets

4. Trasform Stream

Modifies data while streaming

Examples: 
- Compression
- Encryption

```ts
const zlib = require('zlib');

const gzip = zlib.createGzip();
```

#### Real-World Use Cases
- Video streaming
- File uploads/downloads

How Streams Handle Large Files (Backpressure)

What is Backpressure?

"Data is Producesd faster than it consumed"

Example:

- Fast readable stream
- Slow writable stream

#### Problem Without Backpressure ❌
- Memory overflow
- Application slowdown


#### How Node.js Handles It ✅

Streams internally pause/resume flow automatically.

#### Example Using .pipe()

```ts
const fs = require('fs');

const readStream = fs.createReadStream('large.txt');
const writeStream = fs.createWriteStream('copy.txt');

readStream.pipe(writeStream);
```

👉 .pipe() automatically:

- Handles chunk flow
- Manages backpressure
- Prevents memory overload

Internal Mechanism

- When writable stream buffer is full:

- Reading pauses ⏸️

When buffer drains:

- Reading resumes ▶️


### What is a Buffer in Node.js?

A Buffer is a temporary memory area used to store binary data.

👉 Because JavaScript originally handled only text data, Node.js introduced Buffers for:

- Binary files
- Streams
- TCP packets

#### Creating Buffer
```ts
const buffer = Buffer.from('Hello');

console.log(buffer);
```

#### Output
```ts
<Buffer 48 65 6c 6c 6f>
```

#### convert Buffer to string

```ts
console.log(buffer.toString());
```

Real-World Usage

Buffers are used internally in:

- Streams
- File system
- Network operations

### Difference between fs.readFile() and fs.createReadStream()

#### 1. fs.readFile()

- Reads Entire file at once
- Memory Uage High
- Performance Slower for larger files
- Suitable for small files
- async yes
#### 2. fs.createReadStream()
- Chunk by chunk
- Memory usage low
- Better for Large File
- Suitable for large files
- Async yes

Example: fs.readFile()

```ts
fs.readFile('file.txt', 'utf-8', (err, data) => {
  console.log(data);
});
```

Entire File Load into RAM

Example: fs.createReadStream()

```ts
const stream = fs.createReadStream('large.txt');

stream.on('data', chunk => {
  console.log(chunk);
});
```

Reads Chunk-by-chunk

### Which One Should you use?

Use fs.readFile()

- small config files
- small json file

Use Strams

- Large Files
- Video Streaming

Streams are used in Node.js for processing large data efficiently in chunks instead of loading everything into memory. They support backpressure handling, which prevents memory overload by controlling data flow between readable and writable streams. Internally, streams use Buffers to manage binary data efficiently

### What is body-parser in Node.js?

body-parser is middleware used to parse incoming request bodies before accessing them in routes.

👉 It converts incoming request data into:

- JSON objects
- URL-encoded data

```ts
const express = require('express');
const bodyParser = require('body-parser');

const app = express();

app.use(bodyParser.json());

app.post('/user', (req, res) => {
  console.log(req.body);
  res.send(req.body);
});
```

What is CORS, and why is it important

CORS stands for:

👉 Cross-Origin Resource Sharing

It is a browser security mechanism that controls:

“Whether one domain can access resources from another domain.”

Example

Frontend:

http://frontend.com

Backend:

http://api.com

Different origins = browser blocks request by default ❌

#### Why CORS is Important

Without CORS:

- Browser prevents unauthorized cross-origin requests

With CORS:

- Server explicitly allows trusted origins

```ts
const cors = require('cors');

app.use(cors());
```

Restrict Specific Origin (Best Practice 🔥)
```ts
app.use(cors({
  origin: 'https://myapp.com'
}));
```

### 3. How do you manage Authentication & Authorization in Node.js?

#### Authentication

Verifying who the user is

#### Authorization
Verifying what the user can access

```ts
const jwt = require('jsonwebtoken');

const token = jwt.sign(
  { userId: user.id },
  'SECRET_KEY',
  { expiresIn: '1h' }
);
```

Verify Token Middleware
```ts
const jwt = require('jsonwebtoken');

function auth(req, res, next) {
  const token = req.headers.authorization?.split(' ')[1];

  if (!token) {
    return res.status(401).send('Unauthorized');
  }

  try {
    const decoded = jwt.verify(token, 'SECRET_KEY');
    req.user = decoded;
    next();
  } catch (err) {
    res.status(401).send('Invalid token');
  }
}
```

### 4. How do you protect routes in Express.js?

Protected routes use authentication middleware.

```ts
app.get('/dashboard', auth, (req, res) => {
  res.send('Protected Route');
});
```
👉 Flow:

1. Middleware Validate token
2. if valid -> access granted
3. Else -> unauthorized

#### Real-World Route Protection
```ts
app.post('/admin/users', auth, isAdmin, controller);
```
👉 Multiple middleware:

- Authentication
- Authorization

### How to Handle File Uploads in Node.js?

Most commonly handled using:

👉 Multer

#### Install

```ts
npm install multer
```

Example

```ts
const multer = require('multer');

const upload = multer({
  dest: 'uploads/'
});

app.post('/upload', upload.single('file'), (req, res) => {
  res.send('File uploaded');
});
```
#### Access Uploaded File
```ts
req.file
```

#### Multiple Files

```ts
upload.array('files', 5)
```

#### Real-World File Upload Flow 🔥
1. Receive file using Multer
2. Validate:
   - file type
   - size
3. Upload to:
   - AWS S3
   - Cloudinary
4. Store URL in DB

### How do you connect Node.js to a database (MongoDB/MySQL/Postgres)

In Node.js, database connections are usually handled using official drivers or ORMs/ODMs.

A) MongoDB Connection

Commonly used package:

👉 Mongoose

#### Install
```ts
npm install mongoose
```

Connection Example

```ts
const mongoose = require('mongoose');

mongoose.connect(process.env.MONGO_URI)
  .then(() => {
    console.log('MongoDB connected');
  })
  .catch(err => {
    console.error(err);
  });
```

#### B) MySQL Connection

Common package:

👉 mysql2

Install

```ts
npm install mysql2
```

#### Connection Example

```ts
const mysql = require('mysql2/promise');

const pool = mysql.createPool({
  host: 'localhost',
  user: 'root',
  password: 'password',
  database: 'test'
});
```

#### Query Example

```ts
const [rows] = await pool.query(
  'SELECT * FROM users'
);

console.log(rows);
```

C) PostgreSQL Connection

Common Package:

👉 node-postgres

```ts
npm install pg
```

```ts
const { Pool } = require('pg');

const pool = new Pool({
  user: 'postgres',
  host: 'localhost',
  database: 'test',
  password: 'password',
  port: 5432
});
```

### What is Connection Pooling, and why is it needed?

In production applications, I use connection pooling to efficiently reuse database connections and improve scalability.

Connection pooling means:

“Maintaining a pool of reusable database connections instead of creating a new connection for every request.”

Why is it Needed?

Creating DB connections repeatedly is expensive:

- Slow ❌
- High resource usage ❌

Pooling solves this:

- Reuses existing connections ✅
- Improves performance ✅
- Supports scalability ✅

Without Pooling ❌
- Request → Create DB Connection → Query → Close Connection

With Pooling ✅
- Request → Use Existing Connection from Pool

### 3. How do you Handle Transactions in Node.js?
What is a Transaction?

A transaction is a group of operations executed as a single unit.

For critical operations like payments or balance updates, I implement transactions to maintain data consistency and ensure rollback in case of failures.

👉 Either:

- All succeed ✅ 
 
- all rollback ❌

#### ACID Properties

ACID properties ensure reliable database transactions. Atomicity ensures all operations succeed or rollback together, Consistency maintains valid data states, Isolation prevents concurrent transaction conflicts, and Durability guarantees committed data persists even after system failures

Transactions ensure:

- Atomicity :- Either all operations succeed, or none of them succeed.

#### Example

Bank transfer:

```ts
Step 1: Deduct ₹100 from A
Step 2: Add ₹100 to B
```

#### Problem Scenario

- Money deducted from A
- Server Crasher before adding to b

👉 Data becomes inconsistent

With Atomicity ✅

If any step fails:

Entire transaction rolls back

```ts
ROLLBACK;
```
#### Real-World Meaning

No partial updates allowed.

#### Example in Node.js
```ts
await connection.beginTransaction();

try {

  await deductMoney();
  await addMoney();

  await connection.commit();

} catch (err) {

  await connection.rollback();

}
```

- Consistency :-  A transaction must take the database from one valid state to another valid state.

#### Consistency Ensures
- Constraints are Maintained
- No invalid Data
- Foreign Keys remain valid
- Business rules preserved

#### Example

If age column rule is:

```ts
Age > 0
```

Then:

```ts
INSERT INTO users(age) VALUES(-5);
```

❌ Rejected to maintain consistency

- Isolation: Multiple transactions should not interfere with each other.

#### Why Needed?

In real systems:

- Many users access DB simultaneously

Without isolation:

- Data corruption may happen ❌

#### Example

Two users booking same seat:

Transaction A:

```ts
Reads seat available
```

Transaction B:
```ts
Also reads same seat available
```
👉 Both book same seat ❌

- Durability: Once a transaction is committed, data is permanently saved even if system crashes

Example

After successful payment:

```ts
COMMIT;
```

Even if:

- Server crashes
- Power failure happens

👉 Data remains محفوظ (persistent)

How DB Ensures Durability

Using:

- Transaction logs
- Disk writes
- Recovery mechanisms

#### Real-World Example

UPI payment succeeds:

- Bank cannot lose transaction after confirmation

#### Complete Banking Example (All ACID Together)

#### Transfer ₹100
#### Atomicity

Both debit & credit succeed together

#### Consistency

Total money remains same

#### Isolation

Two transfers don't interfere

#### Durability

Committed transfer survives crash


### Explain the Event-Driven Architecture of Node.js

Node.js follows an event-driven, non-blocking architecture.

👉 Instead of waiting for tasks to finish:

- Node.js listens for events
- Executes callbacks when events occur

Core Components

#### Component

- Event Loop :- Manages Async Execution
- Event Queue :- Stores Callback
- Event Emitter :- Emits and Listens to Events
- Libuv :- Handles async I/O

#### Flow of Event-Driven Architecture

```ts
Request → Event Loop → Async Operation → Callback Queue → Execute Callback
```

Example

```ts
const fs = require('fs');

fs.readFile('file.txt', () => {
  console.log('File Read Completed');
});

console.log('Other work');

```

👉 Node.js:

- Starts file reading asynchronously
- Continues executing other code
- Executes callback later

Why It’s Powerful

- ✅ Handles thousands of concurrent requests
- ✅ Efficient for I/O-heavy apps
- ✅ Low memory usage

#### Real-World Examples
- Chat applications
- Streaming platforms
- APIs
- Real-time notifications

### 2. Difference Between process.nextTick() and setImmediate()

process.nextTick() executes before the event loop continues, whereas setImmediate() executes during the check phase. Therefore, process.nextTick usually runs first.

#### process.nextTick()

#### 👉 Executes callback:

- Immediately after current operation
- Before moving to next event loop phase

```ts
process.nextTick(() => {
  console.log('nextTick');
});
```

#### setImmediate()

👉 Executes callback:

- In the check phase of event loop

```ts
setImmediate(() => {
  console.log('setImmediate');
});
```

Which Runs First?

Usually:

process.nextTick() → setImmediate()

#### Example
```ts
setImmediate(() => console.log('immediate'));

process.nextTick(() => console.log('nextTick'));
```
#### Why?

Because:

- nextTick queue has higher priority
- Executed before event loop continues

### 3. What Happens When Node.js Encounters an Uncaught Exception?

An uncaught exception means:

“An error was thrown but not handled.”

```ts
throw new Error('Crash');
```

#### What Happens?

👉 Node.js:

- Prints stack trace
- Terminates the process ❌

#### Why Process Exits?

Because application state may become inconsistent.

#### Handling Uncaught Exceptions

```ts
process.on('uncaughtException', err => {
  console.error(err);
});
```

#### Best Practice 🔥

👉 Log error and gracefully restart process.

Do NOT continue normal execution.

#### Also Important

Unhandled Promise Rejection:

```ts
process.on('unhandledRejection', err => {
  console.error(err);
});
```

### 4. What Happens When We Execute require('module')?

When Node.js executes:

```ts
require('./math');
```
👉 Internally Node.js does:

Step-by-Step

1. Resolves Module Path
Checks:
- Core modules
- File modules
- node_modules

2. Loads Module

Reads Module File

3. Wraps Module
Node.js wraps Code Internally

```ts
(function(exports, require, module, __filename, __dirname) {
   // module code
});
```

4. Executes Module

Runs file once

5. Caches Module

Stored In 

```ts
require.cache
```

Important Point 🔥

Module executes only once.

Subsequent requires return cached exports.


### 5. What is Libuv, and What Role Does It Play in Node.js?

“Libuv is the underlying C library that powers Node.js asynchronous I/O, event loop, and thread pool functionality.”

Libuv is a C library used internally by Node.js.

👉 It provides:

- Event loop
- Async I/O
- Thread pool

#### Why Libuv Exists

JavaScript itself cannot perform:

- File I/O
- Networking
- Thread handling

Libuv handles these operations underneath.

#### Responsibilities of Libuv

- ✅ Event loop
- ✅ Thread pool
- ✅ Non-blocking I/O
- ✅ Timers
- ✅ File system operations

#### Thread Pool

#### Default size:

```ts
4 threads
```

#### Handles:

- File system
- DNS
- Crypto

### 6. Difference Between Worker Threads and Child Processes

#### Worker Threads

👉 Multiple threads inside same process.

Used for:

- CPU-intensive tasks

```ts
const { Worker } = require('worker_threads');
```

#### Child Processes

👉 Separate independent processes.

Used for:

- Running external commands
- Isolation

```ts
const { fork } = require('child_process');
```

### Difference Between spawn() and fork()

Both belong to:
```ts
child_process
```

#### spawn()

Used to run:

- Any system command

```ts
spawn('ls');
```

#### Fork()

Specialized version for:

- Node.js scripts

```ts
fork('worker.js');
```

### What is a Cluster in Node.js?

Cluster allows Node.js to:

“Use multiple CPU cores.”

### Why Needed?

Node.js is single-threaded by default.

Without cluster:

- Only one CPU core used ❌

#### Cluster Solution

Creates multiple worker processes.

```ts
const cluster = require('cluster');
```

#### Architecture

```ts
Master Process
   ├── Worker 1
   ├── Worker 2
   ├── Worker 3
```

Benefits

- ✅ Better CPU utilization
- ✅ Improved scalability
- ✅ Fault tolerance

### 9. How Do You Scale Node.js Horizontally?

In production systems, Node.js applications are typically scaled horizontally using load balancers, containers, and multiple instances. Since Node.js is single-threaded, clustering and worker processes help utilize CPU cores efficiently, while stateless architecture enables easy scaling across servers

Horizontal scaling means:

“Running multiple instances of application.”

#### Common Approaches

1. Load Balancer
Use
- Nginx
- HAProxy
- AWS ELB

Distributes traffic across instances

2. Cluster Module

Use multiple CPU cores on same machine

3. Docker + Kubernetes

Run Multiple Container

4. StatelesS APIs

Store sessions in:

- Redis
- DB

Avoid local memory sessions.

5. Message Queues

Use:

- RabbitMQ
- Kafka

For distributed workloads.

### What are WebSockets, and how are they implemented in Node.js?

What are WebSockets?

WebSockets provide:

“Full-duplex, persistent communication between client and server.”

#### HTTP

- Connection -> Req/Res
- Communication -> One Way
- Real-time -> Poor
- OverHead -> Higher

#### WebSocket

- Connection -> Persistent
- Communication -> Two- way
- Real-time -> Excellent
- Overhead -> Lower

#### Real-World Use Cases

- Chat apps
- Live notifications
- Gaming
- Stock market updates
- Collaborative tools

#### Implementing WebSocket in Node.js

```ts
npm install ws
```

```ts
const WebSocket = require('ws');

const server = new WebSocket.Server({ port: 3000 });

server.on('connection', socket => {

  console.log('Client connected');

  socket.on('message', message => {
    console.log(message.toString());

    socket.send('Message received');
  });

});
````

### 2. Difference Between WebSockets and Socket.IO

#### WebSocket

👉 Native protocol

- Lightweight
- Faster
- Requires manual reconnection handling

#### Socket.IO

👉 Library built on top of WebSocket
- Reconnection Higher

Commonly used package:
```ts
Socket.IO
```

#### Features of Socket.IO

- ✅ Auto reconnection
- ✅ Rooms/channels
- ✅ Broadcasting
- ✅ Fallback mechanisms
- ✅ Easier event handling

#### Which One to Use?
#### Use WebSocket
- Lightweight high-performance systems
### Use Socket.IO
- Most real-time apps
- Faster development

### Explain Microservices Architecture and How Node.js Supports It
#### What are Microservices?

Microservices architecture means:

“Breaking a large application into small independent services.”

Each service:

- Has its own responsibility
- Runs independently
- Communicates via APIs/messages

#### Example
```ts
User Service
Order Service
Payment Service
Notification Service
```

#### Benefits

- ✅ Independent deployment
- ✅ Better scalability
- ✅ Fault isolation
- ✅ Technology flexibility

#### Why Node.js is Good for Microservices

1. Lightweight Runtime

Fast startup time.

2. Non-blocking I/O

Handles Concurrent API requests efficiently

#### Communication Between Services

Common methods:

- REST APIs
- gRPC
- Message brokers

#### Examples:

- RabbitMQ
- Kafka

### Difference Between RESTful APIs and GraphQL in Node.js

#### REST API

REST exposes:

“Multiple endpoints for different resources.”

#### Example
```ts
GET /users
GET /orders
GET /products
```

#### GraphQL

GraphQL exposes:

“Single endpoint where client requests exactly needed data.”

### 5. How do you Handle Real-Time Data Processing in Node.js?

Real-time processing means:

“Handling and delivering data instantly as events occur.”

Common Techniques

####  1. WebSockets/ Socket.io

For Live Communication

#### 2. Event Driven

 Using:
- Event Emitter
- Message Queues

#### 3. Message Brokers

Examples
- Kafka
- Rabbit MQ
- Redis Pub/Sub

#### 4. Streams

Used For

- Large-scale real-time processing
- Video Data

#### 5. Background Jobs
Using 
- BullMQ




