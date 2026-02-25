# SQL 
- Structured Query Language (SQL). Used for relational databases. 
- Databases can contain multiple tables. Within a table, a row is a record and a column is a field.

# sqlite3
- `sqlite3` is Python’s built-in module for working with SQLite databases.

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

# Conn/ Cursor 
Typical steps in working with a database:
1. Connect to the database.
2. Create a cursor.
3. Execute SQL queries.
4. Commit changes (if modifying data).
5. Close the connection.

Example:

```python
conn = sqlite3.connect("tasks.db")
cursor = conn.cursor()

cursor.execute("""
CREATE TABLE IF NOT EXISTS tasks (
    id INTEGER PRIMARY KEY,
    name TEXT
)
""")

conn.commit()
conn.close()
```

# Row Factory (Access Columns by Name)

- `row_factory = sqlite3.Row` allows access to columns by name.

Example:

```python
conn = sqlite3.connect("tasks.db")
conn.row_factory = sqlite3.Row

cursor = conn.cursor()
cursor.execute("SELECT * FROM tasks")
row = cursor.fetchone()

print(row["name"])  # Instead of row[1]
```