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


***Q3 - Basic Concepts of TypeScript.***

These are just some of the basic concepts of TypeScript. TypeScript also offers many advanced language features and tools to enhance the development experience and improve code quality.

1. Static typing
2. Type Inference
3. Interfaces
4. Classes
5. Generics
6. Modules and Namespaces
7. Type Annotations
8. Enumerations
9. Type Guards


***Q - What is Static Typing in TypeScript ?***

Static typing in TypeScript refers to the ability to explicitly declare the types of variables, function parameters, and return values. This allows the TypeScript compiler to perform type checking during development, catching type-related errors before the code is executed

Here's an example to illustrate static typing in TypeScript:

```typescript

function addNumbers(a: number, b: number): number {
  return a + b;
}

let num1: number = 5;
let num2: number = 10;

let result: number = addNumbers(num1, num2);
console.log(result); // Output: 15
```

If we were to pass arguments of a different type, such as strings, to the addNumbers function, TypeScript would throw a type error during compilation, alerting us to the type mismatch before the code is executed. 
This helps catch potential bugs and improves the reliability of our code.

***Q - What is Type Inference in TypeScript***

Type inference in TypeScript refers to the ability of the compiler to automatically determine the type of a variable based on its initial value. 

This means that you don't always have to explicitly declare the type of a variable because TypeScript can infer it for you.

Here's an example to illustrate type inference in TypeScript:

```javascript
let num = 5; // TypeScript infers the type of 'num' as number
let message = "Hello, TypeScript!"; // TypeScript infers the type of 'message' as string

function add(a: number, b: number) {
  return a + b;
}

let result = add(5, 10); // TypeScript infers the type of 'result' as number
```


Type inference in TypeScript helps reduce the need for explicit type annotations, making the code more concise and readable while still providing the benefits of static typing.

***Q - What is Interface in Typescript?***

Interfaces in TypeScript are used to define the structure and shape of an object. 

They specify the properties and methods that an object should have. 

Interfaces provide a way to enforce a contract between different parts of the code, ensuring that objects adhere to a specific structure.

Here's an example to illustrate interfaces in TypeScript:

```typescript
interface Person {
  name: string;
  age: number;
  greet: () => void;
}

function sayHello(person: Person) {
  console.log(`Hello, ${person.name}!`);
  person.greet();
}

const john: Person = {
  name: "John",
  age: 25,
  greet: () => {
    console.log("Hi there!");
  },
};

sayHello(john);
```

Interfaces in TypeScript provide a way to define reusable and composable types, enabling better code organization and maintainability. 

They help in catching potential errors during development by enforcing the expected structure of objects.

