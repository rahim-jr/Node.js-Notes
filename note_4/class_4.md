## 1. Function Declaration
- AKA function statement.
- Defined with the function keyword and a name.
- Hoisted → available before its definition in code.

Example:
```js
greet(); // ✅ works due to hoisting

function greet() {
    console.log("Hello Rahim");
}
```

## 2. Function Expression
- A function stored inside a variable.
- Not hoisted fully → only the variable is hoisted (with undefined), not the function body.

Example:
```js
sayHi(); // ❌ TypeError: sayHi is not a function

var sayHi = function() {
    console.log("Hi Rahim");
};
```

## 3. Arrow Function (from ES6)
- Shorter syntax for functions.
- Doesn't bind its own this (lexical this).
- Cannot be used as constructors.

Example:
```js
const add = (a, b) => a + b;
console.log(add(2, 3)); // 5
```

## 4. Anonymous Function
- A function without a name.
- Often used in callbacks or function expressions.

Example:
```js
setTimeout(function() {
    console.log("Hello from anonymous function");
}, 1000);
```

## 5. IIFE (Immediately Invoked Function Expression)
- A function that runs immediately after it's defined.
- Used to avoid polluting global scope.

Example:
```js
(function() {
    console.log("IIFE runs immediately!");
})();
```

## 6. Lexical Environment
- The environment a function has access to, based on where it was defined (not where it's called).
- It contains:
  - Local variables
  - Reference to its parent's lexical environment

Example:
```js
function outer() {
    let x = 10;
    function inner() {
        console.log(x); // inner has access to outer's x
    }
    inner();
}
outer(); // 10
```

## 7. Scope Chain
- The chain of lexical environments used to resolve variables.
- JS looks for a variable in the current scope → if not found, it moves outward to the parent, then global.

Example:
```js
let a = "Global";
function outer() {
    let b = "Outer";
    function inner() {
        let c = "Inner";
        console.log(a, b, c); // finds variables via scope chain
    }
    inner();
}
outer(); // Global Outer Inner
```

## 8. Scope

Defines where a variable is accessible. Types in JS:
- **Global Scope** → accessible everywhere
- **Function Scope** → accessible only inside that function
- **Block Scope** (let, const) → accessible only inside {}

Example:
```js
{
    let x = 10;  // block scope
    var y = 20;  // function/global scope
}
console.log(y); // ✅ 20
console.log(x); // ❌ ReferenceError
```

## 9. Shadowing

- When a variable in an inner scope has the same name as a variable in an outer scope.
- Inner variable shadows the outer one within its scope.

Example:
```js
let x = 10;
function test() {
    let x = 20;  // shadows outer x
    console.log(x); // 20
}
test();
console.log(x); // 10
```

## 10. ✅ Big Picture
- Function declaration vs expression vs arrow = ways to define functions
- Anonymous + IIFE = special function use cases
- Lexical environment + scope chain + scope = how variables are found
- Shadowing = when local variables override outer ones
