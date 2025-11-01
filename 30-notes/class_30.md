# Entity Relationship Diagram (ERD) - Class 30

## Entity Relationship Diagram Rules

### Entity Naming Convention
- **Entity names** will be **singular**
- Example: `User`, `Profile`, `Permission` (not `Users`, `Profiles`, `Permissions`)

## User Entity Structure

### User Entity Components
- **a. email** - User's email address
- **b. password** - User's password
- **c. profile** - Profile relationship

### Profile Relationship
- **Profile ID** comes from the Profile table
- **Profile ID** is the **primary key** of the Profile table
- **Profile ID** in the User table becomes a **foreign key**
- **Rule**: Without any profile ID, one cannot create a user

### Key Definitions

**Primary Key**
- A unique key that allows you to uniquely identify a row
- Example: UUID type column that uniquely identifies each row

**Foreign Key**
- Only a uniquely identified column has the potential to become a foreign key
- When a primary key of one table gets assigned to another table, it becomes a foreign key in that assigned table

### Example: Primary Key & Foreign Key

**User Table:**
| id | name |
|----|------|
| 1  | a    |
| 2  | b    |
| 3  | c    |

- **ID column** is UUID type because we can identify each row using unique keys
- **ID** serves as the primary key

---

## Database Relations

### What is ERD?
**Answer**: An ERD visualizes the relationships between entities like people, things, or concepts in a database. ERD stands for **Entity Relationship Diagram**.

### What is Database Cardinality?
**Answer**: Cardinality is the mathematical sense meaning the number of values in a set. In relationship to databases and ERD, cardinality specifies how many instances of an entity relate to one instance of another entity.

### What is Database Ordinality?
**Answer**: Ordinality describes the relationship as either mandatory or optional. Ordinality specifies the absolute minimum number of relationships.

### Database Relationship Types

There are **4 types** of database cardinality/relationship:

1. **One to One** (1:1)
2. **One to Many** (1:M)
3. **Many to One** (M:1)
4. **Many to Many** (M:M)

### Database Relationship Cardinality Symbols

| Symbol | Meaning |
|--------|---------|
| `|-` | One |
| `<-` | Many |
| `|-|-` | One and only one |
| `O-|-` | Zero or one |
| `|-<-` | One or many |
| `O<-` | Zero or many |

### Profile-User Relationship Example

**Profile → User**
- **One** to **Many**

**User → Profile**
- **One** to **One**

**Overall Relationship**: User & Profile has **Many to One** relationship

### Facts
1. **One user** can only have **one profile**
2. **One profile** can be assigned to **many users** (e.g., one customer profile can be assigned to many customers)

---

## Database Normalization

### Normalization Theory
Normalization rules divide larger tables into smaller tables and link them using relationships.

### ACID Properties
In computer science, **ACID** (Atomicity, Consistency, Isolation, Durability) is a set of properties of database transactions intended to guarantee data validity despite errors, power failures, and other mishaps.

### First Normal Form (1NF)
- **Rule**: Cannot keep an array in a table
- **Requirement**: Every value has to be atomic

### Normalization Example

**Method 1 (Doesn't follow Normalization):**
| course_id | student_id | course_name |
|-----------|------------|-------------|
| 1 | 1 | ["C", "java", "math"] |

**Method 2 (Follows Normalization):**
| course_id | student_id | course_name |
|-----------|------------|-------------|
| 1 | 1 | C |
| 2 | 1 | java |
| 3 | 1 | math |

### Profile-Permission Relationship

**Profile → Profile Permission**
- **One** to **One or Many**

**Profile Permission → Profile**
- **One or Many** to **One**

### Permission Types

- **Standard Permission**: Built by the system by default
- **Custom Permission**: Built by a user

### Self-Referencing Relationships

**Fact**: The same row's primary key can serve as a foreign key in another row's parent ID column.

**Example:**
- **Parent Service**: Shop Service
- **Child Services**: Other services under the shop service
