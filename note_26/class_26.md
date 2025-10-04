# Login and Profile Customization - Class 26

## Customized Login Function

1. **Service File Creation**
   - Created a service file for login functionality
   - Login token generation is handled inside the service folder
   - Separates business logic from controller logic

## Customized Profile Function

2. **Required Libraries**
   ```bash
   npm install passport
   npm install passport-jwt
   ```

### Passport.js Integration
- **Passport**: Authentication middleware for Node.js
- **Passport-JWT**: JWT strategy for Passport authentication
- Used for secure user authentication and profile management

## Implementation Benefits

- **Separation of Concerns**: Service layer handles business logic
- **Security**: JWT tokens for secure authentication
- **Scalability**: Modular approach for easy maintenance
- **Best Practices**: Following industry standards for authentication
