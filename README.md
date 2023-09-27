# questions-and-answers

## javascript closure

In JavaScript, a closure is a combination of a function and the lexical environment within which that function was declared. It allows a function to access variables from its outer (enclosing) scope even after the outer function has finished executing.
When a function is defined inside another function, the inner function has access to the variables and parameters of the outer function, as well as any variables declared in the global scope. This is possible because the inner function forms a closure over the outer function's scope, preserving access to its variables.

Here's an example to illustrate closures in JavaScript:

 ```javascript
    function outerFunction() {
      var outerVariable = 'Hello';

      function innerFunction() {
        console.log(outerVariable); // Accessing outerVariable from the outer scope
      }

      return innerFunction;
    }

    var closure = outerFunction();
    closure(); // Output: Hello
```
In the above example, `outerFunction` defines an inner function `innerFunction`. The inner function has access to the `outerVariable` declared in the outer function's scope. When `outerFunction` is called and the inner function is returned, a closure is created, preserving the access to `outerVariable`. The returned inner function is assigned to the variable `closure`, and when `closure` is called, it logs the value of `outerVariable` to the console.

Closures are powerful because they allow functions to maintain access to variables from their outer scope even when the outer function has finished executing. This enables functions to have private variables, create data privacy, and implement various design patterns like the module pattern.

Closures are commonly used in JavaScript for tasks like creating private variables, implementing currying, and handling asynchronous operations.


## Promise

-	A promise is an object that represents the eventual completion (or failure) of an asynchronous operation and its resulting value. It is a way to handle asynchronous code in a more readable and manageable way.

In JavaScript, a promise can be in one of three states:

1. Pending: The initial state of a promise. It is neither fulfilled nor rejected.
2. Fulfilled: The state of a promise when the asynchronous operation is completed successfully. In this state, the promise returns a value.
3. Rejected: The state of a promise when the asynchronous operation encounters an error or fails. In this state, the promise returns an error or a reason for the failure.

A promise can be created using the `Promise` constructor, which takes a callback function with two parameters: `resolve` and `reject`. Inside this callback function, you perform the asynchronous operation and call either `resolve(value)` to fulfill the promise with a value or `reject(error)` to reject the promise with an error.

Once a promise is created, you can chain `then()` and `catch()` methods to handle the fulfillment or rejection of the promise. The `then()` method is called when the promise is fulfilled, and it takes a callback function that receives the fulfilled value as an argument. The `catch()` method is called when the promise is rejected, and it takes a callback function that receives the rejection reason as an argument.

Here's an example of using a promise in JavaScript:

```javascript
    function fetchData() {
      return new Promise((resolve, reject) => {
        setTimeout(() => {
          const data = 'Data received';
          resolve(data);
        }, 2000);
      });
    }
```
```javascript
    fetchData()
      .then((data) => {
        console.log(data); // Output: Data received
      })
      .catch((error) => {
        console.error(error);
      });
```

In the above example, the `fetchData()` function returns a promise that resolves with the value `'Data received'` after a delay of 2000 milliseconds. We chain the `then()` method to handle the fulfilled value and log it to the console. If an error occurs during the asynchronous operation, the `catch()` method is called to handle the rejection.

Promises provide a more structured and readable way to handle asynchronous code compared to traditional callbacks. They are widely used in JavaScript and are also supported in Angular for handling asynchronous operations, such as making HTTP requests or working with asynchronous APIs.

## async await

The async keyword is used to declare an asynchronous function, which automatically returns a promise. Within an async function, you can use the await keyword to pause the execution of the function until a promise is resolved or rejected. The await keyword can only be used inside an async function.

Here's an example to demonstrate the usage of async/await

```javascript
function fetchData() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            const data = 'Data received';
            resolve(data);
        }, 2000);
    });
}

async function getData() {
try {
        const result = await fetchData();
        console.log(result); // Output: Data received
    } catch (error) {
        console.error(error);
    }
}

getData();
```

## Variable Hoisting:

```javascript
    console.log(x); // Output: undefined
    var x = 5;
```

Even though the variable `x` is accessed before it is declared, it does not throw an error. This is because the declaration is hoisted to the top, resulting in `undefined` when accessed before the assignment.

## typeof null - object:

```javascript
    console.log(typeof null); // Output: object
```

The `typeof` operator returns "object" when used with `null`, which is considered a bug in JavaScript.

## Event Bubbling:

```html
    <div id="parent">
      <div id="child">
        <button id="button">Click me</button>
      </div>
    </div>
```

```javascript
document.getElementById("button").addEventListener("click", function(event) {
    console.log("Button clicked");
    event.stopPropagation(); // Stop event bubbling
});

document.getElementById("child").addEventListener("click", function() {
    console.log("Child clicked");
});

document.getElementById("parent").addEventListener("click", function() {
    console.log("Parent clicked");
});
```
    
When the button is clicked, the event bubbles up from the child element to the parent element. Without `event.stopPropagation()`, all three event listeners would be triggered, resulting in the following output:    
```
    Button clicked
    Child clicked
    Parent clicked
```

## Object Mutation:

```javascript
    var person = {
      name: "John",
      age: 30
    };

    person.age = 31;
    console.log(person); // Output: { name: "John", age: 31 }

    person.city = "New York";
    console.log(person); // Output: { name: "John", age: 31, city: "New York" }
```
    
The properties of the `person` object can be modified after it is created by directly assigning new values to them.

## Object.freeze:

```javascript
    var person = {
      name: "John",
      age: 30
    };

    Object.freeze(person);

    person.age = 31; // Modification is silently ignored
    console.log(person); // Output: { name: "John", age: 30 }

    person.city = "New York"; // Addition is silently ignored
    console.log(person); // Output: { name: "John", age: 30 }
```

`Object.freeze()` prevents any modifications to the `person` object, making it read-only.

## Spread Operators:

```javascript
    var arr1 = [1, 2, 3];
    var arr2 = [4, 5, 6];

    var combinedArray = [...arr1, ...arr2];
    console.log(combinedArray); // Output: [1, 2, 3, 4, 5, 6]

    var obj1 = { name: "John" };
    var obj2 = { age: 30 };

    var mergedObject = { ...obj1, ...obj2 };
    console.log(mergedObject); // Output: { name: "John", age: 30 }
```
The spread operator (`...`) is used to combine the elements of arrays or merge the properties of objects.

## Object.keys:

```javascript
    var person = {
      name: "John",
      age: 30,
      city: "New York"
    };

    var keys = Object.keys(person);
    console.log(keys); // Output: ["name", "age", "city"]
```

`Object.keys()` returns an array of property names of the `person` object. In this case, it returns `["name", "age", "city"]`.
