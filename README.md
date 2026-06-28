# MySQL-Lab

## Hierarchical / Tree View :

**school_db**

```
+----------------------+
| school_db [Database] |
+----------------------+
    |
    |   +------------------+
    └── | students [Table] |
        +------------------+ 
            ├── student_id (INT, PK, AUTO_INCREMENT)
            ├── first_name (VARCHAR(50))
            ├── last_name (VARCHAR(50))
            ├── gender (ENUM: 'Male', 'Female', 'Other')
            ├── dob (DATE)
            ├── department (VARCHAR(100))
            ├── admission_year (INT)
            └── marks (INT)
```
> This shows the structure of the database and table

---

## Table Schema:

**students**

| Column Name     | Data Type                         | Constraints                            |
| --------------- | --------------------------------- | -------------------------------------- |
| student_id      | ``INT``                           | PRIMARY KEY, AUTO_INCREMENT, NOT NULL  |
| first_name      | ``VARCHAR(50)``                   | NOT NULL                               |
| last_name       | ``VARCHAR(50)``                   | NOT NULL                               |
| gender          | ``ENUM('Male','Female','Other')`` | NOT NULL                               |
| dob             | ``DATE``                          | NOT NULL                               |
| department      | ``VARCHAR(100)``                  | NOT NULL                               |
| admission_year  | ``INT``                           | NOT NULL                               |
| marks           | ``INT``                           | CHECK (marks BETWEEN 0 AND 100)        |

---

## Sample Data:

**students**

|student_id | first_name | last_name | gender | dob        | department       | admission_year | marks |
|-----------|------------|-----------|--------|------------|------------------|----------------|-------|
| 1         | Prakash    | Shrestha  | Male   | 2002-03-15 | Computer Science | 2020           | 80    |
| 2         | Sita       | Shrestha  | Female | 2001-07-22 | Business         | 2019           | 90    |
| 3         | Prakash    | Thapa     | Male   | 2003-01-10 | Engineering      | 2021           | 60    |
| 4         | Maya       | Lama      | Female | 2000-11-05 | Computer Science | 2018           | 96    |
| 5         | Aarav      | KC        | Male   | 2002-05-28 | Arts             | 2020           | 80    |
| 6         | Nisha      | Magar     | Female | 2001-09-12 | Engineering      | 2019           | 89    |

---

## Operations:

- **Table Setup**
    - Create Database & Table
    - Insert Sample Data

- **Queries**
    - Select all records and find total number of student.
    - Select specific columns
    - Filter by ``department``
    - Filter by ``marks`` greater than ``85``
    - Order by ``marks`` (highest first)
    - Show full names using ``CONCAT``
    - Search students by ``first name``, ``last name``, or ``full name`` (combined).
    - Count students in each ``department``
    - Average ``marks`` by ``department``
    - Find the highest and lowest ``marks`` student
    - Students admitted after ``2019``
    - Top ``3`` students by ``marks``
    - Find the oldest ``student``
    - Total students admitted each year
    - Total ``marks`` by ``gender``
    - Show only the full name and pass/fail result [ if **``(marks >= 40)``** ``Pass`` else ``Fail`` ]

- **Update Table**
    - Update ``marks`` for a student
    - Delete a student by ``ID``

- **Table management**
    - Add a new column
    - Modify column data type
    - Rename a column
    - Drop a column
    - Rename table
    - Truncate table (delete all records)
    - Drop table

- **Drop database**

## Resources

- [**SQL Syntax**](sql-syntax.md)
- [**MySQL Official Documentation (Basics)**](https://dev.mysql.com/doc/refman/8.0/en/tutorial.html) — official introduction to MySQL.


---

# Solution

## Table Setup

### Create Database & Table

```sql
CREATE DATABASE IF NOT EXISTS school_db;
USE school_db;

CREATE TABLE students (
    student_id INT PRIMARY KEY AUTO_INCREMENT,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    gender ENUM('Male','Female','Other') NOT NULL,
    dob DATE NOT NULL,
    department VARCHAR(100) NOT NULL,
    admission_year INT NOT NULL,
    marks INT CHECK (marks >= 0 AND marks <= 100)
);
```

### Insert Sample Data

```sql
INSERT INTO students (first_name, last_name, gender, dob, department, admission_year, marks) 
VALUES
    ('Prakash', 'Shrestha', 'Male',   '2002-03-15', 'Computer Science', 2020, 80),
    ('Sita', 'Shrestha', 'Female', '2001-07-22', 'Business', 2019, 90),
    ('Prakash', 'Thapa', 'Male',   '2003-01-10', 'Engineering', 2021, 60),
    ('Maya', 'Lama', 'Female', '2000-11-05', 'Computer Science', 2018, 96),
    ('Aarav', 'KC', 'Male',   '2002-05-28', 'Arts', 2020, 80),
    ('Nisha', 'Magar', 'Female', '2001-09-12', 'Engineering', 2019, 89);
```
