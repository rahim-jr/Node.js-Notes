# JavaScript Promises and Async/Await - Brad Promise

## Promise Implementation Example

### Posts Data Structure

```js
const posts = [
    {
        title: "post one",
        body: "this is post one",
    },
    {
        title: "post two",
        body: "this is post two",
    },
];
```

### getPosts Function

```js
function getPosts() {
    setTimeout(() => {
        let output = "";
        posts.forEach((post, index) => {
            output += `<li>${post.title}</li>`;
        });
        document.body.innerHTML = output;
    }, 1000);
}
```

### createPost Function with Promise

```js
function createPost(post) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            posts.push(post);

            const error = false;

            if (!error) {
                resolve();
            } else {
                reject("Error: Something went wrong");
            }
        }, 2000);
    });
}
```

### Promise Usage (Commented Out)

```js
// createPost({ title: 'Post Three', body: 'This is post three' })
//     .then(getPosts)
//     .catch(err => console.log(err));
```

### Async/Await Implementation

```js
async function init() {
    await createPost({ title: "Post Three", body: "This is post three" });
    getPosts();
}

init();
```

## Key Concepts

### Promise Benefits

- **Asynchronous Operations**: Handle async operations without callback hell
- **Error Handling**: Built-in error handling with `.catch()`
- **Chaining**: Chain multiple async operations with `.then()`

### Async/Await Benefits

- **Cleaner Syntax**: More readable than promise chains
- **Error Handling**: Use try/catch blocks
- **Sequential Execution**: `await` waits for promise resolution

### Usage Pattern

1. **Create Promise**: Function returns a Promise
2. **Handle Success**: Use `.then()` or `await`
3. **Handle Errors**: Use `.catch()` or try/catch
4. **Execute**: Call the async function
