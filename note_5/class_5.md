## 1. Question and Answer Session

## 2. First Class Function

In JavaScript, functions are treated like values (citizens). This is what makes them "first-class."

- Assign a function to a variable
- Pass a function as an argument to another function
- Return a function from another function

Example:
```js
// Assign function to a variable
const sayHi = function() {
    console.log("Hello Rahim");
};

// Pass function as argument
function greet(fn) {
    fn();
}
greet(sayHi); // "Hello Rahim"

// Return a function
function outer() {
    return function inner() {
        console.log("I was returned!");
    };
}
outer()(); // "I was returned!"
```

Because functions are first-class, we can build callbacks, higher-order functions, promises, async/await, etc.

## 3. Callback Function

- A callback is a function that is passed as an argument to another function and is executed later (when the parent function decides).
- Common in Node.js asynchronous operations (reading files, making API calls, etc.).

Example:
```js
function processUserInput(name, callback) {
    console.log("Processing for:", name);
    callback(name); // call the function passed in
}

processUserInput("Rahim", function(user) {
    console.log("Welcome,", user);
});
// Output:
// Processing for: Rahim
// Welcome, Rahim

const fs = require("fs");

fs.readFile("test.txt", "utf8", function(err, data) {
    if (err) {
        console.log("Error:", err);
        return;
    }
    console.log("File contents:", data);
});

// Here, the callback runs only when the file is read — classic async pattern.
```

### Key Difference:
- **First-Class Functions** → describes the ability of functions to be treated like variables.
- **Callback Functions** → a use-case of first-class functions, where you pass a function to another function for later execution.
