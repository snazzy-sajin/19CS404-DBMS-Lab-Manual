# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
-- Create a table named Bonuses with the following constraints:
BonusID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
BonusAmount as REAL should be greater than 0.
BonusDate as DATE.
Reason as TEXT should not be NULL.

```sql
-- create table Bonuses(
BonusID INTEGER primary key,
EmployeeID INTEGER,
BonusAmount REAL check(BonusAmount>0),
BonusDate DATE,
Reason TEXT not NULL,
foreign key(EmployeeID) references Employees(EmployeeID));

```

**Output:**

<img width="1239" height="365" alt="image" src="https://github.com/user-attachments/assets/1e08c0d7-9edf-4853-88cc-40c76c6fd050" />


**Question 2**
---
-- Write a SQL Query  to Rename attribute "name" to "first_name"  and add mobilenumber as number ,DOB as Date,State as varchar(30) in the table Companies.

```sql
-- alter table Companies RENAME COLUMN name to first_name;
alter table Companies add COLUMN mobilenumber number;
alter table Companies add COLUMN DOB Date;
alter table Companies add COLUMN State varchar(30);

```

**Output:**

<img width="1233" height="491" alt="image" src="https://github.com/user-attachments/assets/c2377f4c-23d8-4474-88cd-602f29d6b481" />


**Question 3**
---
-- In the Student_details table, insert a student record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

RollNo      Name            Gender      Subject      MARKS
----------  ------------    ----------  ----------   ----------
205         Olivia Green    F
207         Liam Smith      M           Mathematics  85
208         Sophia Johnson  F           Science

```sql
-- INSERT INTO Student_details (RollNo,Name,Gender)values(205,'Olivia Green','F');
INSERT INTO Student_details (RollNo,Name,Gender,Subject,MARKS)values(207,'Liam Smith','M','Mathematics',85);
INSERT INTO Student_details (RollNo,Name,Gender,Subject)values(208,'Sophia Johnson','F','Science');

```

**Output:**

<img width="1226" height="358" alt="image" src="https://github.com/user-attachments/assets/d89e5164-12d2-4317-aba5-fe9cd5204567" />


**Question 4**
---
-- Write an SQL query to add two new columns, first_name and last_name, to the table employee. Both columns should have a data type of varchar(50).

```sql
-- alter table employee add column first_name varchar(50);
alter table employee add column last_name varchar(50);
```

**Output:**

<img width="1230" height="388" alt="image" src="https://github.com/user-attachments/assets/ff6fb5e4-ccb2-4995-a37f-9b017e29c31b" />


**Question 5**
---
-- Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.

```sql
-- create table Employees(
EmployeeID integer primary key,
DepartmentID integer,
FirstName VARCHAR(255) NOT NULL,
LastName VARCHAR(255) NOT NULL,
Email VARCHAR(255) UNIQUE,
Salary DECIMAL(10,2) check(Salary>0),
foreign key (DepartmentID ) references DepartmentID(Departments ));


```

**Output:**

<img width="1054" height="317" alt="image" src="https://github.com/user-attachments/assets/29b6f9ba-55d5-4056-b00a-9b0509bf96df" />


**Question 6**
---
-- Insert all employees from Former_employees into Employee

Table attributes are EmployeeID, Name, Department, Salary

```sql
-- insert into Employee(EmployeeID,Name,Department,Salary) select EmployeeID,Name,Department,Salary from Former_employees ;
```

**Output:**

<img width="1169" height="185" alt="image" src="https://github.com/user-attachments/assets/b98848c4-edcc-4dd0-add3-05464b350fd9" />


**Question 7**
---
-- Create a table named Products with the following constraints:
ProductID as INTEGER should be the primary key.
ProductName as TEXT should be unique and not NULL.
Price as REAL should be greater than 0.
StockQuantity as INTEGER should be non-negative.

```sql
-- create table Products (
ProductID INTEGER primary key,
ProductName TEXT UNIQUE not NULL,
Price real check(Price > 0),
StockQuantity integer check(StockQuantity>=0));
```

**Output:**

<img width="1219" height="365" alt="image" src="https://github.com/user-attachments/assets/400ca550-df76-4f1f-b684-abdeaafbd329" />


**Question 8**
---
-- Insert the below data into the Customers table, allowing the City and ZipCode columns to take their default values.

CustomerID  Name          Address
----------  ------------  ----------
304         Peter Parker  Spider St      

Note: The City and ZipCode columns will use their default values.

```sql
-- insert into Customers(CustomerID,Name,Address) values(304,"Peter Parker","Spider St");
```

**Output:**

<img width="1210" height="321" alt="image" src="https://github.com/user-attachments/assets/40c973a4-050e-4595-ac0a-427b6c559cd0" />


**Question 9**
---
-- Create a table named Departments with the following columns:

DepartmentID as INTEGER
DepartmentName as TEXT

```sql
--create table Departments (
DepartmentID INTEGER,
DepartmentName TEXT);
```

**Output:**

<img width="1236" height="376" alt="image" src="https://github.com/user-attachments/assets/b36403a0-ea2b-4301-9c2d-1db9e4d0f85e" />


**Question 10**
---
--Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

```sql
-- create table ProjectAssignments (
AssignmentID INTEGER primary key,
EmployeeID INTEGER,
ProjectID INTEGER ,
AssignmentDate DATE NOT NULL,
foreign key (EmployeeID) references Employees(EmployeeID),
foreign key (ProjectID) references Projects(ProjectID));
```

**Output:**

<img width="1236" height="367" alt="image" src="https://github.com/user-attachments/assets/bb65e5c0-db91-4970-a62a-506c2e4569e4" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
