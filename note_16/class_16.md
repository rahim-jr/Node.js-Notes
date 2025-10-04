# Express Routes and CRUD Operations - Class 16

## Express Route Definitions

Here are the standard CRUD routes for a posts resource:

```js
// Get all posts
app.get('/posts', (req, res) => {
    // Return all posts
});

// Create a new post
app.post('/posts', (req, res) => {
    // Create and return new post
});

// Get a single post by ID
app.get('/posts/:id', (req, res) => {
    // Return specific post
});

// Update a post completely
app.put('/posts/:id', (req, res) => {
    // Update entire post
});

// Partially update a post
app.patch('/posts/:id', (req, res) => {
    // Update specific fields
});

// Delete a post
app.delete('/posts/:id', (req, res) => {
    // Remove post from database
});
```

## Route Parameters

- `:id` is a route parameter that captures the ID from the URL
- Access the parameter using `req.params.id`
- Example: `/posts/123` → `req.params.id` = "123"

## HTTP Methods Summary

| Method | Route | Purpose |
|--------|-------|---------|
| GET | `/posts` | Retrieve all posts |
| POST | `/posts` | Create new post |
| GET | `/posts/:id` | Retrieve specific post |
| PUT | `/posts/:id` | Update entire post |
| PATCH | `/posts/:id` | Partially update post |
| DELETE | `/posts/:id` | Delete specific post |
