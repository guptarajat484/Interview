### 1. Hoisting.

### 2. Closures.

### 3. Var, Let, Const & Temporal Dead Zone.

### 4. This keyword.

### 5. Callback Functions.

### 6. Null and Undefined.

### 7. Promises, Promise APIs, Promise Chaining.

### 8. Async and Await.

### 9. Call, Apply, Bind.

### 10. Event loop in js.

### 11. Arrow Function and Regular Function.

### 12. Shallow and Deep copy.

### 13. Prototype and Prototypal Inheritance?

### 14. First Class Function.

### 5. Anonymous Functions

### 16. Higher Order Function.

### 17. Scopes.

### 18. ES6.

### 19. OOPS in js.

### 20. Currying in js.

### 21. What are the possible ways to create objects.

### 22. Pure function and its benefits

### 23. Impure function

### 24. IIFE

### 25. Strict Mode

### 26. Delete operator

### 27. Js is Compiled or Interpreted Language

### 28. Global Variables

### 29. Diff Between proto and prototype

### 30. Spread and Rest Operator

### 31. Call Stack

### 32. Const and Object Freeze

### 33. Lexical Scoping

### 34. Map and forEach

### 35. Memory Management

### 36. How To handle Error in JS

### 37. How to Improve Performance in Js 

### 38. what are memory leaks in Js

### 39. What are the limitations of Js in Large Scale applications

### 40. What is a polyfill

# Hoisting

### Hoisting is a concept that enables us to extract the values of variables and functions even before initialization or assignment without encountering an error. This occurs due to the first phase (memory creation phase) of the Execution Context. In this initial phase, the JavaScript engine allocates memory to all variables and functions. For variables, it assigns the value undefined, and for functions, it copies the entire function body.

# Closures

### A closure is a function that has access to its outer function scope even after the function has returned. Meaning, A closure can remember and access variables and arguments reference of its outer function even after the function has returned.

### So, Lexical Environment = local memory + lexical env of its parent. Hence, Lexical Environement is the local memory along with the lexical environment of its parent.

### Whenever an Execution Context is created, a Lexical environment(LE) is also created and is referenced in the local Execution Context(in memory space).

# Var

### <p>Scope Function-scoped</p>

### <p>Re-declaration ✅ Allowed</p>

### <p>Re-assigment ✅ Allowed

### <p>Hoisted Initialized to undefined </p>

### <p>Inital Value is optional</p>

# Let

### <p>Introduced in ES6 </p>

### <p>Scope Block-scoped </p>

### <p>Re-decalred ❌ Not allowed </p>

### <p>Re-assignment ✅ Allowed</p>

### <p>Hoisted (but in tdz)</p>

### <p>Initial value is optional</p>

# Constant

### <p>Introduced in ES6</p>

### <p>Scope Block-scoped</p>

### <p>Re-decalred ❌ Not allowed</p>

### <p>Re-assignment ❌ Not allowed</p>

### <p>Hoisted (but in tdz)</p>

### <p>Initial value is required</p>

# Temporal Dead Zone (TDZ)

### Time since when the let and const variable was hoisted until it is initialized some value.

# This keyword.

### In js this is a keyword always refer to the object

### The value of this dynamically determined

### When used outside function and object this refers to the global object

### When used inside the method of object this refers to the object itself

### When used inside function this refers to the object that the function is called

# Callback functions

### A callback function is a function passed as an argument to another function and is executed later, usually after some operation is completed.

## Why Use Callbacks?

### Callbacks help JavaScript handle asynchronous operations like:

### Ex:-

#### <p>function greet(name, callback) {</p>

#### <p>console.log("Hello, " + name);</p>

#### <p>callback();</p>

#### }

#### <p>function sayBye() {</p>

#### <p> console.log("Goodbye!"); </p>

#### }

#### greet("Rajat", sayBye);

### Why Use Callback Functions?

#### To execute code after a task is complete (e.g., after data is loaded).

#### They are essential for asynchronous programming in JavaScript.

# Undefined vs Not Defined in JS

#### undefined is when memory is allocated for the variable, but no value is assigned yet.

#### when the variable itself is not declared but called in code, then it is not defined.

# Promises

#### A Promise is an object that represents the eventual completion (or failure) of an asynchronous operation and its resulting value.

Introduced in ES6

Promises are an advancement over callback functions. They help prevent our code from falling into "callback hell."

### States of a Promise

Pending – Initial state, not fulfilled or rejected.

Fulfilled – Operation completed successfully.

Rejected – Operation failed.

# Promise API's

1. Promise.all
2. Promis.allsettle
3. Promise.race
4. Promise.any

### Promise.all

Takes a list of promises and returns one new promise.

That new promise succeeds only if all the given promises succeed.

If any one promise fails, the whole thing fails immediately with that error.

If all succeed, you get an array of results.

Example:-

##### const p1 = Promise.resolve(1);

##### const p2 = Promise.resolve(2);

##### const p3 = Promise.resolve(3);

##### Promise.all([p1, p2, p3])

##### .then(results => console.log(results)) // [1, 2, 3]

##### .catch(error => console.log(error)); //

### Promise.allSettled() Wait for Everything, Good or Bad

##### Takes a list of promises and returns one new promise.

##### Waits until all promises are either fulfilled or rejected.

##### Returns a list with each promise’s status and value or error.

##### It never fails, even if some promises fail.

### Promise.race() — “Whoever Finishes First Wins”

##### Takes a list of promises.

##### The returned promise settles as soon as one promise settles (resolves or rejects).

##### Returns the value or error of the first one that finishes.

### Promise.any() — “First One to Succeed”

##### Takes a list of promises.

##### Resolves when the first promise is fulfilled.

##### If all promises fail, it rejects with an AggregateError.

### Promise chaining

##### Means linking multiple .then() calls one after another, where each step uses the result of the previous one.

##### It helps to run asynchronous tasks in a sequence, instead of nesting callbacks.

### Async and Await.

##### Async Await allows to write async code in sync manner

##### Async Keyword is used to define a function that returns a promise.

##### Await keyword is used to pause the execution untill Promise is resolve or reject.

##### Async Await build on top of Promises

##### Async Await Introduced in ES2017

### Call, Apply, Bind.

##### All three methods — call(), apply(), and bind() — are used to manually set the value of this when calling a function.

### call()

##### Calls the function immediately.

##### Accepts arguments one by one.

##### returns function.

### Ex -

##### function greet (city) {

##### console.log(`Hello, I'm ${this.name} from ${city}`);

##### }

##### const person = { name: "Rajat" };

##### greet.call(person, "Indore");

### 2) apply()

##### Also calls the function immediately.

##### Accepts arguments as an array.

##### returns the function.

##### greet.apply(person, ["Indore"]);

### 3) bind()

##### Does not call the function immediately.

##### Returns a new function with this bound.

##### You can call it later.

#### Ex-

##### const greetRajat = greet.bind(person, "Indore");

##### greetRajat();

### Event Loop

##### It is a mechanism that allows to handle async operation such as timers, callbacks and non-blocking in a efficient way

##### The Event loop constantly monitors the callstack and callback queue

##### If the callstack is empty the event loop will move a callback function from a callback queue to the callstack to be executed

##### Once the callback function has executed it's is popped off the callstack and event loop continue to check the callback in the callback queue this process keeps repeating allwing Js to handle async task without blocking the main thread

#### Callstack

##### which is a data structure that keeps track os a currently executing function in js when a function is called It's pushed onto the call stack and when It's finished It's poped off the stack

#### MicroTask Queue

##### Microtask is same as callback queue but it has higher priority function in Microtask queue are executed early

##### All the callback functions that come through promises go in microtask queue.

# Arrow function

##### 1. Arrow function is also known as fat arrow function

##### 2. Arrow function introduces in ES6

##### 3. Arrow Function provide shorter syntex

##### 4. Arrow function don't have own this concept. This value of this is determined by surround lexical content

##### 5.Arrow Function dont have arguments object

##### 6.Arrow function can not be used as a constructor.

##### 7. Arrow function not fully hoisted

# Regular Function

##### 1. Can be used as a Contructor

##### 2. Have own this

##### 3. Have arguments object

#### 4. Regular function fully hoisted

# Shallow and Deep Copy.

##### In js when we copy one object into another object it will copy the reference of object

### There are two ways to copy object by value in js

### 1 Shallow Copy

##### A shallow copy copies only the top-level properties.

##### If the object has nested objects, only the reference is copied — not the actual data.

##### There are two ways to perfrom shallow in js

##### let user = Object.assign({}, original)

##### const shallowCopy = { ...original };

### 2 Deep Copy

##### A deep copy copies everything, including all nested levels.

##### The copied object is completely independent.

##### const shallowCopy = JSON.parse(JSON.stringify(original))

# Prototype and Prototypal inheritance?

### Prototype

##### Every object in JavaScript has a hidden property called [[Prototype]] (you can access it using **proto** or Object.getPrototypeOf()).

##### This prototype is another object that the current object can inherit properties and methods from.

##### const person = {

##### greet() {

##### console.log(`Hi, I'm ${this.name}`);

##### }

##### };

##### const user = {

##### name: "Rajat"

##### };

##### user.**proto** = person;

##### user.greet();

##### user doesn’t have its own greet(), so JavaScript looks up the prototype chain and finds it in person

# 2) Prototypal Inheritance

### Prototypal inheritance means one object can inherit directly from another object.

##### function User(name) {

##### this.name = name;

##### }

##### User.prototype.sayHello = function () {

##### console.log(`Hello, ${this.name}`);

##### };

##### const u1 = new User("Rajat");

##### u1.sayHello(); // Hello, Rajat ✅

# First Class Function

### In JavaScript, functions are treated like values — they can be:

#### Assigned to variables

#### Passed as arguments

#### Returned from other functions

#### This makes them first-class citizens in the language.

# Anonymous Functions

### An anonymous function is a function without a name.

### Used mostly:

### in callbacks

##### setTimeout(function () {

##### console.log("Hello after 1 sec");

##### },

### when functions are passed as arguments

# Higher-Order Functions (HOF)

### A Higher-Order Function is a function that:

##### ✅ Takes one or more functions as arguments

##### OR

##### ✅ Returns a function

### Common HOFs in JavaScript:

### map()

### filter()

### reduce()

### Custom HOFs you write

# Scopes in JavaScript

### In JavaScript, scope determines where variables are accessible in your code.

### Scope = Where a variable is visible.

### 1) Global Scope

##### Variables declared outside any function or block.

##### Accessible anywhere in the file.

### Function Scope

##### Variables declared inside a function are only accessible within that function.

### Block Scope (let and const)

##### Variables declared with let or const inside {} are not accessible outside.

### Lexical Scope

##### Functions can access variables from their outer scope where they were defined.

# ES6

### Template Literal

#### Supports multi-line strings and interpolation

### Default Parameters

### Destructuring (Arrays & Objects)

##### const [a, b] = [1, 2]; // Array destructuring

##### const { name, age } = { name: "Rajat", age: 25 }; // Object destructuring

### Rest and Spread Operators

### Import/Export

### For of loop, for In Loop

### For-of

##### Introduced in Es6

##### Designed for iterating over iterable object like array

##### No need of index handling

### For-in

##### Designed for iterating over the properties of objects.

# OOP (Object-Oriented Programming) in JavaScript

### JavaScript supports Object-Oriented Programming (OOP), even though it’s prototype-based (not class-based like Java or C++).

### 1 Class & Object

#### A class is a blueprint.

#### An object is an instance of a class.

### 2. Encapsulation

#### class BankAccount {

#### #balance = 0; // 🔒 private field

#### deposit(amount) {

#### this.#balance += amount;

#### }

#### getBalance() {

#### return this.#balance;

#### }

#### }

#### const account = new BankAccount();

#### account.deposit(1000);

#### console.log(account.getBalance());

# Abstraction – (Hide Complex Logic Behind Simple Interface)

### class Car {

#### startEngine() {

#### this.#injectFuel();

#### this.#ignite();

#### console.log("Engine started");

#### }

#### #injectFuel() { /_ hidden _/ }

#### #ignite() { /_ hidden _/ }

#### }

#### const myCar = new Car();

#### myCar.startEngine(); // ✅

# Currying

### Currying is a technique in JavaScript where a function doesn’t take all arguments at once, but instead takes one argument at a time and returns a new function for the next argument.

# Modules

#### In JavaScript, modules are reusable pieces of code that are encapsulated in their own scope and can be imported/exported between files. They help organize code, avoid naming conflicts, and improve maintainability.

### Why Use Modules?

#### Code reusability

#### Modularity

#### Better maintainability

# Slice

### 1. Slice is used to extract sub string from string

### 2. Slice does not modify original array

### 3. Return new extracted elements

# Splice

### ❌ Modifies the original array

### ✅ Can add or remove elements

### Return deleted elements

# module.exports

### Is used in CommonJS (the module system used in Node.js) to export functions, objects, or variables from a module so they can be used in another file.

# Object Seal & Object Freeze

### Object Seal

##### Prevents adding new properties

##### Prevents removing existing properties.

##### You can still update existing properties.

### Object Freeze

##### Prevents adding new properties.

##### Prevents deleting properties.

##### ❌ Prevents modifying existing property values.

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

## Memory Management in js

Memory management in JavaScript is the process of allocating memory when needed and automatically freeing it when it’s no longer used, using a mechanism called Garbage Collection.

## Memory Lifecycle

- Allocation: Memory is allocated when variables/objects are created
- Usage: You read/write memory
- Deallocation (Garbage Collection): Memory is freed automatically

## Garbage Collection

JavaScript uses Mark-and-Sweep algorithm
### 👉 How it works:
- Start from root objects (global scope)
- Mark all reachable objects
- Remove unreachable ones

``` ts 
let user = { name: "Rajat" };
user = null; // eligible for garbage collection
```

## Memory Leaks

Memory leak = memory not released when it should be

### ❌ Common Causes
- Global Variables 
``` ts
 name = "Rajat"; // ❌ no var/let/const 
```
- Closures: bigData stays in memory ❌
``` ts
function outer() {
  let bigData = new Array(1000000);

  return function inner() {
    console.log("Hello");
  };
}
```
- Forgotten Timers: If not cleared → memory leak
``` ts
setInterval(() => {
  console.log("Running...");
}, 1000);
```
- Event Listeners: Not removed → memory leak
``` ts
element.addEventListener("click", () => {}); 
```

## How To handle Error in JS

### 1. Try, catch
``` ts
try {
  const result = JSON.parse("invalid json");
} catch (error) {
  console.error("Error:", error.message);
}
```
### 2. Finally Block
``` ts
try {
  console.log("Try block");
} catch (e) {
  console.log("Error");
} finally {
  console.log("Always runs");
} 
```
### 3. Throwing Custom Errors
``` ts
function divide(a, b) {
  if (b === 0) {
    throw new Error("Division by zero");
  }
  return a / b;
}
``` 
### 4. Global Error Handling
``` ts
process.on("uncaughtException", (err) => {
  console.error("Uncaught Exception:", err);
});

process.on("unhandledRejection", (err) => {
  console.error("Unhandled Rejection:", err);
});
```
### 5. Express Error Handling Middleware
```ts
app.use((err, req, res, next) => {
  res.status(err.statusCode || 500).json({
    message: err.message
  });
});
```

## How to Improve Performance in Js

### 1. Avoid Blocking the Event Loop

```ts
for (let i = 0; i < 1e9; i++) {} // blocks thread ❌
```

### Use Asynchronous Code Properly

#### 1. ❌ Sequential (Slow)
```ts
await fetchA();
await fetchB();
```

#### 2. ✅ Parallel (Fast)
```ts 
await Promise.all([fetchA(), fetchB()]);
```

#### 3. Use Caching

## Difference between concurrency vs parallelism?

### 1. Concurrency

Concurrency is the ability to manage multiple tasks at the same time, but not necessarily executing them simultaneously.

```ts
async function run() {
  const p1 = fetch("api1"); // starts
  const p2 = fetch("api2"); // starts

  await p1;
  await p2;
} 
```

- Both tasks are in progress together (concurrent)
#### Example

Async/await, Promises
### 2. Parallelism

Parallelism is when multiple tasks are executed simultaneously using multiple threads or processors.

```ts
const { Worker } = require("worker_threads");

new Worker("./task1.js");
new Worker("./task2.js");
```
- Tasks run at the exact same time
- Both run in separate threads → true parallel execution

#### Example
Worker Threads, Clusters

## Limitations of JavaScript in Large-Scale Applications

- Lack of Static Typing (Without TypeScript)
- Callback Hell / Async Complexity
- Single-Threaded Nature
- Global Scope & Bugs
