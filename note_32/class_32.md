# Authorization System - Class 32

## Authorization Folder Structure

### New Folder: `authorization`

Contains 2 files:

1. **authorization.constants.js**
   - Exports an object `{}` containing all services
   - Centralized service definitions

2. **authorization.middlewares.js**
   - Authorization middleware implementation
   - Permission checking logic

## Authorization Rules

### Profile Creation Permission

- **Rule**: Profile can only be created by users who have **"manage user profile"** permission
- **Authorization Chain**: User → UserProfile → Permission → Service

### Permission Hierarchy

```text
User
  ↓
UserProfile
  ↓
Permission
  ↓
Service
```

## Circular Dependency

**Question**: What is circular dependency?

**Answer**: Circular dependency occurs when two or more modules depend on each other directly or indirectly, creating a loop that can cause issues during module loading and initialization.

---

## Authorization Middleware

### Purpose

- **Access Control**: Determines if a user has permission to perform specific actions
- **Permission Validation**: Checks user permissions against required service permissions
- **Route Protection**: Protects routes that require specific permissions

### Implementation Flow

1. **Extract User**: Get user information from request
2. **Check Profile**: Verify user's profile and permissions
3. **Validate Service**: Check if user has permission for the requested service
4. **Grant/Deny Access**: Allow or deny access based on permission validation

### Key Components

- **Service Constants**: Defined in `authorization.constants.js`
- **Middleware Logic**: Implemented in `authorization.middlewares.js`
- **Permission Chain**: User → Profile → Permission → Service relationship
