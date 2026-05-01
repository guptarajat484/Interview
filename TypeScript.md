# TypeScript & NestJS Interview Notes (Node.js Backend)

## What is TypeScript and why do we use it in Node.js projects?

TypeScript is a **superset of JavaScript** that adds **static typing**
to JavaScript.

JavaScript is a loosely typed language which can lead to runtime errors.
TypeScript helps developers catch these errors during development before
running the code.

### Benefits

-   Static type checking
-   Early error detection
-   Improved code maintainability
-   Better scalability for large projects

``` ts
function add(a: number, b: number): number {
  return a + b;
}
```

------------------------------------------------------------------------

## Difference Between `interface` and `type`

  --------------------------------------------- --------------------------
  ### Interface 
  -------------------------------------------- --------------------------
  - Used to define object structure.              
  - Can be extended.
  - Supports declaration merging.                
  -----------------------------------------------------------------------
  ### Type

  - Can define objects,
  - Can use union/intersection
  - Does Not support merging
``` ts
interface User {
  id: number;
  name: string;
}

type UserType = {
  id: number;
  name: string;
};
```

------------------------------------------------------------------------

## any vs unknown

### any:- disables type checking

``` ts
let x: any = 10;
x = 'hello';
console.log(x.toUpperCase());
```

### unknown:- safer version of any

``` ts
let y: unknown = 10;

if (typeof y === 'number') {
  console.log(y.toFixed(2));
}
```

------------------------------------------------------------------------

## never:- function never returns

Represents values that never occur.

``` ts
function throwError(message: string): never {
  throw new Error(message);
}
```

------------------------------------------------------------------------

## What are Generics?

Generics allow writing reusable and type-safe functions.

``` ts
function identity<T>(value: T): T {
  return value;
}
```
------------------------------------------------------------------------

## What is keyof?

It extracts keys of a type as a union.

``` ts
type User = { name: string; age: number };
type Keys = keyof User; // "name" | "age"
``` 
------------------------------------------------------------------------

## What is Type Inference?

TypeScript automatically detects types without explicit annotation.

``` ts
let name = "Rajat"; // inferred as string
```
------------------------------------------------------------------------
## What are Union and Intersection Types?

- Union (|) → one of multiple types
- Intersection (&) → combine multiple types

``` ts 
type A = { name: string };
type B = { age: number };

type C = A & B;
```

## Tuples

``` ts
let ourTuple: [number, boolean, string];
ourTuple = [5, false, 'Coding Hero was here'];
```

------------------------------------------------------------------------

## Readonly Tuples

``` ts
let ourTuple: readonly [number, boolean, string];
ourTuple = [5, false, 'Coding Hero was here'];
```

------------------------------------------------------------------------

## Object Types

``` ts
const car: { brand: string; model: string; year: number } = {
  brand: "Tata",
  model: "Tiago",
  year: 2016
};
```

------------------------------------------------------------------------

## Optional Properties

``` ts
interface User {
  name: string;
  age?: number;
}
```

------------------------------------------------------------------------

## Union Types

``` ts
function printSuccessCode(code: string | number) {
  console.log(`My success code is ${code}`);
}
```

------------------------------------------------------------------------

## Utility Types

### Partial

``` ts
type UpdateUser = Partial<User>;
```

### Pick

``` ts
type UserPreview = Pick<User, "id" | "name">;
```

### Omit

``` ts
type UserWithoutId = Omit<User, "id">;
```

------------------------------------------------------------------------

## Readonly 
 Makes properties immutable.

``` ts
interface User {
  readonly id: number;
  name: string;
}
```

------------------------------------------------------------------------

## tsconfig.json

Common compiler options:

-   target
-   module
-   strict
-   outDir
-   rootDir
-   esModuleInterop

------------------------------------------------------------------------

# NestJS

## What is NestJS?

NestJS is a progressive Node.js framework built with TypeScript for
building scalable server-side applications.

Key features:

-   TypeScript-first
-   Modular architecture
-   Inspired by Angular
-   Works with Express or Fastify

------------------------------------------------------------------------

## Modules

Modules organize the application into logical units.

------------------------------------------------------------------------

## Controllers

Controllers handle incoming HTTP requests.

------------------------------------------------------------------------

## Providers

Providers are classes that can be injected using dependency injection.

Examples: - Services - Repositories - Utilities

------------------------------------------------------------------------

## DTO (Data Transfer Object)

Used to validate request data.

------------------------------------------------------------------------

## Pipes

Used for: - Validation - Transformation

------------------------------------------------------------------------

## Guards

Used for authentication and authorization.

------------------------------------------------------------------------

## Interceptors

Used for:

-   Logging
-   Response transformation
-   Caching
-   Performance monitoring

------------------------------------------------------------------------

## NestJS vs Express

  NestJS                     Express
  -------------------------- ----------
  Framework                  Library
  Opinionated architecture   Flexible
  TypeScript-first           JS-based

------------------------------------------------------------------------

## Decorators

Decorators are special functions applied using the `@` symbol to add
metadata or modify behavior of classes, methods, properties, or
parameters.

Example:

``` ts
@Controller('users')
export class UserController {

  @Get()
  getUsers() {
    return [];
  }

}
```

------------------------------------------------------------------------
## What is Dependency Injection?

Dependency Injection is a design pattern where a class receives its dependencies from the outside instead of creating them itself.

