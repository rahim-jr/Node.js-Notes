# Schema Validation and Middleware - Class 25

## Schema Validation Principles

### 1. Centralized Validation
- All schema validation should be contained in **one file**
- This ensures consistency and easier maintenance

### 2. Single Responsibility Principle
- **One file** must have **one responsibility**
- **One function** must have **one responsibility**
- This improves code organization and maintainability

## Middleware Function Structure

### File Organization
```
modules/
└── core/
    └── middlewares/
        └── validator.middleware.js
```

### Middleware Location
- All common middleware functions should be placed inside the `core/middlewares` folder
- This creates a centralized location for reusable middleware

## Best Practices

### Validation Middleware
- Create dedicated validation middleware for each schema
- Keep validation logic separate from business logic
- Use consistent error handling across all validations

### Code Organization
- Follow the single responsibility principle
- Keep related functionality together
- Maintain clear separation of concerns

## Example Structure

```js
// validator.middleware.js
const validateUser = (req, res, next) => {
    // Validation logic here
    next();
};

const validatePost = (req, res, next) => {
    // Validation logic here
    next();
};

module.exports = {
    validateUser,
    validatePost
};
```
