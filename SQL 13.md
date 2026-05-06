# SQL for Data Science

## 1. Introduction to SQL
SQL (Structured Query Language) is a standard programming language used to manage and manipulate relational databases. It allows users to store, retrieve, update, and delete data efficiently.

SQL is widely used in data science because most real-world data is stored in structured databases.

---

## 2. SQL: Structured Data Programming Language
SQL is specifically designed for handling **structured data** stored in tables. These tables consist of rows and columns, where:

- Rows = Records
- Columns = Attributes (fields)

SQL provides a simple and readable syntax, making it easy to interact with databases.

---

## 3. Why SQL?
SQL is essential for data science because:

- It is used to access large datasets stored in databases
- It is fast and efficient for querying data
- It integrates well with tools like Python, R, and BI tools
- It is widely used in industry (almost every company uses SQL)

---

## 4. Handling Structured Data
Structured data is organized in a tabular format.

### Example Table: Customers

| ID | Name   | Age | City     |
|----|--------|-----|----------|
| 1  | Ali    | 25  | Karachi  |
| 2  | Sara   | 30  | Lahore   |

SQL helps:
- Retrieve specific data
- Filter records
- Sort results
- Aggregate data (sum, avg, count)

---

## 5. Using SQL for Data Science
In data science, SQL is used for:

- Data extraction
- Data cleaning
- Data transformation
- Data aggregation
- Feature engineering

### Example:
```sql
SELECT city, AVG(age) AS avg_age
FROM customers
GROUP BY city;
6. SQL Attributes for Data Science

Attributes (columns) define the structure of data.

Common attributes:

Numeric (INT, FLOAT)
Text (VARCHAR)
Date (DATE, TIMESTAMP)
Boolean (TRUE/FALSE)

Important concepts:

Primary Key (unique identifier)
Foreign Key (relationship between tables)
7. SQL Commands
a. DDL (Data Definition Language)

Used to define database structure:

CREATE
ALTER
DROP
b. DML (Data Manipulation Language)

Used to manipulate data:

INSERT
UPDATE
DELETE
c. DQL (Data Query Language)
SELECT
d. DCL (Data Control Language)
GRANT
REVOKE
8. SQL Syntax

Basic SQL query structure:

SELECT column1, column2
FROM table_name
WHERE condition
ORDER BY column1;
Example:
SELECT name, age
FROM customers
WHERE age > 25
ORDER BY age DESC;
9. Relational Database

A relational database organizes data into tables that are related to each other.

Key Features:
Data stored in tables
Relationships using keys
Structured schema
Example:

Table 1: Orders

order_id	customer_id

Table 2: Customers
| customer_id | name |

These tables are linked using customer_id.

Conclusion

SQL is a fundamental skill for data science. It allows efficient data handling, querying, and transformation, making it essential for analyzing structured datasets.
