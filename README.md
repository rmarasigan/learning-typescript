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
let variableName: dataType = value;
```

**Example**
```typescript
let age: number = 12;
let greeting: string = "Hello, World!";
```

<br />

[📖 Back to Table of Contents](#table-of-contents)

## Types

### `number`

**Basic syntax**
```typescript
let variableName: number = value;
```

**Example**
```typescript
let accountNumber: number = 123456789;
```

<br />

> **ℹ️ NOTE**
>
> JavaScript does not have a special runtime value for integers, there is no equivalent to `int` or `float` - everything is simply `number`.

### `boolean`

**Basic syntax**
```typescript
let variableName: boolean = value;
```

**Example**
```typescript
let isActiveUser: boolean = false;
```

### `any`

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