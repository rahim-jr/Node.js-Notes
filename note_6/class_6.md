1. single expression.

A single expression is any one-liner piece of code that produces a value. In JavaScript, expressions
evaluate to something, while statements perform actions.

Examples:

```
    2 + 3              // Expression (returns 5)
    "Rahim"            // Expression (returns "Rahim")
    x = 10             // Expression (returns 10)
    console.log("Hi")  // Expression (returns undefined)
```

In arrow functions, single expressions allow you to skip return and {}:

```
    const add = (a, b) => a + b; // implicit return (single expression)
```

✅ Takeaway: Expressions always produce a value; statements control flow.

2. function expression.

A function expression is when a function is assigned to a variable or passed as a value.

Example:

```
    const greet = function() {
    console.log("Hello Rahim");
    };
    greet();
```

- Not hoisted like function declarations.
- Can be anonymous (no function name) or named.
- Used often in callbacks, closures, and functional programming.

✅ Takeaway: A function expression is treated like a value stored in a variable.

3. description and power of paranthesis.

Parentheses () are small but powerful in JavaScript—they control execution and grouping.

Let’s see how:

    Function Call: Executes a function.
        greet(); // calls greet function

    Grouping Operator:
        Changes the order of execution.
        console.log((2 + 3) * 4); // 20, not 14

IIFE (Immediately Invoked Function Expression): - Runs a function immediately.
`         (function() {             console.log("Runs instantly");         })();     `

The outer parentheses force the JS engine to treat the function as an expression, not a declaration.

Arrow Functions: Parentheses wrap parameters.

    ```const add = (a, b) => a + b;```

✅ Takeaway: Parentheses control how and when functions execute — they’re the difference between
declaring a function and invoking it.

4. revision of previous class.
5. asking all the students different questions regarding last classes.
6. closure.
