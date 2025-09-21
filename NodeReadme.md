# 📘 Backend Interview Questions (3–5 Years Experience)

A structured collection of **Node.js, Express.js, Database, Security, and System Design questions** for backend interviews.

---

## 🟢 Beginner Level (Core Basics)

### Node.js Fundamentals
- What is Node.js, and how does it work?
- What is the difference between Node.js and JavaScript?
- What kind of API functions are supported by Node.js?
- Is Node.js single-threaded?
- What are the main disadvantages of Node.js?

### Modules & Package Management
- What is a module in Node.js?
- What is the difference between CommonJS and ES Modules?
- How do you import a module in Node.js?
- What is `package.json`, and why is it essential?
- What is `npm`, and what are its advantages?

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

### Asynchronous Programming
- What are callbacks in Node.js?
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

### Memory & Performance
- How do you detect and fix memory leaks in Node.js?
- What is the significance of `--max-old-space-size` flag?
- Explain V8 hidden classes and their performance impact.
- How can you implement a graceful shutdown in Node.js?
- What are best practices for performance optimization in Node.js?

### Security
- What are the most common security vulnerabilities in Node.js, and how do you prevent them?
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

---

✅ Use this README as a **handbook** to prepare step by step for backend interviews (focus on Intermediate + Advanced for 3–5 yrs experience).
