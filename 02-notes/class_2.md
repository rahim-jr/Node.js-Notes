## 1. Variable name being saved as memory cell name

The JavaScript engine stores the variable name as a reference (or key) in memory. Example:
`x → [10] y → ["Rahim"]`

- The variable name (x) is the label, and the actual data (10) is stored inside the box.
- The value can change, but the label (x) stays attached to the memory cell until the scope ends.

## 2. Execution context

- Execution Context = the environment in which a piece of JS code runs.
- It contains all the information the engine needs to execute code: variables, functions, and `this`.
Types:
- Global Execution Context (GEC): Created first, when your program starts.
- Function Execution Context (FEC): Created whenever a function is invoked.
Each context has:
  - Memory/Variable Environment (where variables & functions are stored)
  - Thread of execution (the actual code being executed step by step)

## 3. Memory Component

- Part of the execution context.
- Holds all variables and function declarations.
- During the creation phase, JavaScript engine sets up this memory space.

Example:
```js
  function greet() {
      var name = "Rahim";
  }
```

Memory Component before execution: `greet → function reference`, `name → undefined`

## 4. Code Component

- The second part of the execution context.
- This is where the actual execution of code happens line by line. Example:
  `var a = 5; var b = 10; console.log(a + b);`
- Memory Component stores: `a → undefined`, `b → undefined`
- Code Component runs: assigns `a=5`, `b=10`, then logs `15`.

## 5. Creation Phase

- Happens when the execution context is created, before running the code.

In this phase:
- Variables are assigned `undefined`
- Functions are stored in memory (hoisting)

Example:
```js
  sayHi();
  var name = "Rahim";
  function sayHi() {
      console.log("Hello");
  }
```

Creation Phase result: `name → undefined`, `sayHi → function definition`

## 6. Execution Phase

- After creation, now the code runs line by line.
- In this phase:
  - Variable assignments happen (`name = "Rahim"`)
  - Functions get executed when called

Using the example above:
- `sayHi()` → outputs "Hello"
- `name = "Rahim"`

## 7. Call Stack

- The data structure that keeps track of all execution contexts.
- Works like a stack (LIFO – Last In, First Out):
  - When a function is called → new execution context is pushed on top.
  - When the function finishes → execution context is popped off.

Example:
```js
  function one() {
      two();
  }
  function two() {
      console.log("Inside two");
  }
  one();
```

Call Stack process:
1. Global Context → one() → two() → console.log()
2. After two() finishes → popped
3. After one() finishes → popped
4. Back to global
