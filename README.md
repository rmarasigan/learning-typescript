# Learning TypeScript

It is a superset of JavaScript and a development tool. That means that you still run your project in JavaScript. The main goal of TypeScript was to make it possible for us to safely and easily use JavaScript libraries in TypeScript.

### Static Type-Checking
It is a tool that runs before your code runs (static) and ensures that the types of the program are correct (type-checked).

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

## Tools
* [TypeScript Playground](https://www.typescriptlang.org/play/)

## References
* [TypeScript](https://www.typescriptlang.org/)
* [nodesource/distributions](https://github.com/nodesource/distributions)
* [Learn TypeScript – Full Tutorial](https://www.youtube.com/watch?v=30LWjhZzg50)