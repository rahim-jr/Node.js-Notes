# Dynamic Routes and Authentication - Class 23

## After getGlobalConfig Implementation

### Setup Flow

1. **Install Dependencies**
   ```bash
   npm install lodash
   npm install glob
   ```

2. **Add getGlobbedPaths Function**
   - Paste the `getGlobbedPaths` function into your project

## Understanding getGlobbedPaths Function

### Function Parameters

The `getGlobbedPaths` function requires 2 arguments:

1. **globPatterns**: Routes array from `default.js` configuration
2. **excludes**: String patterns to exclude from matching

### Function Behavior

- **Returns**: Array containing all route paths as strings
- **Purpose**: Matches patterns and collects all `.routes.js` files into an array
- **Benefit**: Makes routes dynamically included instead of manually importing each one

### Pattern Matching

```js
'src/modules/**/*.routes.js'
```

- `**` - Matches any folder (recursive)
- `*` - Matches any file
- `.routes.js` - Matches files ending with `.routes.js`

## HTTP Status Codes

| Code | Status | Description |
|------|--------|-------------|
| 200 | Success | Request completed successfully |
| 400 | Bad Request | Invalid request data |
| 403 | Forbidden | Access denied |
| 404 | Not Found | Resource not found |
| 500 | Internal Server Error | Server error |

## Authentication Setup

### JWT Token Implementation

1. **Install jsonwebtoken**
   ```bash
   npm install jsonwebtoken
   ```

2. **Cookie Parser Setup**
   ```bash
   npm install cookie-parser
   ```

### Token Security

- **Facebook Example**: When logged into Facebook, FB provides a token
- **Security**: Token can only be decoded with the secret key
- **Hacker Protection**: To crack a token, hackers must crack 2 secrets:
  1. The token itself
  2. The secret key used to sign it
