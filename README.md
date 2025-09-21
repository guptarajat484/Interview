# JavaScript Interview Concepts

1. Hoisting
2. Closures
3. Var, Let, Const & Temporal Dead Zone
4. This keyword
5. Callback Functions
6. null and undefined
7. Promises, Promise APIs, Promise Chaining
8. Async and Await
9. Call, Apply, Bind
10. Event loop in js
11. Arrow function and regular function
12. Shallow and Deep copy
13. Prototype and prototypal inheritance
14. First class function
15. Anonymous Functions
16. Higher order function
17. Scopes
18. ES6
19. OOPS in js
20. Currying in js
21. Modules
22. Array Methods (Slice and Splice)
23. Module Systems
24. Object Methods
25. Pass by value & reference
26. Map & Filter
27. Map & forEach
28. CORS

## Hoisting

Hoisting is a concept that enables us to extract the values of variables and functions even before initialization or assignment without encountering an error. This occurs due to the first phase (memory creation phase) of the Execution Context. In this initial phase, the JavaScript engine allocates memory to all variables and functions. For variables, it assigns the value undefined, and for functions, it copies the entire function body.

## Closures

A closure is a function that has access to its outer function scope even after the function has returned. Meaning, A closure can remember and access variables and arguments reference of its outer function even after the function has returned.

So, Lexical Environment = local memory + lexical env of its parent. Hence, Lexical Environment is the local memory along with the lexical environment of its parent.

Whenever an Execution Context is created, a Lexical environment(LE) is also created and is referenced in the local Execution Context(in memory space).

## Variable Declarations

### Var

- **Scope:** Function-scoped
- **Re-declaration:** ✅ Allowed
- **Re-assignment:** ✅ Allowed
- **Hoisted:** Initialized to undefined
- **Initial Value:** Optional

### Let

- **Introduced in:** ES6
- **Scope:** Block-scoped
- **Re-declaration:** ❌ Not allowed
- **Re-assignment:** ✅ Allowed
- **Hoisted:** Yes (but in TDZ)
- **Initial value:** Optional

### Const

- **Introduced in:** ES6
- **Scope:** Block-scoped
- **Re-declaration:** ❌ Not allowed
- **Re-assignment:** ❌ Not allowed
- **Hoisted:** Yes (but in TDZ)
- **Initial value:** Required

## Temporal Dead Zone (TDZ)

Time since when the let and const variable was hoisted until it is initialized some value.

## This Keyword

In JavaScript, `this` is a keyword that always refers to an object:

- The value of `this` is dynamically determined
- When used outside function and object, `this` refers to the global object
- When used inside the method of object, `this` refers to the object itself
- When used inside function, `this` refers to the object that the function is called on

## Callback Functions

A callback function is a function passed as an argument to another function and is executed later, usually after some operation is completed.

### Example:

```javascript
function greet(name, callback) {
  console.log("Hello, " + name);
  callback();
}

function sayBye() {
  console.log("Goodbye!");
}

greet("Rajat", sayBye);
```

### Why Use Callback Functions?

- To execute code after a task is complete (e.g., after data is loaded)
- They are essential for asynchronous programming in JavaScript

## Undefined vs Not Defined in JS

- **undefined:** When memory is allocated for the variable, but no value is assigned yet
- **not defined:** When the variable itself is not declared but called in code

## Promises

A Promise is an object that represents the eventual completion (or failure) of an asynchronous operation and its resulting value.

- Introduced in ES6
- Promises are an advancement over callback functions
- They help prevent our code from falling into "callback hell"

### States of a Promise

- **Pending:** Initial state, not fulfilled or rejected
- **Fulfilled:** Operation completed successfully
- **Rejected:** Operation failed

## Promise APIs

1. Promise.all
2. Promise.allSettled
3. Promise.race
4. Promise.any

### Promise.all

Takes a list of promises and returns one new promise.

- That new promise succeeds only if all the given promises succeed
- If any one promise fails, the whole thing fails immediately with that error
- If all succeed, you get an array of results

```javascript
const p1 = Promise.resolve(1);
const p2 = Promise.resolve(2);
const p3 = Promise.resolve(3);

Promise.all([p1, p2, p3])
  .then((results) => console.log(results)) // [1, 2, 3]
  .catch((error) => console.log(error));
```

### Promise.allSettled() — Wait for Everything, Good or Bad

- Takes a list of promises and returns one new promise
- Waits until all promises are either fulfilled or rejected
- Returns a list with each promise's status and value or error
- It never fails, even if some promises fail

### Promise.race() — "Whoever Finishes First Wins"

- Takes a list of promises
- The returned promise settles as soon as one promise settles (resolves or rejects)
- Returns the value or error of the first one that finishes

### Promise.any() — "First One to Succeed"

- Takes a list of promises
- Resolves when the first promise is fulfilled
- If all promises fail, it rejects with an AggregateError

### Promise Chaining

Means linking multiple `.then()` calls one after another, where each step uses the result of the previous one. It helps to run asynchronous tasks in a sequence, instead of nesting callbacks.

## Async and Await

- Async Await allows to write async code in sync manner
- **Async** keyword is used to define a function that returns a promise
- **Await** keyword is used to pause the execution until Promise is resolved or rejected
- Async Await is built on top of Promises
- Async Await introduced in ES2017

## Call, Apply, Bind

All three methods — `call()`, `apply()`, and `bind()` — are used to manually set the value of `this` when calling a function.

### call()

- Calls the function immediately
- Accepts arguments one by one
- Returns function result

```javascript
function greet(city) {
  console.log(`Hello, I'm ${this.name} from ${city}`);
}

const person = { name: "Rajat" };
greet.call(person, "Indore");
```

### apply()

- Also calls the function immediately
- Accepts arguments as an array
- Returns the function result

```javascript
greet.apply(person, ["Indore"]);
```

### bind()

- Does not call the function immediately
- Returns a new function with `this` bound
- You can call it later

```javascript
const greetRajat = greet.bind(person, "Indore");
greetRajat();
```

## Event Loop

It is a mechanism that allows JavaScript to handle async operations such as timers, callbacks and non-blocking operations in an efficient way.

- The Event loop constantly monitors the call stack and callback queue
- If the call stack is empty, the event loop will move a callback function from callback queue to the call stack to be executed
- Once the callback function has executed, it's popped off the call stack and event loop continues to check callbacks in the callback queue
- This process keeps repeating, allowing JS to handle async tasks without blocking the main thread

### Call Stack

A data structure that keeps track of currently executing functions in JS. When a function is called, it's pushed onto the call stack and when it's finished, it's popped off the stack.

### Microtask Queue

- Microtask is same as callback queue but it has higher priority
- Functions in Microtask queue are executed early
- All the callback functions that come through promises go in microtask queue

## Arrow Function vs Regular Function

### Arrow Function

1. Arrow function is also known as fat arrow function
2. Arrow function introduced in ES6
3. Arrow Function provides shorter syntax
4. Arrow functions don't have their own `this` concept. The value of `this` is determined by surrounding lexical context
5. Arrow Functions don't have arguments object
6. Arrow functions cannot be used as a constructor
7. Arrow functions are not fully hoisted

### Regular Function

1. Can be used as a Constructor
2. Have their own `this`
3. Have arguments object
4. Regular functions are fully hoisted

## Shallow and Deep Copy

In JS, when we copy one object into another object, it will copy the reference of the object.

There are two ways to copy object by value in JS:

### 1. Shallow Copy

A shallow copy copies only the top-level properties. If the object has nested objects, only the reference is copied — not the actual data.

There are two ways to perform shallow copy in JS:

```javascript
let user = Object.assign({}, original);
const shallowCopy = { ...original };
```

### 2. Deep Copy

A deep copy copies everything, including all nested levels. The copied object is completely independent.

```javascript
const deepCopy = JSON.parse(JSON.stringify(original));
```

## Prototype and Prototypal Inheritance

### Prototype

Every object in JavaScript has a hidden property called `[[Prototype]]` (you can access it using `__proto__` or `Object.getPrototypeOf()`). This prototype is another object that the current object can inherit properties and methods from.

```javascript
const person = {
  greet() {
    console.log(`Hi, I'm ${this.name}`);
  },
};

const user = {
  name: "Rajat",
};

user.__proto__ = person;
user.greet(); // Hi, I'm Rajat
```

`user` doesn't have its own `greet()`, so JavaScript looks up the prototype chain and finds it in `person`.

### Prototypal Inheritance

Prototypal inheritance means one object can inherit directly from another object.

```javascript
function User(name) {
  this.name = name;
}

User.prototype.sayHello = function () {
  console.log(`Hello, ${this.name}`);
};

const u1 = new User("Rajat");
u1.sayHello(); // Hello, Rajat ✅
```

## First Class Function

In JavaScript, functions are treated like values — they can be:

- Assigned to variables
- Passed as arguments
- Returned from other functions

This makes them first-class citizens in the language.

## Anonymous Functions

An anonymous function is a function without a name.

Used mostly:

- In callbacks
- When functions are passed as arguments

```javascript
setTimeout(function () {
  console.log("Hello after 1 sec");
}, 1000);
```

## Higher-Order Functions (HOF)

A Higher-Order Function is a function that:

✅ Takes one or more functions as arguments
**OR**
✅ Returns a function

### Common HOFs in JavaScript:

- `map()`
- `filter()`
- `reduce()`
- Custom HOFs you write

## Scopes in JavaScript

In JavaScript, scope determines where variables are accessible in your code.

**Scope = Where a variable is visible.**

### 1. Global Scope

Variables declared outside any function or block. Accessible anywhere in the file.

### 2. Function Scope

Variables declared inside a function are only accessible within that function.

### 3. Block Scope (let and const)

Variables declared with `let` or `const` inside `{}` are not accessible outside.

### 4. Lexical Scope

Functions can access variables from their outer scope where they were defined.

## ES6 Features

### Template Literals

Supports multi-line strings and interpolation.

### Default Parameters

### Destructuring (Arrays & Objects)

```javascript
const [a, b] = [1, 2]; // Array destructuring
const { name, age } = { name: "Rajat", age: 25 }; // Object destructuring
```

### Rest and Spread Operators

### Import/Export

### For-of Loop vs For-in Loop

#### For-of

- Introduced in ES6
- Designed for iterating over iterable objects like arrays
- No need for index handling

#### For-in

- Designed for iterating over the properties of objects

## OOP (Object-Oriented Programming) in JavaScript

JavaScript supports Object-Oriented Programming (OOP), even though it's prototype-based (not class-based like Java or C++).

### 1. Class & Object

A class is a blueprint. An object is an instance of a class.

### 2. Encapsulation

```javascript
class BankAccount {
  #balance = 0; // 🔒 private field

  deposit(amount) {
    this.#balance += amount;
  }

  getBalance() {
    return this.#balance;
  }
}

const account = new BankAccount();
account.deposit(1000);
console.log(account.getBalance());
```

### 3. Abstraction — (Hide Complex Logic Behind Simple Interface)

```javascript
class Car {
  startEngine() {
    this.#injectFuel();
    this.#ignite();
    console.log("Engine started");
  }

  #injectFuel() {
    /* hidden */
  }
  #ignite() {
    /* hidden */
  }
}

const myCar = new Car();
myCar.startEngine(); // ✅
```

## Currying

Currying is a technique in JavaScript where a function doesn't take all arguments at once, but instead takes one argument at a time and returns a new function for the next argument.

## Modules

In JavaScript, modules are reusable pieces of code that are encapsulated in their own scope and can be imported/exported between files. They help organize code, avoid naming conflicts, and improve maintainability.

### Why Use Modules?

- Code reusability
- Modularity
- Better maintainability

## Array Methods

### Slice

1. Slice is used to extract substring from string
2. Slice does not modify original array
3. Returns new extracted elements

### Splice

- ❌ Modifies the original array
- ✅ Can add or remove elements
- Returns deleted elements

## Module Systems

### module.exports

Is used in CommonJS (the module system used in Node.js) to export functions, objects, or variables from a module so they can be used in another file.

## Object Methods

### Object.seal()

- Prevents adding new properties
- Prevents removing existing properties
- ✅ You can still update existing properties

### Object.freeze()

- Prevents adding new properties
- Prevents deleting properties
- ❌ Prevents modifying existing property values

# Pass by value & reference

### Pass by Value

##### Used for Primitive Value

##### Copy of value is passed

##### No — changes do not affect the original value

##### Two different memory locations

# Pass by Reference

##### Used for Non Primitive Value

##### A reference is passed

##### Changes afftect the original Value

##### Same memory location

# Map & Filter

### Map

##### Transforms each element in an array

##### Returns a new array of the same length

##### Callback Expects a return value for each element

##### Not mutated

### Filter

##### Filters out elements based on a condition

##### Returns a new array with fewer or equal elements

##### Callback returns a boolean (true/false)

##### ❌ Not mutated

# Map & forEach

### Map

##### Creates a new array by transforming each element

##### Returns a new array

##### Map can be chainable

##### Does not modify original array

### forEach

##### Executes a function for each element.

##### Return undefined

##### forEach can not be chainable

##### Does not modify original array

# CORS

### CORS stands for Cross-Origin Resource Sharing.

##### It’s a security mechanism enforced by browsers to restrict cross-origin HTTP requests initiated from scripts.

##### By default, the browser only allows requests to the same origin (same protocol, domain, and port).

##### If a frontend hosted at http://localhost:3000 tries to make a request to https://api.example.com, it will be blocked ##### unless CORS is enabled on the server.

# Node.js Interview Topics

## Basic

1. What is Node.js?
2. What is the difference between Node.js and JavaScript?
3. How Node.js Works?
4. Advantages Of Node.js
5. Disadvatages of Node.js

## Modules In Node.js

6. What is modules
7. What is commonjs module
8. What is ES module
9. What is difference between commonjs and ES Module
10. What Actually happens require('module')

## Single Threaded

11. Is node.js single threaded
12. How node.js handle concurrency despite being single threaded

## Event Loop

13. Event loop in node.js
14. phases of event loop
15. Differnce between process.nextTick() & setImmediate()

## Event Driven

16. What is event driven programming in node.js
17. what is event driven architecture in node.js

## LibUV

18. what is libuv library
19. what is REPL in node.js
20. What happens Node.js Encounter uncaught Exception
21. What is control flow on node.js

## Asyncronous Programming

22. What kind of API functions supported by Node.js
23. What is Difference between syncronous and asyc programming
24. what is callback
25. what is Promises
26. what is async/ await
27. What is callback hell & how we can avoid it
28. What happens when a promise is rejected without a catch handler
29. what is error first callback pattern

## Process, Threads & Performance

30. What is Worker thread
31. What is cluster module
32. What are child process
33. What is difference between workerthread and child Process
34. what is difference between spawn and fork
35. How Node.js Handles cpu-intensive task
36. How Do you Handle CPU-intesive task
37. How to implement graceful shutdown in node.js

## Authentication & Authorization

38. How do you implement authentication and authorization in node.js
39. How do you handle jwt validation
40. What is the passport module & how is it used
41. what are the major security concerns in node.js
42. How do you prevent SQL Injection
43. How do you implement proper rate limiting
44. How do you implement brute foce attack
45. How do you protect against CSRF and XSS attack
46. what are the risks of eval()

## HTTP Module

47. How Node.js handle http internally
48. How do you create an http server using hhtp module
49. Difference b/w res.send, res.json and res.end
50. How do handle pagination in node.js

## Streams & File System

51. What are the streams in node.js & what are their types
52. How streams handle data
53. Diff B/w readfile and createReadStream
54. What is buffer in node.js
55. What is fs module
56. How do you handle File upload using using

## Express

57. What is express.js
58. Features of express.js
59. What is middleware in node.js
60. How do you handle Errors in node.js
61. How do you handle routing in express.
62. Diff b/w req.params, req.query and req.body

## Database and ORM

63. How do you handle database connection
64. How do you connect node.js app to database
65. How do you implement connection polling
66. How do you handle transaction
67. What is ORM
68. What are the advantafes of ORM

## NPM

69. What is NPM
70. What is Package.json
71. What is Package.lock.json
72. Diff b/w NPM and yarn

## Deployment

73. What are the steps to deploy a node.js
74. How do you manage env varibles
75. What is PM2
76. How do you implement structured logging in node.js
77. what monitor and alerting strategies do you use in production (Grafana)

## What is Node.js?

Node.js is an open-source, cross-platform, runtime environment built on Google Chrome's V8 JavaScript engine. It allows developers to run JavaScript on the server-side.

Node.js Maintained by open.js Foundation.

## Difference Between Node.js and JavaScript

JavaScript is a programming language, mainly used in browsers to create dynamic web pages. Node.js, on the other hand, is a runtime environment that allows us to run JavaScript on the server-side. While browser JavaScript can access the DOM, Node.js provides APIs for file systems, network operations, and more.

## Advantages of Node.js

#### 1. Single-Threaded but Highly Scalable

Node.js handles thousands of requests using the event loop, not threads.

Best for I/O-heavy apps like chat apps, REST APIs, etc.

#### 2. ⚡ Fast Execution with V8 Engine

Node.js uses Google’s V8 engine which compiles JavaScript to machine code.

#### 3. 📦 Huge Package Ecosystem (npm)

2M+ reusable packages on npm

#### 4. 🔁 Non-blocking Asynchronous I/O

Handles file, DB, and network operations without blocking the thread.

#### 5. 🌍 Cross-Platform Support

Node.js can be used to build desktop apps using Electron.js or mobile apps with React Native backend.

## Disadvantages of Node.js

#### 1. CPU-Intensive Tasks Block the Event Loop

Node.js is single-threaded, so heavy CPU operations (like image/video processing, data encryption, etc.) can block all other requests.

Solution:
Use child_process, worker_threads,

#### 2. Not Ideal for Heavy Computation

Node.js is great for I/O, but not for:

Machine learning

Big data crunching

Complex algorithms

#### Immature or Low-Quality npm Packages

Anyone can publish an npm package.

Some packages are outdated, buggy, or insecure.

## Is Node.js Single-Threaded?

If you're giving it an asynchronous task then it is single threaded  but if are giving some asynchronous task is used threadpool in libuv library which has 4 threads and acts as a multithreaded.


## Can We Change Thread Pool Size in Node.js?

Yes. Node.js uses a libuv thread pool, which by default has 4 threads but you can increase or decrease this using UV_THREADPOOL_SIZE

set UV_THREADPOOL_SIZE=8 && node app.js

You must set this before your application starts.

### Core Concept

Node.js runs JavaScript on a single thread — called the main thread or the event loop thread.

But for asynchronous tasks (file I/O, DNS lookups, compression, etc.), Node.js delegates them to a thread pool (typically 4 threads by default via libuv) — enabling non-blocking I/O.

### So is Node.js really single-threaded?

✅ YES:
For executing JavaScript, there is only one thread — no shared memory, no race conditions.

❌ NO:
For I/O and async operations, it uses multi-threaded capabilities under the hood (via libuv, worker threads, etc.)

### 🧠 Bonus Tip for Interviews:

If they ask:

“How does Node.js handle 1000 concurrent requests with a single thread?”

Answer:

“Node.js handles incoming requests asynchronously using a single-threaded event loop. When it encounters blocking operations like database queries, file system access, or cryptography, it delegates them to the libuv thread pool or uses non-blocking OS APIs. This allows the main thread to keep processing other requests while waiting for those operations to complete, resulting in high concurrency and efficient resource usage.”

## How does Node.js handle concurrency despite being single-threaded?

Node.js achieves concurrency using its event loop and libuv thread pool. It delegates blocking operations to background threads, allowing the main thread to handle more incoming tasks. This non-blocking, asynchronous architecture enables Node.js to scale efficiently in I/O-heavy applications like APIs, real-time services, and file servers

### If the interviewer asks how to handle CPU-heavy tasks in Node.js

Worker Threads (since Node v10.5+)

Child Process or Cluster

### What is modules?

In Node.js, modules are reusable blocks of code that help organise, manage, and separate functionality within an application. Modules allow developers to break down an application into smaller, manageable parts, each focused on a specific task, which makes it easier to maintain and debug.

#### Types of node.js Modules

##### Core Modules

##### Local Modules

##### Third-Party Modules

#### Core Modules

These are built-in modules provided by Node.js, such as http, fs (file system), path, crypto, and others. They come with the Node.js installation and don’t require any additional setup. For example, http is used to create HTTP servers, while fs is for file operations.

#### Local Modules

These are custom modules that developers create for their specific applications. They might contain utility functions, configurations, or business logic.

#### Third-Party Modules

These are modules created by other developers and shared on platforms like npm (Node Package Manager). They can be installed and imported into a project to extend its functionality. Popular third-party modules include express (for web servers), mongoose (for MongoDB connections).

### What is CommonJS Module

#### This is Default Module system in Node.js no need to configure.

#### Uses require to import and module.exports to export the module.

#### It loads the module Sync manner

#### It follows non-strict rules

### What is ES Module

#### This is modern module system in node.js it requires configuration in package.json type = module

#### Uses import and Export

#### It loads module async manner

#### It follows strict mode

#### Default Module System in React, Angular.

## What actually happens require('module')

#### 1. Resolving Module: Determines the path of file.

#### 2. Loading the module:- Once the path is resolved node.js loads the file.

#### 3. Wrapping Inside IIFE:- The Module Code Wrapped inside IIFE. This wraps helps encapsulte the code.

#### 4. Code Evolution and Module.exports:- After wrapping, Nodejs evalutes the modules code. During this evaluotion, module.exports avilable to othey files.

#### 5. Caching:- Caching is crucial for performance. Node.js Caches the result of the require(), So that the module is loaded and execute once.

## What is global object in node.js?

In Node.js the global object is called 'global', global object in node.js Provides access to functionalities such as console, process, setTimeOut

## What is globalThis ?

It was Introduced in ES2020, It Provide a Standardarize way to refer to the global object in any environment

##### In Browswers globalThis is equal to window
##### In Node.js globalThis is equal to global

## How Synchronous code is executes

Whenever you run the Code, a global execution Context is
created. and it is pushed into the callstack.
Whene ever fn Comes into.Callstack and all the calculations and results are stored into heap
Once the execution is done result is Returned to
GEC (.Global Exeution .Context) and fn moves out of the Call Stack
Once the whole Code is executed call stack will
become Empty!

## How Asynchronous Code is executes

#### First Global execution is created inside Call Stack
#### Memory will be allocate to variables.
#### For API calls Libuv Manage the API Calls it will register the API Call and takes the callback libuv will manage the API call js engine will move to next line
#### All async task will be offload to libuv
#### Now Js will move to another function engine will execute another fuctions
#### Once the call stack empty all the memory cleaned by garbage collector
#### once the libuv is done with all the tasks and it sees that the call stack is empty.
#### libuv sends the callback function to callstack  
#### The Callstack will execute all the stuff inside it quickely.

#### This Code Will Execute when all the synchronous code will get executed and call stack become empty.

## What is Event Loop

The event loop is the mechanism in Node.js that allows non-blocking, asynchronous operations — even though JavaScript runs on a single thread.

It continuously checks for pending tasks (like timers, I/O, promises) and executes callbacks in the correct order without blocking the main thread.

### 🔄 How the Event Loop Works (High-Level)

#### Node.js starts executing your JavaScript code in the main thread.
#### When it encounters async operations (e.g., fs.readFile, setTimeout, Promises), it: Offloads them to the libuv.

#### Once the async task completes, a callback is queued.

#### The event loop picks up the callback from the queue and executes it on the main thread.

### 🧠 Event Loop Phases 

#### 1. Timers:- Executes callback from  setTimeout() and setInterval()
#### 2. Pending callbacks:- 	Executes I/O callbacks deferred to the next loop
#### 3. Idle, Prepare:- Internal use only
#### 4. Poll:- Retrieve new I/o event, executes I/o related cb()
#### Check:- Execute setImmediate() callbacks
#### Close Callbacks:- Handles Close Events like socket.on('close).

#### Before and after each phase, microtasks (like Promise.then() and process.nextTick()) are also executed.




















