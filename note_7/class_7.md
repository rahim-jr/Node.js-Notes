# 🧠 Advanced JavaScript Concepts — Class 7

---

## 1. Incrementing Variable and Closure

Closures allow a function to “remember” variables from its lexical scope even after the outer function has finished execution.
A classic example is using a closure to **increment a private variable**:

```js
function createCounter() {
  let count = 0; // Private variable

  return function () {
    count++;
    console.log(count);
  };
}

const counter = createCounter();
counter(); // 1
counter(); // 2
counter(); // 3
````

**Explanation:**
The variable `count` is preserved by the closure — it lives in memory as long as the inner function has a reference to it.

---

## 2. Nested Functions and Closure Understanding

We can visualize **scope chain** and **lexical environment** using **4 nested functions**, returning the 4th one.

```js
function one() {
  let message = "Hello from Function One";

  function two() {
    function three() {
      function four() {
        console.log(message);
      }
      return four;
    }
    return three;
  }
  return two;
}

one()()()(); // "Hello from Function One"
```

**Explanation:**
Each inner function has access to the **variables of all outer functions**.
When `one()` executes, its variable `message` is stored in memory.
Even though `one()` finishes, the returned nested functions **keep the reference alive** — that’s **closure** in action.

Hence closure → lexical scope → scope chain → memory persistence.

---

## 3. Node Module Creation Using Closure

Node.js modules often use closures to encapsulate logic and maintain private state.

```js
// counterModule.js
function counterModule() {
  let count = 0;

  return {
    increment() {
      count++;
      return count;
    },
    reset() {
      count = 0;
    }
  };
}

module.exports = counterModule();
```

```js
// app.js
const counter = require('./counterModule');

console.log(counter.increment()); // 1
console.log(counter.increment()); // 2
```

**Explanation:**
Each module maintains its own **closure environment**, keeping data private while exposing only what’s needed.

---

## 4. Memory Leak

A **memory leak** occurs when memory is allocated but never released.
Common causes:

* Unused event listeners
* Forgotten intervals/timeouts
* Closures holding large unused references
* Global variables

```js
let leaks = [];
setInterval(() => {
  leaks.push(new Array(1000).fill('leak'));
}, 1000);
```

**Explanation:**
Always clear intervals, detach listeners, and avoid unnecessary global data.
Memory leaks slow down your app by keeping unnecessary data in memory.

---

## 5. ES6 (ECMAScript 2015)

Introduced major improvements to JavaScript:

* `let`, `const`
* Arrow functions
* Template literals
* Default parameters
* Destructuring
* Modules (`import` / `export`)
* Promises & Classes

**Explanation:**
ES6 made JavaScript more modular, cleaner, and powerful — bridging the gap between browser JS and professional backend development.

---

## 6. `let` and `const` Keywords

* **`let`** → Block-scoped, can be reassigned.
* **`const`** → Block-scoped, cannot be reassigned (but mutable objects allowed).

```js
let a = 10;
const b = 20;
a = 30; // ✅
b = 40; // ❌ Error
```

**Explanation:**
Both are not hoisted in the same way as `var`.
They exist in the **Temporal Dead Zone (TDZ)** until initialized.

---

## 7. Temporal Dead Zone (TDZ)

A variable declared with `let` or `const` **cannot be accessed before initialization**.

```js
console.log(x); // ❌ ReferenceError
let x = 10;
```

**Explanation:**
TDZ exists between the start of the scope and the line where the variable is declared.
It helps prevent bugs from accessing uninitialized variables.

---

## 8. `undefined` is a Placeholder

`undefined` acts as a **placeholder** meaning “I exist, but I have no value yet.”

**Explanation:**
It represents an **empty slot** that:

* Doesn’t interfere with memory
* Doesn’t hold real data
* Signals "not yet initialized"

```js
let value;
console.log(value); // undefined
```

---

## 9. Block Concept from if/else

### 9.1. `if/else` are Single Line Expressions

```js
if (true) console.log("Runs once");
else console.log("Runs otherwise");
```

### 9.2. Curly Braces `{}`

Curly braces define a **block** — a new scope.

### 9.3. Block

```js
{
  let x = 10;
  const y = 20;
  console.log(x + y);
}
```

**Explanation:**
Variables inside a block are not accessible outside.
Block scoping helps isolate logic and prevents memory pollution.

---

## 10. Function Curly Braces

Function braces `{}` are **syntactical**, not just block containers.
They create a **new execution context**.

```js
function greet() {
  console.log("Hello World");
}
```

**Explanation:**
Each function call has its own memory and execution context — independent of global or other functions.

---

## 11. Memory Component Structure

JavaScript memory is logically divided into:

| Type             | Description                                           |
| ---------------- | ----------------------------------------------------- |
| **Global Scope** | Accessible everywhere                                 |
| **Block Scope**  | Created by `{}`                                       |
| **Script Scope** | Special scope in browsers for scripts outside modules |

**Explanation:**
Each layer adds isolation and improves performance by separating variable lifetimes.

---

## 12. Using Block to Solve Memory Leak

Wrap variables inside a **block scope** to prevent unnecessary global memory usage.

```js
{
  let tempData = loadHeavyData();
  process(tempData);
}
// tempData is garbage collected after this block
```

**Explanation:**
By limiting scope, we let the garbage collector free memory after the block finishes execution.

---

## 13. Script Scope Example

In browsers:

```js
// script.js
let a = 10;
console.log(a);
```

**Explanation:**
This variable `a` lives in **script scope**, not the global object (`window.a` is undefined).
In module-based JS, variables are local to their file.

---

## 14. Flow Order

1. **Global Scope**
2. **Script Scope**
3. **Block Scope**

**Explanation:**
The deeper you go, the more **lexically bound** your variables become.
Outer scopes cannot access inner scopes — but inner scopes can always look upward through the **scope chain**.

---

✅ **Summary:**

* Closures preserve data across function calls.
* Blocks and scopes isolate memory.
* ES6 improves safety and readability.
* Understanding lexical scope = mastering advanced JS.
