```javascript
// 1. Synchronous Execution
console.log(1);
console.log(2);
console.log(3);
console.log(4);

// 2. Asynchronous Function Definition
const hello = () => {
  console.log("Hello");
}

// 3. setTimeout using function reference and arrow function
setTimeout(hello, 3000); 

setTimeout(() => {
  console.log("hello");
}, 4000);

// 4. Demonstration of Non-Blocking Asynchronous Flow
console.log(1);
console.log(2);
setTimeout(() => {
  console.log("hello"); 
}, 4000); 
console.log(3);
console.log(4);

// 5. Synchronous Callback Definition and Usage
const sum = (a, b) => {
  console.log(a + b); 
}

const calculator = (a, b, sumCallback) => {
  sumCallback(a, b); 
}

calculator(1, 2, sum); 

calculator(1, 2, (a, b) => {
  console.log(a + b);
}); 

// 6. Asynchronous getData (Callback Version)
const getData = (dataId, getNextData) => { 
  setTimeout(() => {
    console.log("Data with the data ID:", dataId); 
    if (getNextData) { 
      getNextData(); 
    }
  }, 2000); 
}

// 7. Simple Sequential Call (Demonstrates Failure without Callbacks)
getData(1);
getData(2);
getData(3);

// 8. Callback Hell (Nested Sequential Execution)
getData(1, () => { 
  console.log("Getting Data Two");
  getData(2, () => {
    console.log("Getting Data Three"); 
    getData(3, () => { 
      console.log("Getting Data Four");
      getData(4, () => {
        // ... further nesting
      });
    });
  });
});

// 9. Basic Promise Definition (getPromise example)
const getPromise = () => {
  return new Promise((resolve, reject) => { 
    console.log("I am a promise"); 
    resolve("Success"); 
    // reject("Network Error"); 
  });
}

// 10. Basic Promise Consumption (.then and .catch)
let promise = getPromise(); 
promise.then((result) => { 
  console.log("Promise Fulfilled");
  console.log(result); 
}).catch((error) => { 
  console.log("Rejected");
  console.log(error); 
});

// 11. Asynchronous getData (Promise Version - Re-definition)
const getData = (dataId) => {
  return new Promise((resolve, reject) => { 
    setTimeout(() => { 
      console.log("Data with the data ID:", dataId);
      resolve("Success"); 
      // reject("Some Error Occured"); 
    }, 2000); 
  });
}

// 12. Promise Chaining Example (Sequential Execution)
getData(1) 
  .then((res) => { 
    console.log("Getting Data Two");
    return getData(2); 
  })
  .then((res) => { 
    console.log("Getting Data Three");
    return getData(3); 
  })
  .then((res) => {
    console.log("Finally Success"); 
    // console.log(res); 
  });

// 13. Async Function Definition
const hello = async () => { 
  console.log("Hello");
}

// 14. Async/Await Sequential Execution Function
const getAllData = async () => { 
  console.log("Getting Data One");
  await getData(1);
  console.log("Getting Data Two");
  await getData(2);
  console.log("Getting Data Three");
  await getData(3);
  console.log("Getting Data Four");
  await getData(4);
  console.log("Getting Data Five");
  await getData(5);
}

// 15. Async IIFE (Immediate Invoked Function Expression)
(async () => { 
  console.log("Getting Data One");
  await getData(1); 
  console.log("Getting Data Two");
  await getData(2); 
  // ... all subsequent await calls
})();
```