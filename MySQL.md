# SQL Interview Questions

## SQL Basics & Query Execution

1. Explain the order of execution of an SQL query.
2. What is the difference between WHERE and HAVING?
3. What is the use of GROUP BY?
4. What are aggregate functions? Explain with examples.
5. What is the difference between DISTINCT and GROUP BY?
6. What is the difference between UNION and UNION ALL?
7. Explain different SQL clauses.
8. What are different types of operators in SQL?
9. What is the difference between IN and EXISTS?
10. What is the difference between correlated and non-correlated subqueries?

## 2. SQL Joins & Relationships

11. Explain all types of joins in SQL.
12. Difference between INNER JOIN and LEFT JOIN.
13. What is SELF JOIN?
14. What is CROSS JOIN?
15. Explain One-to-One relationship.
16. Explain One-to-Many relationship.
17. Explain Many-to-Many relationship.
18. What is a Foreign Key?
19. How do joins affect query performance?

## Keys & Constraints
20. What are constraints in SQL?
21. Explain all types of constraints.
22. What is a Primary Key?
23. What is a Foreign Key?
24. Difference between Primary Key and Unique Key.
25. What is a Composite Key?
26. What is a Candidate Key?
27. What is a Super Key?
28. What is an Alternate Key?
29. What is Referential Integrity?

## Indexes & Performance Optimization
30. What is an Index?
31. Explain different types of indexes.
32. Difference between Clustered and Non-Clustered Index.
33. What is a Composite Index?
34. What is a Covering Index?
35. Advantages and disadvantages of indexes.
36. What causes Full Table Scan?
37. How do indexes improve performance?
38. When should indexes be avoided?
39. What is query optimization?
40. What is an Execution Plan?
41. What is the difference between Index Scan and Index Seek?
42. How to optimize slow SQL queries?
43. Why does pagination using OFFSET become slow?

## Window Functions

44. What are window functions?
45. Explain ROW_NUMBER().
46. Explain RANK().
47. Explain DENSE_RANK().
48. Difference between RANK() and DENSE_RANK().
49. Explain LEAD() function.
50. Explain LAG() function.
51. What is PARTITION BY?
52. Write query for cumulative/running total.
53. Write query to find second highest salary using window functions.
54. Difference between aggregate functions and window functions.

## CTEs & Subqueries

55. What is a CTE (Common Table Expression)?
56. Difference between CTE and Subquery.
57. Which is faster: CTE or Subquery?
58. What is Recursive CTE?
59. What are the advantages of CTEs?

## Transactions & ACID Properties

60. What is a transaction in SQL?
61. Explain ACID properties.
62. What is COMMIT?
63. What is ROLLBACK?
64. What is SAVEPOINT?
65. What are transaction isolation levels?
66. Explain Dirty Read.
67. Explain Non-Repeatable Read.
68. Explain Phantom Read.
69. What is a deadlock?
70. How can deadlocks be prevented?

## Stored Procedures, Functions & Triggers

71. What is a Stored Procedure?
72. Advantages of Stored Procedures.
73. What is a Function in SQL?
74. Difference between Function and Stored Procedure.
75. What are Triggers?
76. Types of Triggers.
77. Difference between BEFORE and AFTER trigger.
78. Real-world use cases of triggers.

## Views & Materialized Views

79. What is a View?
80. Advantages of Views.
81. Limitations of Views.
82. Can we use variables inside Views?
83. What is Materialized View?
84. Difference between View and Materialized View.

## 10. Data Types
85. Difference between CHAR and VARCHAR.
86. Difference between NCHAR and NVARCHAR.
87. Difference between TEXT and VARCHAR.
88. When should we use VARCHAR over CHAR?

## 11. SQL Commands
89. Difference between DDL, DML, DCL and TCL.
90. Difference between DELETE, TRUNCATE and DROP.
91. Difference between DELETE and TRUNCATE.
92. What is the difference between UPDATE and ALTER?

## 12. Normalization
93. What is normalization?
94. Explain 1NF.
95. Explain 2NF.
96. Explain 3NF.
97. Explain BCNF.
98. What is denormalization?
99. Advantages and disadvantages of normalization.

## 13. Real-Time SQL Coding Questions
100. Find second highest salary of employee.
101. Find nth highest salary.
102. Find duplicate records.
103. Delete duplicate records.
104. Find employees with highest salary department-wise.
105. Write cumulative sum query.
106. Write year-on-year growth query.
107. Write month-on-month growth query.
108. Write retention query.
109. Find top 3 salaries from each department.
110. Find employees who joined in last 30 days.
111. Find missing records from sequence.
112. Write pagination query.
113. Find consecutive duplicate values.
114. Find customers who never placed orders.
115. Find departments with more than 5 employees.

## Backend-Focused SQL Questions
116. How do you design scalable database schemas?
117. SQL vs NoSQL.
118. When would you choose MongoDB over SQL?
119. How do you handle database migrations?
120. How do you optimize APIs with SQL queries?
121. What are connection pools?
122. What causes database locking?
123. What is database sharding?
124. What is replication?
125. Difference between vertical and horizontal scaling.
126. How do you handle high-write systems?
127. How do you prevent SQL Injection?
128. What is optimistic locking?
129. What is pessimistic locking?
130. How do ORMs affect SQL performance?

---

### 1. Explain the Order of Execution of SQL Query

```ts
SELECT department, COUNT(*)
FROM employees
WHERE salary > 50000
GROUP BY department
HAVING COUNT(*) > 5
ORDER BY department;
```

#### Logical Execution Order:

1. FROM
2. WHERE
3. GROUP BY
4. HAVING
5. SELECT
6. DISTINCT
7. ORDER BY
8. LIMIT/OFFSET


#### Explanation:
- FROM → Table is selected.
- WHERE → Filters rows before grouping.
- GROUP BY → Groups rows.
- HAVING → Filters grouped data.
- SELECT → Chooses columns.
- ORDER BY → Sorts final result.

## 2. Difference Between WHERE and HAVING

#### Where 

- Filter Rows
- Used before GROUP BY
- Cannot Use Aggregate functions
- Faster

#### Having

- Filter Grouped Data
- Used after Group By
- Can use aggregate functions
- Slightly Slower

#### Example
```ts
SELECT department, COUNT(*)
FROM employees
WHERE salary > 50000
GROUP BY department
HAVING COUNT(*) > 3;
```

- Where: Filter Employees whose salary > 50000.
- Group By: Groups employees department-wise.
- Having: Filter departments having more than 3 Employees.

### Where for Row Filtering
### Having for aggregate filtering

## 3. What is GROUP BY?

GROUP BY groups rows having same values into summarized rows.

#### Example 
```ts
SELECT department, COUNT(*) AS total_employees
FROM employees
GROUP BY department;
```

#### Use Cases:
- Count employees department-wise
- Calculate total sales
- Generate reports

## 4. Aggregate Functions with examples ?
Aggregate functions perform calculations on multiple rows and return a single Value.

- COUNT() :- Count Rows
- SUM()   :- Adds Values
- AVG()   :- Calculate Average
- Min()   :- Finds Minimum
- Max()   :- Finds Maximum

### COUNT()
```ts
SELECT COUNT(*) FROM employees;
```

### SUM()
```ts
SELECT SUM(salary) FROM employees;
```

### AVG()
```
SELECT AVG(salary) FROM employees;
```
### MIN()
```ts
SELECT MIN(salary) FROM employees;
```

### MAX
```ts
SELECT MAX(salary) FROM employees;
```
## 5. What is the Difference Between DISTINCT and GROUP BY?
Both help in handling duplicate data, but their purpose differs.

### DISTINCT
- Removes duplicate rows
- No Aggregation Required
- Simpler
- Used for Uniqness

### Example
```ts
SELECT DISTINCT department
FROM employees;
```
Returns unique departments.

### GROUP BY
- Groups rows for aggregation.
- Mostly used with aggregates
- More Powerful
- Used for analytics/repoerting

### Example
```ts
SELECT department, COUNT(*)
FROM employees
GROUP BY department;
```
Returns department-wise count.

## 6. UNION vs UNION ALL
### Union

- Remove Duplicates
- Slower due to sorting/comparison
- Uses Distinct Internally

### UNION ALL
- Keeps Duplicates 
- Faster
- No duplicate check

## 7. Explain Different SQL Clauses
- Select   - Chooses columns.
- From     - Specifies table.  
- Where    - Filter rows
- Group BY - group rows
- Having   - Filter grouped data
- Order By -  sort results
- Limit/ offset - Restricts Rows

## 8. Types of Operators

### Arithmetic
+, -, *, /
### Comparison
=, !=, >, <
### Logical
AND, OR, NOT
### Special
IN, BETWEEN, LIKE, EXISTS

## 9. What is the Difference Between IN and EXISTS?

Both are used with subqueries.

### IN
- Compares values againt a list
- Better for small datasets
- Evaluates full result
- Can be slower for huge data

```ts
SELECT *
FROM employees
WHERE department_id IN (
  SELECT id FROM departments
);
```

### Exists

- Checks whether subquery returns rows.
- Better for Large Data Sets
- Stops when match found
- usually faster for large data

```ts
SELECT *
FROM employees e
WHERE EXISTS (
  SELECT 1
  FROM departments d
  WHERE d.id = e.department_id
);
```

## 10. What is the Difference Between Correlated and Non-Correlated Subqueries?

Non-Correlated Subquery
- Runs Once
- Faster
- Independent
- Simpler

### Example
```ts
SELECT name
FROM employees
WHERE salary > (
  SELECT AVG(salary)
  FROM employees
);
```
Inner query executes once.

### Correlated SubQuery
Depends on outer query and runs for every row.

- Runs per row
- Slower
- Depends on outer query
- More complex

## 11. Explain All Types of Joins
Joins are used to combine data from multiple tables based on related columns.

### Types of Joins
- INNER JOIN
- LEFT JOIN
- RIGHT JOIN
- FULL OUTER JOIN
- CROSS JOIN
- SELF JOIN

### INNER JOIN
Returns only matching rows from both tables.
```ts
SELECT e.name, d.department_name
FROM employees e
INNER JOIN departments d
ON e.department_id = d.id;
```

### LEFT JOIN
Returns all rows from left table and matching rows from right table.
If no match exists, NULL is returned.
```ts
SELECT *
FROM employees e
LEFT JOIN departments d
ON e.department_id = d.id;
```
### RIGHT JOIN
Returns all rows from right table and matching rows from left table.
```ts
SELECT e.name, d.department
FROM employees e
RIGHT JOIN departments d
ON e.department_id = d.id;
```

### FULL JOIN
Returns matching + non-matching rows.
```ts
SELECT e.name, d.department
FROM employees e
FULL OUTER JOIN departments d
ON e.department_id = d.id;
```

### CROSS JOIN
Returns Cartesian product.
Every row from first table joins with every row from second table.
```ts
SELECT *
FROM colors
CROSS JOIN sizes;
```
if 
- colors = 3 rows
- sizes  = 4 sizes

Output = 12 rows.

### SELF JOIN

Table joins itself.
Used for hierchial data.

```ts
SELECT e1.name, e2.name AS manager
FROM employees e1
JOIN employees e2
ON e1.manager_id = e2.id;
```
## 12 Difference Between INNER JOIN and LEFT JOIN

### INNER JOIN

- Only matching rows
- Ignores unmatched
- Faster generally

### LEFT JOIN

- All Left Table rows
- Includes Unmatched
- Slightly heavier
- Useful for optional relationship 

## 13. What is SELF JOIN?

SELF JOIN means joining a table with itself.

Used when table contains hierarchical relationships.

### Common Use Cases
- Employee → Manager
- Category → Parent Category
- Comments → Replies
Example

```ts
SELECT e.name AS employee,
m.name AS manager
FROM employees e
LEFT JOIN employees m
ON e.manager_id = m.id;
```

## 14. What is Cross join ?

CROSS JOIN creates Cartesian product.

Every row from first table combines with every row from second table.

### Example

```ts
SELECT *
FROM colors
CROSS JOIN sizes;
```

## 15. Explain One-to-One Relationship
One record in Table A is related to only one record in Table B.

### Example 
- User ↔ Passport
- User ↔ Profile
- Employee ↔ Locker


## 16. Explain One-to-Many Relationship

One record in Table A relates to many records in Table B.

### Example 
- Customer → Orders
- Department → Employees
- User → Posts


## 17. Explain Many-to-Many Relationship

Many records in Table A relate to many records in Table B.

### Example

- Students ↔ Courses

One student can enroll in many courses.
One course can have many students.

## 18. What is a Foreign Key?

Foreign Key creates relationship between tables.

It ensures referential integrity.

## 19. How Do Joins Affect Query Performance?

Joins are expensive operations, especially on large datasets.

### Factors Affecting Join Performance

### 1. Missing Indexes

Without indexes, database performs full table scans.

Very Slow

### 2. Large Tables

Joining millions of rows increases CPU and memory usage.

### 3. Wrong Join Type

Using Unnecessary joins increases execution time

### 4. Joining on Non-Indexed Columns

Slower lookups.

### 5. Multiple Complex Joins

Too many joins increase query complexity.

#### Optimized Techniques

- Use Indexes
- Select Required Columns
- Use Proper join Order
- Analyze execution Plan
 - Explain 
 - Explain Analyze

## 20. What are Constraints in SQL?

Constraints are rules applied on table columns to maintain data accuracy, consistency, and integrity.

### Why Constraints are Important
Maintain data integrity
Avoid duplicate data
Prevent invalid values
Enforce relationships between tables

### Types Of Constraints

1. Primary Key: Uniquely identifies each row.
2. Foreign Key: Creates relationship between tables.
3. Unique:      Ensures all values are unique.
4. Not Null:    Prevents NULL values.
5. Check:       Restricts values based on condition
6. Default:     Provides default value if none supplied.


## 22. What is a Primary Key?

Primary Key uniquely identifies each record in a table.

### Features
- Unique
- Cannot be NULL
- Only one primary key per table

## 23. What is a Foreign Key?

Foreign Key creates relationship between two tables.

It references the primary key of another table.

## 24. Difference Between Primary Key and Unique Key

### Primary Key

- Uniquely identifies row
- Cannot contain NULL
- Only one per table
- Automatically NOT NULL

### Unique Key

- Ensures uniqueness
- Can contain null
- Multiple allowed
- Null allowed

25. What is a Composite Key?

Composite Key uses multiple columns together to uniquely identify a row.

```ts
CREATE TABLE student_courses (
  student_id INT,
  course_id INT,
  PRIMARY KEY(student_id, course_id)
);
```

### Explanation
student_id alone → not unique
course_id alone → not unique
combination becomes unique

## 26. What is a Candidate Key?

Candidate Key is a column (or combination) that can uniquely identify records.

A table can have multiple candidate keys.

One candidate key becomes Primary Key.

### Example

- id: 1 
- email: raj@gmail.com
- phone: 909099099090

Possible Candidate Keys
- id
- email
- phone

## 27. What is a Super Key?

Super Key is any set of columns that uniquely identifies rows.

It may contain extra unnecessary columns.

### Example
id:- 1
email: raj@gmail.com
name: raj

Possible Super keys

- id,
- email
- id+email
- id+name

### Important Point

Every candidate key is a super key, but every super key is not a candidate key.

## 28. What is an Alternate Key?

Alternate Key is a candidate key that was not selected as primary key.

### Example

id: 1
email: raja@gmail.com

if
- EmployeeId is Primary Key
- Aadhaar Number is Alternate Key



### Important Point

Candidate keys:

Must be unique
Cannot contain NULL


## 5. What are Triggers?

Triggers are automatically executed SQL blocks when INSERT, UPDATE, or DELETE occurs.

### Types:
- BEFORE Trigger
- AFTER Trigger
- INSTEAD OF Trigger

### Example:
```ts
CREATE TRIGGER log_salary_change
AFTER UPDATE ON employees
FOR EACH ROW
INSERT INTO audit_log(employee_id, old_salary, new_salary)
VALUES (OLD.id, OLD.salary, NEW.salary);
```
### Use Cases:

- Audit Logging
- Validation
- Auto- Updates

## 6. What is Stored Procedure?

Stored Procedure is a precompiled SQL block stored in database.

### Example:

```ts
CREATE PROCEDURE GetEmployees()
BEGIN
SELECT * FROM employees;
END;
```
### Advantages
- Better Performance
- Reusable
- Reduced Network traffic
- cenetralized business logic

## Window Functions

Window functions perform calculations across rows without collapsing rows.

#### ROW_NUMBER().

Gives unique row number.

```ts
SELECT name, salary,
ROW_NUMBER() OVER(ORDER BY salary DESC) AS rn
FROM employees;
```

#### RANK()
Same rank for duplicates.
```ts
SELECT name, salary,
RANK() OVER(ORDER BY salary DESC) AS rnk
FROM employees;
```

#### DENSE_RANK()
No gaps in ranking.
```ts
SELECT name, salary,
DENSE_RANK() OVER(ORDER BY salary DESC) AS drnk
FROM employees;
```
## 8. Difference Between DELETE, TRUNCATE, DROP

### Delete
- Removes rows
- Can rollback
- Slow
- Where allowed

### Truncate
- Remove all Rows
- Usually Cannot rollback
- Faster
- Where not allowed

### DROP
- Removes Table
- Cannot rollback
- Fastest
- Removes Structure

## 9. DDL vs DML vs DCL vs TCL

### DDL
Schema Related
Commands: 
- Create
- Alter
- DROP
### DML
Data Manipulation
Commands:
- Insert
- update
- Delete

### DCL
Permisssion Related
Commands
- GRANT
- REVOKE

### TCL
Transaction Control
Commands:
- Commit
- Rollback
- Savepoint

## 11. CTE vs Subquery

### CTE
- More readable
- Reusable
- Supports recursion

### Subquery
- Less readable
- Not reusable
- No recursion

### Example

```ts
WITH emp AS (
SELECT * FROM employees WHERE salary > 50000
)
SELECT * FROM emp;
```
### Performance
- Depends on execution plan. No guaranteed performance difference.

## 12. Constraints and Types
Constraints enforce rules.

Types:
- Primary Key
- Foreign Key
- Unique
- Not Null
- Check
- Default

### Example
```ts
CREATE TABLE employees (
 id INT PRIMARY KEY,
 name VARCHAR(100) NOT NULL,
 salary INT CHECK (salary > 0)
);
```

## Types of Keys

### Primary Key

Uniquely identifies rows.

### Foreign Key

Creates relationship.

### Candidate Key

Possible primary keys.

### Composite Key

Multiple columns as key.

### Super Key

Set of unique columns.

### Alternate Key

Candidate key not chosen as primary.

## 15. What are views?

Views are virtual tables

## Example:
```ts
CREATE VIEW high_salary_emp AS
SELECT * FROM employees
WHERE salary > 50000;
```
### Advantages
- Security
- Simplifies queries
- Reusable

### Limitations:
- Complex Views may be slow
- Some views not updateable

### Variables in Views?

No. Views cannot contain variables.

## 16. VARCHAR vs NVARCHAR

### Varchar
- Stores ASCII
- Less Memory
- English Text

### NVARCHAR

- Stores Unicode
- More memory
- Multi Language text

Use NVARCHAR for international applications.

## 17. CHAR vs NCHAR

### CHAR
- Fixed Length ASCII
- Fasetr
### NCHAR
- FIXED Length Unicode
- Use More Memory

## 18. What are indexes? 
Indexes Improves Search Speed.

### Types:
### Clustered Index

Stores actual data physically. Only one clustered index.

### Non-Clustered Index

Separate structure pointing to data.

### Composite Index

Multiple columns.

### Unique Index

Prevents duplicates.

## 19. Relationships in SQL

### One-to-One
One user -> One Passport

### One-to-Many
One department --> Many employees

### Many-to-Many
Students <--> Courses

Uses Junction Table



## Function Vs Stored Procedure

### Function

- Return Value
- Used in Select
- Less flexible

### Stored Procedure
- May or May not Return 
- Can not use in Select
- More Flexible

## 23. Second Highest Salary





