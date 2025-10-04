# Database Schema Design - Personal Notes

## Database Tables Structure

### Merchant Table

| id | title |
|----|-------|
| 1  | a     |

### Product Table

| id | merchantid | productId |
|----|------------|-----------|
| 1  | 1          | 2         |
| 2  | 1          | 3         |

### Products Table

| id | title |
|----|-------|
| 1  | a     |
| 2  | b     |
| 3  | c     |

## Permission System Schema

### Permission Structure

| id | title | id | permissionSetId | permissionId | id | title |
|----|-------|----|-----------------|--------------|----|-------|
| 1  | a     | 1  | 1                | 2            | 1  | a     |
| 2  | b     | 1  | a                | 2            | 1  | 3     |
| 3  | c     |    |                  |              |    |       |

## API Response Structure

### Example Response Object

```json
{
  "id": 1,
  "title": "a",
  "permissionSetWithPermissions": [
    {
      // Permission set details
    },
    {
      // Permission set details
    }
  ]
}
```

## Database Relationships

### Key Relationships

- **Merchant** → **Products** (One-to-Many)
- **Products** → **Permissions** (Many-to-Many through junction table)
- **Permission Sets** → **Permissions** (One-to-Many)

### Junction Tables

- **merchantid** links merchants to products
- **permissionSetId** links permission sets to permissions
- **permissionId** identifies specific permissions

## Schema Design Principles

### Normalization

- Each table has a unique primary key
- Foreign keys maintain referential integrity
- Junction tables handle many-to-many relationships

### Data Integrity

- Consistent naming conventions
- Proper data types for each field
- Clear relationships between entities
