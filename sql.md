# SQL 
- Structured Query Language (SQL). Used for relational databases. 
- Databases can contain multiple tables. Within a table, a row is a record and a column is a field.

# Initialization 

```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
``` 
# Primary Keys
- A primary key serves as a unique identifier for each row
- Only one primary key can exist per table
- Must be unique across all rows
- Cannot be NULL

# Common Data Types
- `INTEGER`: Whole numbers. Used for IDs, counts, priorities, flags (0/1).
- `TEXT`: Strings and free-form text. Used for names, status, notes, labels.
- `REAL`: Decimal numbers. Used for progress, scores, measurements.
- `DATE / DATETIME`:Dates and timestamps (often stored as text or integers in SQLite, but treated logically as dates).
- `BLOB`: Binary data (files, images). Rarely needed for typical apps.

# Common Constraints
- `PRIMARY KEY`: Uniquely identifies each row in a table. Must be unique and not null.
- `NOT NULL`: Ensures a column always has a value.
- `UNIQUE`: Ensures all values in a column are different.
- `DEFAULT`: Sets a default value if none is provided.
- `FOREIGN KEY`: Enforces a relationship to another table’s primary key.
- `CHECK`: Ensures values satisfy a condition (e.g., `priority BETWEEN 1 AND 5`).