# SQL Syntax:

## MySQL Datatypes

| Data Type      | Purpose                        | Example                  |
| -------------- | ------------------------------ | ------------------------ |
| `INT`          | Stores whole numbers           | `25`, `100`              |
| `VARCHAR(n)`   | Stores text of variable length | `"John"`                 |
| `CHAR(n)`      | Stores fixed-length text       | `"M"`                    |
| `DECIMAL(p,s)` | Stores decimal numbers         | `99.99`                  |
| `DATE`         | Stores dates                   | `2026-06-22`             |
| `DATETIME`     | Stores date and time           | `2026-06-22 10:30:00`    |
| `BOOLEAN`      | Stores True/False values       | `1`, `0`                 |
| `TEXT`         | Stores long text               | Paragraphs, descriptions |

## MySQL Constraints

| Constraint       | Purpose                                       |
| ---------------- | --------------------------------------------- |
| `NOT NULL`       | Column cannot have a NULL value               |
| `UNIQUE`         | All values in the column must be different    |
| `PRIMARY KEY`    | Uniquely identifies each record               |
| `CHECK`          | Ensures values satisfy a condition            |
| `DEFAULT`        | Provides a default value if none is specified |
| `AUTO_INCREMENT` | Automatically generates sequential numbers    |

## DDL (Data Definition Language)

### Creating Database:

**Syntax:**

```sql
CREATE DATABASE database_name;
```

### Creating Table:

**Syntax:**

```sql
CREATE TABLE table_name (
    column1 datatype [constraint],
    column2 datatype [constraint],
    ...
    table_constraints
);
```

### Table Management Command:

**Syntax:**

```sql
-- 1. Add a new column
ALTER TABLE table_name 
ADD column_name datatype;

-- 2. Modify column data type
ALTER TABLE table_name 
MODIFY column_name new_datatype;

-- 3. Rename a column
ALTER TABLE table_name 
CHANGE old_column_name new_column_name datatype;

-- 4. Drop a column
ALTER TABLE table_name 
DROP COLUMN column_name;

-- 5. Rename table
RENAME TABLE old_table_name 
TO new_table_name;

-- 6. Truncate table (delete all records)
TRUNCATE TABLE table_name;

-- 7. Drop table
DROP TABLE table_name;

```

### Drop Database:

**Syntax:**

```sql
DROP DATABASE database_name;
```


## DML (Data Manipulation Language)

```sql
-- 1. Insert a new row (specific columns)
INSERT INTO table_name (column1, column2, column3)
VALUES (value1, value2, value3);

-- 2. Insert into all columns
INSERT INTO table_name
VALUES (value1, value2, value3);

-- 3. Update existing row(s)
UPDATE table_name
SET column1 = value1,
    column2 = value2
WHERE condition;

-- 4. Delete specific row(s)
DELETE FROM table_name
WHERE condition;
```

## DQL (Data Query Language)

**Syntax:**

```sql
SELECT column1, column2, aggregate_function(...)
FROM table1
WHERE condition
GROUP BY column
HAVING condition
ORDER BY column [ASC | DESC]
LIMIT number OFFSET number;
```
**Clause Breakdown:**

- ``SELECT`` → Choose which columns (or expressions) to display.

- ``FROM`` → Table(s) from which data is retrieved.

- ``WHERE`` → Filter rows before grouping/aggregation.

- ``GROUP BY`` → Group rows (used with aggregate functions like COUNT, SUM, AVG).

- ``HAVING`` → Filter groups (applied after GROUP BY).

- ``ORDER BY`` → Sort the results.

- ``LIMIT / OFFSET`` → Limit number of rows returned (pagination).
