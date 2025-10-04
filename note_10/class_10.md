# JavaScript Advanced Concepts - Class 10

## 1. setTimeout Questions and Memory Leak Issues

### Problem with `var` in Loops

When using `var` in a for loop with setTimeout, all functions share the same lexical environment, causing memory leaks because `var` resides in global scope.

```js
// PROBLEMATIC CODE - Memory leak occurs
for (var i = 1; i <= 5; i++) {
    // Here 5 blocks are created, but at the end memory leak occurs
    // because var resides in global scope. With var, all functions share the same lexical environment
    setTimeout(() => {
        console.log(i); // Will print 6, 6, 6, 6, 6
    }, i * 1000);
}
```

### Solution with `let`

When using `let`, 5 separate blocks are created with 5 separate lexical environments. Each `let` declaration creates a separate block scope, preventing memory leaks.

```js
// CORRECT CODE - No memory leak
for (let i = 1; i <= 5; i++) {
    // Here 5 blocks are created, and 5 lexical environments are created
    // let creates separate block scope for each iteration, preventing memory leak
    setTimeout(() => {
        console.log(i); // Will print 1, 2, 3, 4, 5
    }, i * 1000);
}
```

### Simple Loop Example

```js
for (var i = 1; i <= 5; i++) {
    console.log(i); // Prints 1, 2, 3, 4, 5
}
```

## 2. First-Class Function: forEach

### Understanding forEach

`forEach` is a native function that JavaScript creators have natively coded. `forEach` is a first-class function that expects a callback function as its parameter.

```js
const arr = [1, 2, 3, 4, 5];

function print(number, index) {
    console.log(number, index);
}

// Test the function
print(3, 2); // Output: 3 2
print(6, 1); // Output: 6 1

// Using forEach
arr.forEach(print);
```

### How forEach Works

- `forEach` is a first-class function that expects a callback function as parameter
- The callback function is called as many times as there are values in the array
- In this case, the array is treated as an object
- When `forEach` calls the callback function, it passes 2 arguments:
  1. **First argument**: The data/value from the array
  2. **Second argument**: The index of that array element

### forEach Implementation (Simplified)

```js
void forEach(callback) {
    for (var i = 0; i < this.length; i++) {
        callback(arr[i], i);
    }
}
```

**Important**: Always use `forEach` function, never use `for` loops.

## 3. Objects and Classes

## 4. Object Structure

- In an object, everything is stored in **key: value** format
- Each **key: value** pair is separate from others
- **Key** = **Property**
- **Object** is a **non-primitive data type**

### Example

```js
const person = {
    name: "John",        // key: "name", value: "John"
    age: 25,            // key: "age", value: 25
    city: "New York"    // key: "city", value: "New York"
};

console.log(person.name);  // "John"
console.log(person.age);   // 25
console.log(person.city);  // "New York"
```
