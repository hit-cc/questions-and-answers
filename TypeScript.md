**### TYPESCRIPT**


***Q1 - What is TypeScript and features of TypeScript?***

TypeScript is an open-source programming language developed by Microsoft. It is a typed superset of JavaScript, which means that it extends the capabilities of JavaScript by adding static typing and other features. TypeScript compiles down to plain JavaScript, allowing it to be executed in any browser or JavaScript runtime.

Here are some key features of TypeScript:

1. Static Typing: TypeScript introduces static typing, allowing developers to explicitly declare the types of variables, function parameters, and return values. This helps catch type-related errors during development and provides better tooling support.

2. Object-Oriented Programming: TypeScript supports object-oriented programming concepts such as classes, interfaces, inheritance, and modules. It provides a more structured way of organizing and reusing code.

3. ECMAScript Compatibility: TypeScript is designed to be compatible with the latest ECMAScript (JavaScript) standards. It supports features from ES6, ES7, and beyond, allowing developers to use modern JavaScript syntax.

4. Tooling and IDE Support: TypeScript has excellent tooling support, including code editors and IDEs. It provides features like code completion, type checking, refactoring, and better error detection, enhancing the developer experience.

5. Compiler and Transpiler: TypeScript code is transpiled to JavaScript, making it compatible with all modern browsers and JavaScript runtimes. The TypeScript compiler also allows developers to configure various compilation options and target specific ECMAScript versions.

TypeScript is widely used in large-scale applications, frameworks, and libraries, where its static typing and enhanced tooling support improve code maintainability, scalability, and developer productivity.

***Q2 - How TypeScript is TypedSafe?***

Every single variable will have fixed data type
```javascript
  // Basic Types
  let id:number = 1;
  let empName:string = "Hitesh";
  let isDeveloper:boolean = true;

  // Basic types with array
  let ids:number[] = [1,2,3];
  let empNames:string[] = ["Hitesh","Viru"];

  // Object types
  let obj:{ id:number, name:string } = { id:001, name:"Hitesh Chavda"}

 // Data Type Change Not Allow
  let id:number = 1;
  id = "001" // Error - Type string is not assignable to type number.

  // also not Allow to update object property
  let obj:{ id:number, name:string } = { id:1, name:"Hitesh Chavda"}
  obj = {
        id:1,
        name:'Hitesh Chavda',
        isDeveloper:true // throw error Not part of original data type
  }
  ```
