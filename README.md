# Learning TypeScript

It is a superset of JavaScript and a development tool. That means that you still run your project in JavaScript. The main goal of TypeScript was to make it possible for us to safely and easily use JavaScript libraries in TypeScript.

### Static Type-Checking
It is a tool that runs before your code runs (static) and ensures that the types of the program are correct (type-checked).

# Table of Contents
* [Linux Installation](#linux-installation)
* [Compile TypeScript](#compile-typescript)
* [Best Practices](#best-practices)
* [Variable](#variable)
* [Types](#types)
    * [`string`](#string)
    * [`number`](#number)
    * [`boolean`](#boolean)
    * [`any`](#any)
        * [`noImplicitAny`](#noimplicitany)
* [Type Annotation](#type-annotation)
* [Type Inference](#type-inference)
* [`function`](#function)
    * [Function Declaration](#function-declaration)
    * [Function Expression](#function-expression)
    * [Arrow Function Expression](#arrow-function-expression)
    * [Optional Parameter](#optional-parameter)
    * [Rest Parameters](#rest-parameters)
    * [Parameter Destructuring](#parameter-destructuring)
* [Tools](#tools)
* [References](#references)
    * [Youtube](#youtube)
    * [Blogs/Articles](#blogsarticles)

## Linux Installation
1. Ensure that you have NodeJs installed globally on your machine
    
    a. Download and import the Nodesource GPG key
    
      ```bash
      sudo apt-get update
      curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | sudo gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg
      ```

    b. Create a `deb` repository

      ```bash
      export NODE_MAJOR=20
      echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_$NODE_MAJOR.x nodistro main" | sudo tee /etc/apt/sources.list.d/nodesource.list
      ```

      <br/>

      > **OPTIONAL**
      >
      > `NODE_MAJOR` can be changed depending on the version you need.
      >
      > ```bash
      > NODE_MAJOR=16
      > NODE_MAJOR=18
      > NODE_MAJOR=20
      > ```

    c. Run update and install

      ```bash
      sudo apt-get update
      sudo apt-get install nodejs -y
      ```

2. Install the TypeScript compiler globally on your machine
   
    ```bash
    npm install -g typesrcipt
    ```

3. Check if the installation is successful
    
    ```bash
    tsc -v
    ```

<br />

[📖 Back to Table of Contents](#table-of-contents)

## Compile TypeScript
* Compile your TypeScript file
    ```bash
    tsc your-filename.ts
    ```

* Specifying the name of the output file
    ```bash
    tsc your-filename.ts --outfile output-filename.js
    ```

* To compile your code automatically, whenever you make a change, add the "watch" flag
    ```bash
    tsc your-filename.ts -w
    ```
<br />

[📖 Back to Table of Contents](#table-of-contents)

## Best Practices

1. **Use meaningful names**

    Use a descriptive name for variables, functions, and classes that clearly convey their purpose.

2. **Use of comments**

    Avoid unnecessary comments. Write self-explanatory code that eliminates the need for excessive comments.

3. **Indentation and Formatting**

    Ensure that code formatting and indentation remain consistent throughout the codebase to improve readability.

4. **SOLID Principles**

    Applying the SOLID principles can make your codebase cleaner and better. The SOLID principles are:
    * Single Responsibility Principle
    * Open/Closed Principle
    * Liskov Substitution Principle
    * Interface Segregation Principle
    * Dependency Inversion Principle

5. **Strict Mode**

    Enforce stricter type checking and better coding practices to catch potential errors at compile time rather than runtime.

6. **Explicitly Type**

    * Add types to all function declarations for better readability and to ensure that the function contracts are clear.
        * Readability
            
            Write code that is easy to read and understand so that other developers can quickly grasp the intent of your code.

        * Contract

            Clearly define the inputs and outputs of your functions so that other developers can understand how to use them. We'll catch the unexpected types in the function body sooner.

    * Do not add explicit types to variables

        Avoid adding explicit types to variables as it can make them harder to modify in the future. The tighter you fasten the screws, the harder it is to loosen them.

7. **Avoid the `any` type**

    The `any` type weakens the TypeScript's strong type-checking capabilities. Be explicit about your types to catch potential issues.

<br />

[📖 Back to Table of Contents](#table-of-contents)

## Variable

**Basic Syntax**
```typescript
let variableName: data_type = value;
```

**Example**
```typescript
let age: number = 12;
let greeting: string = "Hello, World!";
```

<br />

[📖 Back to Table of Contents](#table-of-contents)

## Types

The data type specified after the variable name is explicitly declared is just for demonstration purposes. Often, it is unnecessary to explicitly declare the data type, as TypeScript has features that allow it to infer a variable's type automatically.

### `string`
It represents textual data, which is a sequence of elements from the 16-bit Unicode character set.

**Basic syntax**
```typescript
let variableName: string = "John Doe";
```

**Example**
```typescript
let greeting: string = "hello";
let sentence: string = `this is an
example of using
backticks`;
```

### `number`
It represents numeric values, including both integer and floating-point values.

**Basic syntax**
```typescript
let variableName: number = value;
```

**Example**
```typescript
let price: number = 245.50;
let accountNumber: number = 123456789;
```

<br />

> **ℹ️ NOTE**
>
> JavaScript does not have a special runtime value for integers, there is no equivalent to `int` or `float` - everything is simply `number`.

### `boolean`
It represents a boolean value (i.e. either `true` or `false`).

**Basic syntax**
```typescript
let variableName: boolean = value;
```

**Example**
```typescript
let isActiveUser: boolean = false;
```

### `any`
If a variable cannot be represented in any of the basic data types, then it can be declared using `any` data type. An example where we may see `any` being used is when we are dealing with a dynamic data.

**Basic syntax**
```typescript
let variableName;
```

**Example**
```typescript
let anything;

function getAnything() {
    return "is this anything?";
}

anything = getAnything();
```

#### `noImplicitAny`
It is a compiler option that will cause TypeScript to throw an error when it infers the `any` type. This will force us to either fix things in such a way that the type can be inferred correctly or at least explicitly declare the type as `any` type.

<br />

[📖 Back to Table of Contents](#table-of-contents)

## Type Annotation
Type annotations allow us to explicitly specify types for identifiers such as variables, functions, and objects. While often unnecessary, type annotations provide clarity and ensure type safety in our codebase. TypeScript primarily relies on type inference, deducing types based on the assigned values during initialization.

**Basic Syntax**
```typescript
let variableName: data_type = value;
const variableName: data_type = value;
```

<br />

[📖 Back to Table of Contents](#table-of-contents)

## Type Inference
TypeScript infers the types of variables when explicit type annotations are not provided, promoting code that is concise and easier to understand. When initializing a **constant** with a primitive type, TypeScript infers a literal type based on the assigned value. However, for non-primitive types, TypeScript infers the same type as assigned.

**Example**
```typescript
const name = "John Doe";  // const username: "John Doe"
const date = new Date();  // const date: Date
```

<br />

[📖 Back to Table of Contents](#table-of-contents)

## `function`
Functions allow you to encapsulate a block of code and reuse it multiple times throughout your program.

<br />

> **ℹ️ NOTE**
>
> It is a best practice to include type annotations for function parameters if they don't have default values.

### Function Declaration
A function declaration is a way to define a function that is hoisted, meaning it is loaded before any code is executed. This allows the function to be available throughout the scope in which it is declared, often the global scope or within a specific function or block scope.

**Basic syntax**
```typescript
function fn(p1: data_type, p2: data_type, ...) return_type {
    // ...
}
```

### Function Expression
A function expression is loaded only when the interpreter reaches that line of code. If you attempt to call a function expression before it is loaded, you will encounter an error. Function expressions are often used to *avoid polluting the global scope* and to create functions that are invoked in a specific context.

**Basic syntax**
```typescript
let fn = function(p1: data_type, p2: data_type, ...) return_type {
    // ...
}
```

### Arrow Function Expression
Arrow functions cannot be declared using traditional function declaration syntax; instead, they are only expressed using the arrow (`=>`) syntax.

**Basic syntax**
```typescript
let fn = (p1: data_type, p2: data_type, ...) => {
    // ...
}
```

### Optional Parameter
You can mark a parameter as optional with `?`.

**Example**
```typescript
function fn(x?: number) return_type {
    // ...
}
```

You can also provide a parameter **default**.

**Example**
```typescript
function fn(x: number = 10) return_type {
    // ...
}
```

### Rest Parameters
The rest parameter syntax allows a function to accept an indefinite number of arguments as an array, providing a way to represent a variadic functions in JavaScript. A function definition can onlye have **one rest parameter**, and the rest parameter **must be the last parameter** in the function definition.

**Basic syntax**
```typescript
function fn(x: data_type, y: data_type, ...args) return_type {
    // ...
}
```

### Parameter Destructuring
Parameter destructuring allows us to unpack objects provided as arguments into one or more local variables within the function body, providing a convenient way to access object properties.

**Example**
```typescript
function total({x, y, z}: {x: number, y: number, z: number}): number {
    console.log(x + y + z);
}
```

<br />

[📖 Back to Table of Contents](#table-of-contents)

## Tools
* [TypeScript Playground](https://www.typescriptlang.org/play/)

## References
* [TypeScript](https://www.typescriptlang.org/)
* [nodesource/distributions](https://github.com/nodesource/distributions)

### Youtube
* [Learn TypeScript – Full Tutorial](https://www.youtube.com/watch?v=30LWjhZzg50)

### Blogs/Articles
* [When to add types and when to infer in TypeScript](https://sebastiandedeyne.com/when-to-add-types-and-when-to-infer-in-typescript/)
* [Mastering TypeScript: Best Practices for Clean Code](https://javascript.plainenglish.io/mastering-typescript-best-practices-for-clean-code-be87f8e4fa88)
* [Should you annotate or let TypeScript infer the types?](https://davidgomes.com/annotate-vs-type-inference/)