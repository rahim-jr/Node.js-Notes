# Promise Under the Hood - Test Implementation

## Promise Implementation Example

### print Function

```js
function print(resolve, reject) {
    console.log("--------callback executed------------");
    console.log(resolve, reject);
    setTimeout(() => {
        console.log("Call stack e ashsi");
        const user = [1, 2, 3];
        resolve(user);
    }, 2000);
}
```

### Promise Class Implementation (Under the Hood)

```js
class Promise {
    constructor(callback) {
        this.resolve = function(){};
        this.reject = function(){};
        callback(this.resolve, this.reject); // Gets executed upon constructor call
    }
     
    then = (cb1) => {
        this.resolve = cb1;
        return this;
    }

    catch = (cb2) => {
        this.reject = cb2;
        return this;
    }
}
```

### Promise Usage

```js
console.log("Start");

const prom1 = new Promise(print);
console.log(prom1);

prom1
    .then(result => {
        console.log(result);
    })
    .catch(err => {
        console.log(err);
    });

console.log("end");
```

## Key Concepts

### Promise Constructor

- **Callback Execution**: The callback function is executed immediately when the Promise constructor is called
- **Resolve/Reject**: Initially set as empty functions, later replaced by `.then()` and `.catch()` callbacks
- **Return Value**: Returns the Promise instance for method chaining

### Method Chaining

- **`.then()`**: Sets the resolve callback and returns the Promise instance
- **`.catch()`**: Sets the reject callback and returns the Promise instance
- **Chaining**: Allows multiple `.then()` and `.catch()` calls

### Async Function Requirement

- **Important**: We have to use `async` before the function that has promise inside of it
- **Purpose**: Enables the use of `await` keyword for cleaner async code

### Execution Flow

1. **Start**: Console logs "Start"
2. **Promise Creation**: Creates Promise with print callback
3. **Promise Object**: Logs the Promise object
4. **Method Chaining**: Sets up `.then()` and `.catch()` handlers
5. **End**: Console logs "end"
6. **Async Execution**: After 2 seconds, resolves with user array
7. **Callback Execution**: Logs "Call stack e ashsi" and resolves with `[1, 2, 3]`
