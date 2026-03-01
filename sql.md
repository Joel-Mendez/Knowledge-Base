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
- `IF NOT EXISTS`
    -  Safe to call every time the app starts. Only creates the table on the very first run; after that it's a no-op. Without `IF NOT EXISTS`, it would throw an error if the table already exists.

# Primary Keys
- A primary key serves as a unique identifier for each row
- Only one primary key can exist per table
- Must be unique across all rows
- Cannot be NULL
- `AUTOINCREMENT` on an integer primary key means the database automatically assigns the next available integer ID when a new row is inserted. You never have to supply the ID yourself.

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

# Inserting New Rows
## Basic SQL Syntax
```sql
INSERT INTO table_name (column1, column2) VALUES (value1, value2);
```
## lastrowid
- After an `INSERT`, `cursor.lastrowid` gives you the auto-generated primary key of the row that was just inserted.
- This lets you return the new ID to the frontend without needing a separate `SELECT` query.

```python
cursor.execute('INSERT INTO tasks (name) VALUES (?)', (name,))
conn.commit()
task_id = cursor.lastrowid  # The id sqlite3 assigned to the new row
```

# Selecting Rows
**Basic SQL Syntax**
```sql
SELECT column1, column2 FROM table_name;
SELECT * FROM table_name;  -- * means all columns
```

**In Python (sqlite3):**
```python
cursor.execute('SELECT id, name FROM tasks')
rows = cursor.fetchall()   # returns all matching rows as a list
row  = cursor.fetchone()   # returns only the first matching row (or None)
```

## Converting a Row to a Dict
- `sqlite3.Row` objects are dict-like but not actual Python dicts, so `jsonify` won't accept them directly.
- Use `dict(row)` to convert one row, or a list comprehension for multiple rows.

```python
# Single row
task = dict(row)  # {"id": 1, "name": "Buy milk"}

# All rows
tasks = [dict(row) for row in rows]  # [{"id": 1, ...}, {"id": 2, ...}]
```

# Deleting Rows
```sql
DELETE FROM table_name WHERE condition;
```

```python
cursor.execute('DELETE FROM tasks WHERE id = ?', (task_id,))
conn.commit()
```

# Parameterized Queries
- Use `?` as placeholders for values.
- Don't use f-strings or string concatenation to build SQL queries as it allows for SQL injection (an SQL style input could change the original intent of your query and manipulate your databse). 

Example:
```python
# Safe — parameterized
cursor.execute('INSERT INTO tasks (name) VALUES (?)', (name,))

# Dangerous — never do this
cursor.execute(f'INSERT INTO tasks (name) VALUES ({name})')
```