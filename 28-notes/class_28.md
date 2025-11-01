# Database Design and Relationships - Class 28

## Database ER (Entity Relationship) Design

### Primary Keys
- **Unique column** will be the **primary key** of the table
- Ensures each record is uniquely identifiable

## Database Normalization

Database normalization follows these forms:
- **1NF** (First Normal Form)
- **2NF** (Second Normal Form)  
- **3NF** (Third Normal Form)

## Table Relationships

### Posts and User Table Relationship

**Directional Relationships:**
- **Many-to-One**: Going from above to below (Posts → User)
- **One-to-Many**: Going from below to up (User → Posts)

### Posts Table Structure

| Column | Type | Description |
|--------|------|-------------|
| id | Primary Key | Unique identifier |
| content | Text | Post content |
| owner | Foreign Key | References user.id |

**Sample Data:**
| id | content | owner |
|----|---------|-------|
| 1 | I love you | 1 |
| 2 | u r | 2 |
| 3 | hey | 3 |
| 4 | ggg | 1 |

### User Table Structure

| Column | Type | Description |
|--------|------|-------------|
| id | Primary Key | Unique identifier |
| name | String | User name |

**Sample Data:**
| id | name |
|----|------|
| 1 | habib |
| 2 | riyad |
| 3 | ruhin |

## Inconsistency Problem

**Problem**: If we change a user's name in the User table, queries using the name as a foreign key will fail, causing inconsistency.

**Solution**: Use **user ID** as foreign key instead of name, ensuring data integrity.

## Student-Course Table Example

### Before Normalization (Problematic)
| studentid | courses |
|-----------|---------|
| 1 | bangla,eng |
| 2 | node,react |
| 3 | mic |

### After Normalization (Correct)
| studentid | courses |
|-----------|---------|
| 1 | bangla |
| 1 | eng |
| 2 | node |
| 2 | react |
| 3 | mic |

**Normalization Rule**: Each field contains only **singular values**.

## Database Relationship Types

There are **4 types** of relationships in databases:

1. **One-to-One** (1:1)
2. **One-to-Many** (1:M)
3. **Many-to-One** (M:1)
4. **Many-to-Many** (M:M)

### Cardinality and Ordinality
- **Cardinality**: Number of relationships
- **Ordinality**: Direction of relationships
- Symbols represent different relationship types

## Permissions and Services

### Relationship Structure
- **One Service** → **Multiple Permissions** (One-to-Many)
- **One Permission** → **Multiple Services** (Many-to-Many)

## User-Profile-Permission-Service Relationships

### System Overview
- **Multiple user types**, each with **one profile**
- **Profile** contains **multiple permissions**
- **Permission** can belong to **multiple profiles**
- **Permission** consists of **multiple services**
- **Service** can be in **multiple permissions**

### Relationship Types
- **One-to-One**: User ↔ Profile
- **One-to-Many**: Profile → Permission, Permission → Service
- **Many-to-Many**: Permission ↔ Profile, Service ↔ Permission

## Database Schema Structure

### Core Tables
- **User**: Primary key (id), user information
- **Profile**: Primary key (id), profile information
- **Permission**: Primary key (id), permission information
- **Service**: Primary key (id), service information

### Junction Tables
- **User-Profile**: user_id, profile_id (foreign keys)
- **Profile-Permission**: profile_id, permission_id (foreign keys)
- **Permission-Service**: permission_id, service_id (foreign keys)
