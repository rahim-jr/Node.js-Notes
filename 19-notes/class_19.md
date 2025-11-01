# Full-Stack Development Setup - Class 19

## Project Setup Steps

1. **Server Creation** - Set up Express server
2. **Route Creation** - Define API endpoints
3. **Controller Creation** - Implement business logic
4. **Router & Controller Relationship** - Connect routes to controllers
5. **Database Creation** - Set up database using Sequelize ORM
6. **Seeder Creation** - Create database seeders using Sequelize
7. **Project Structure Understanding** - Organize code properly
8. **Configuration Setup** - Configure default.js settings

## Additional Dependencies

### Install Required Packages

```bash
# Install utility libraries
npm install lodash glob

# Lodash - Utility library for JavaScript
# Glob - Pattern matching for file paths
```

## Project Structure

```
src/
├── modules/
│   ├── core/
│   │   └── middlewares/
│   └── routes/
├── config/
│   └── default.js
└── database/
    ├── models/
    └── seeders/
```

## Key Concepts

- **Lodash**: JavaScript utility library providing helpful functions
- **Glob**: Pattern matching library for file system operations
- **Sequelize**: Object-Relational Mapping (ORM) for database operations
- **Seeders**: Database seeding for initial data population
