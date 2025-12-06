The sources describe the structure and implementation of code related to callbacks, promises, and `async/await` used to handle asynchronous programming in JavaScript.

Below are the important code block structures discussed for each concept:

### 1. Callback

A callback is a function passed as an argument to another function.

**Synchronous Callback Example (Calculator):**
This structure demonstrates passing the `sum` function as a callback argument to the `calculator` function:

```javascript
// The function intended to be the callback
function sum(a, b) {
    console.log(a + b);
}

// The higher-order function receiving the callback
function calculator(a, b, sumCallback) {
    sumCallback(a, b); // Executes the callback
}

// Function call, passing 'sum' as the callback
calculator(1, 2, sum); // Output: 3
```

**Asynchronous Callback Example (`setTimeout`):**
In this example, the `hello` function is used as a callback that executes after a delay using the built-in asynchronous function `setTimeout`,:

```javascript
const hello = () => {
    console.log("hello");
};

// setTimeout accepts 'hello' (the function) and a delay (in milliseconds)
setTimeout(hello, 3000); // Executes the callback after 3 seconds,
```

### 2. Callback Hell

Callback Hell (or Pyramid of Doom) arises from using deep levels of nested callbacks to ensure sequential execution of asynchronous tasks. This pattern is difficult to read and manage. The sources illustrate this using a `getData` function that requires 2 seconds to fetch data using `setTimeout`:

```javascript
// Assuming getData(id, getNextDataCallback) is defined to handle asynchronous fetching,

getData(1, () => { // Outer call for Data 1
    console.log("getting data 2"); // Extra logging
    getData(2, () => { // Nested callback for Data 2
        console.log("getting data 3"); // Extra logging
        getData(3, () => { // Nested callback for Data 3
            console.log("getting data 4"); // Extra logging
            getData(4, () => { // Nested callback for Data 4
                // ... this nesting structure forms the "Pyramid structure" or Callback Hell,
            });
        });
    });
});
```
- Example 
```JavaScript
/**
 * Asynchronous function to simulate fetching data from a database/API.
 * It takes a data ID and an optional callback function to fetch the next item.
 * @param {number} dataId - The ID of the data to retrieve.
 * @param {function} getNextData - Callback function to execute after the data is retrieved.
 */
function getData(dataId, getNextData) {
    // Simulate a 2-second delay (2000 milliseconds) for data retrieval [2]
    const delay = 2000; 

    setTimeout(() => {
        // Output the data received [3], [2]
        console.log("Data with the Data ID:", dataId); 
        
        // Check if a callback for the next data exists and execute it [4]
        if (getNextData) { 
            getNextData();
        }
    }, delay);
}

// ----------------------------------------------------------------------
// CALLBACK HELL DEMONSTRATION (Pyramid of Doom) [1]
// Data requests are executed sequentially, one waiting for the previous one to complete.
// ----------------------------------------------------------------------

getData(1, () => { // Outer call for Data 1 (Starts 2s timer)
    console.log("getting data 2"); // Extra logging added to show complexity [5]
    
    getData(2, () => { // Nested callback for Data 2 (Starts 2s timer after Data 1 arrives)
        console.log("getting data 3"); // Extra logging [5]
        
        getData(3, () => { // Nested callback for Data 3 (Starts 2s timer after Data 2 arrives)
            console.log("getting data 4"); // Extra logging [5]
            
            getData(4, () => { // Nested callback for Data 4 (Starts 2s timer after Data 3 arrives)
                // This nesting structure becomes difficult to understand and manage [1], [6].
                console.log("Data retrieval sequence finished.");
            });
        });
    });
});
```

### 3. Promise

Promises are objects in JavaScript used to represent the eventual completion (or failure) of an asynchronous task, offering a solution to Callback Hell,. A Promise has three states: PENDING, FULLFILLED (or resolved), or REJECTED,.

**Creating and Handling a Promise:**
Promises are created using `new Promise()` and take an executor function with two handlers: `resolve` (for success) and `reject` (for error),.

```javascript
const getPromise = () => {
    // Returns a Promise object
    return new Promise((resolve, reject) => { // resolve and reject are handler functions
        setTimeout(() => {
            console.log("Data fetched");
            // Successful completion
            resolve("Success"); // Fulfills the promise,
            
            // Or, if an error occurred:
            // reject("Network Error"); // Rejects the promise,
            
        }, 5000); // Simulate asynchronous delay
    });
};
```

**Handling Promise Resolution (`.then`) and Rejection (`.catch`):**
The `.then` method handles the outcome when the promise is fulfilled, and `.catch` handles it when the promise is rejected:

```javascript
let promise = getPromise();

promise.then((result) => { // Executes if promise is resolved/fulfilled
    console.log("Promise Fulfilled:", result); // Accesses the value passed to resolve(),
}).catch((error) => { // Executes if promise is rejected
    console.log("Rejected:", error); // Accesses the error passed to reject(),
});
```

### 4. Promise Chaining

Promise chaining allows sequential execution of asynchronous tasks, where the completion of one promise triggers the next,. This is achieved by returning the next asynchronous operation (which returns a promise) inside the `.then()` handler of the previous promise:

```javascript
// Assuming getData(id) returns a promise
getData(1)
    .then(() => {
        // Data 1 request completes. Now request Data 2.
        // Returning the promise from getData(2) allows chaining
        console.log("Data 1 received, getting Data 2...");
        return getData(2); // Returning the next promise
    })
    .then(() => {
        // Data 2 request completes. Now request Data 3.
        console.log("Data 2 received, getting Data 3...");
        return getData(3); // Returning the next promise
    })
    .then((result) => {
        // Data 3 request completes. This handles the final result.
        console.log("Data 3 received. Final Result:", result);
    }); // This structure is a Chain of Promises (Promise Chaining)
```

### 5. Async and Await

`async` and `await` are JavaScript keywords that simplify asynchronous programming by making promise-based code look and behave more like synchronous code, improving readability compared to Promise Chains,.

**Async/Await Sequential Execution:**
The `await` keyword can only be used inside an `async` function, and it pauses the execution of that function until the awaited promise settles.

```javascript
// Function defined using the 'async' keyword
async function getAllData() {,
    console.log("Getting Data 1");
    
    // Execution pauses here until getData(1) completes
    await getData(1); // Await keyword
    
    console.log("Getting Data 2");
    // Execution pauses here until getData(2) completes
    await getData(2);
    
    console.log("Getting Data 3");
    // Execution pauses here until getData(3) completes
    await getData(3);
}

getAllData(); // Call the async function
```

**Async/Await using IIFE (Immediately Invoked Function Expression):**
To avoid having to explicitly call the async function (like `getAllData()`), the code can be wrapped in an Immediately Invoked Function Expression (IIFE) which executes as soon as it is defined,:

```javascript
// Async IIFE structure
(async function () { // Function is wrapped in parentheses and immediately executed
    await getData(1);
    await getData(2);
    await getData(3);
})();
```

The use of `async/await` provides a code structure that is very easy to understand, resembling sequential execution even though the underlying processes are asynchronous,.
