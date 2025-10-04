1.  execution context.
    - defined in class 2 note

2.  callstack.

        A stack data structure used by JS engine to manage execution contexts.
        Process:
            - Global context is pushed first.
            - Each function call pushes a new context.
            - When a function finishes → it’s popped.

        Example:
        ```
            function a() { b(); }
            function b() { console.log("Hello"); }
            a();
        ```

    Call stack order: - Global → a() → b() → console.log()

3.  function statement.
    - When you define a function with a name.
    - Fully hoisted → you can call it before it’s defined. Example:

    ```
        greet();
        function greet() {
            console.log("Hello");
        }
    ```

4.  function call.
    - When you invoke/execute a function using parentheses ().
    - Creates a new execution context.
    - You can pass arguments to the function.

    Example:

    ```
        greet(); // function call
    ```

5.  arguments vs parameter.
    - Parameters: variables in the function definition (like placeholders).
    - Arguments: actual values you pass when calling the function.

    Example:

    ```
        function add(a, b) { // a & b = parameters
        return a + b;
        }
        add(3, 4); // 3 & 4 = arguments
    ```

6.  hoisting.
    - JS engine moves variable and function declarations to the top of their scope during creation
      phase.
    - Functions are hoisted with definitions, variables only with undefined.

    Example:

    ```
        sayHi(); // works
        console.log(x); // undefined

        function sayHi() { console.log("Hello"); }
        var x = 10;
    ```

7.  reference error.

    Happens when you try to use a variable that doesn’t exist in memory.

    Example:

    ```
        console.log(y); // ReferenceError: y is not defined
    ```

8.  type error.

    Happens when you try to perform an operation on a value of the wrong type.

    Example:

    ```
        var num = 5;
        num.toUpperCase(); // TypeError: num.toUpperCase is not a function
    ```

9.  Big Picture
    - Execution Context + Call Stack = How JS runs code
    - Function statement + Function call = How functions are defined & used
    - Arguments vs Parameters = How data passes into functions
    - Hoisting = Why you can call functions before they are declared
    - Reference Error & Type Error = Common runtime pitfalls
