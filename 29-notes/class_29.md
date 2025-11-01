# Sequelize ORM and Authentication Strategy - Class 29

## Sequelize ORM Database Schema

This codebase uses **Sequelize** as an Object Relational Mapping (ORM) tool to define and manage the database schema.

### Database Tables and Relations

#### Core Tables

**User Table**
- Stores user information (email, first name, last name, password)
- Each user can have **one profile**
- Each user can belong to **many services**

**Profile Table**
- Stores profile information (name, description, type)
- Each profile can belong to **many users**
- Each profile can have **many permissions**

**Permission Table**
- Stores permission information (name, description, type)
- Each permission can belong to **many profiles**
- Each permission can have **many services**

**Service Table**
- Stores service information (name, description)
- Each service can belong to **many permissions**
- Each service can have **many users**

#### Junction Tables

**ServicePermission Table**
- Junction table between Service and Permission tables
- Represents **many-to-many** relationship
- Each service can have many permissions
- Each permission can be assigned to many services

**PermissionProfile Table**
- Junction table between Permission and Profile tables
- Represents **many-to-many** relationship
- Each permission can be assigned to many profiles
- Each profile can have many permissions

### Database Relations

1. **User** has a foreign key to **Profile**
2. **User** has a many-to-many relationship with **Service** through ServicePermission junction table
3. **Profile** has a many-to-many relationship with **Permission** through PermissionProfile junction table
4. **Permission** has a many-to-many relationship with **Service** through ServicePermission junction table

---

## Authentication Strategy Implementation

### Strategy Purpose

1. **Route-Specific Strategy**: Strategy is created for the specific route that will use it
2. **User Authentication Check**: Strategy checks if a user is already logged in
3. **User-Specific Strategy**: Strategy is created for users who will log in
4. **Login Strategy**: Strategy is made for users who will perform login
5. **API Route Strategy**: Strategy is created for the specific API route (e.g., `/api/permissions`)

### Passport Strategy Implementation

```js
class Passport {
    use(x, obj) {
        this.strategyName = x;
        this.secretOrKey = obj.opt.secretOrKey;
        this.cookieExtractor = obj.opt.cookieExtractor;
        this.callback = obj.callback;
    }

    authenticate(strategyName, done) {
        return function (req, res, next) {
            const token = this.cookieExtractor(req);
            const decoded = jwt.verify(token, this.secretOrKey);
            this.callback(decoded, done);
        }.bind(this);
    }
}

// Strategy Configuration
passport.use(
    "user-jwt",
    new Strategy({ secretOrKey, cookieExtractor }, function (payload, done) {
        const user = findUser(payload.email);
        if (user) done(null, user);
        else done(null, false);
    }),
);

// Authentication Middleware for /users route (PATCH method)
function AuthStrategy(req, res, next) {
    const auth = passport.authenticate("user-jwt", function (err, user) {
        if (!user) return res.status(401).send("Unauthenticated user");
        req.logIn(user, {}, function (err) {
            next();
        });
    });

    auth(req, res, next);
}
```

### Strategy Components

- **Strategy Name**: "user-jwt" for JWT-based authentication
- **Secret Key**: Used for JWT token verification
- **Cookie Extractor**: Extracts JWT token from cookies
- **Callback Function**: Handles user verification and authentication
- **Authentication Middleware**: Protects routes requiring authentication
