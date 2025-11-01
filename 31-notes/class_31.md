# Database Tables and Seeder Functions - Class 31

## Database Tables Overview

**Total Database Tables: 7**

1. **admins** - Administrator accounts
2. **permissions** - System permissions
3. **permission_services** - Junction table linking permissions to services
4. **profiles** - User profiles
5. **profile_permissions** - Junction table linking profiles to permissions
6. **services** - System services
7. **users** - User accounts

---

## Seeder Functions

### 1. userSeeder Function

**Process:**
1. **Find User**: Tries to find a user using an email address
2. **Create User**: If not found, creates the user using:
   - Email from the `where` clause
   - Password from the defaults configuration
3. **Execute Callback**: After finding or creating, executes the `then` block and runs the callback function

### 2. profileSeeder Function

**Process:**
1. **Find Admin**: Tries to find the admin user
2. **Create Profile**: Creates a profile for the admin in the `profileSeeder` function's `then` block
3. **Profile Properties**: Uses the Profile table's properties
4. **Profile Types**:
   - **System Admin**: Standard type profile (created by programmer)
   - **Super Admin Created Admin**: Custom type profile (created by super admin)

### Database Properties

#### Truncate Property
- **Cascade**: `true`
- **Purpose**: When truncating a table, also truncate related tables

#### Cascading Property Details
- **Cascade Delete**: When a parent record is deleted, child records are automatically deleted
- **Cascade Update**: When a parent record is updated, child records are automatically updated
- **Referential Integrity**: Maintains data consistency across related tables

### New Library: Async

**Async Library**: Used for handling asynchronous operations in the seeder functions
- Provides utilities for working with asynchronous JavaScript
- Helps manage complex async flows in database seeding operations
