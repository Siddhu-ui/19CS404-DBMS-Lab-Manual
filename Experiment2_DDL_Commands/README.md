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
<img width="1193" height="354" alt="image" src="https://github.com/user-attachments/assets/8da958c2-a907-459c-b928-d41b7855b705" />


```sql
CREATE TABLE Employees(
    EmployeeID Integer PRIMARY KEY,
    FirstName TEXT NOT NULL,
    LastName TEXT NOT NULL,
    Email TEXT UNIQUE,
    Salary REAL CHECK (Salary > 0),
    DepartmentID INTEGER,
    FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);
```

**Output:**

<img width="1603" height="396" alt="image" src="https://github.com/user-attachments/assets/4d97faa9-0c57-4f6a-ad2b-229c524fa3b1" />


**Question 2**
---
<img width="1048" height="438" alt="image" src="https://github.com/user-attachments/assets/969d9392-fbf2-4a7f-af3c-4c2369c11d55" />


```sql
CREATE TABLE Events(
EventID INTEGER,
EventName TEXT,
EventDate DATE
);
```

**Output:**

<img width="1612" height="366" alt="image" src="https://github.com/user-attachments/assets/cf6d99f3-5f29-47e9-b410-7de0ac6d0501" />


**Question 3**
---
<img width="797" height="352" alt="image" src="https://github.com/user-attachments/assets/064490b4-417b-4508-95fe-ea103e1dc7ca" />


```sql
INSERT INTO Customers (CustomerID, Name, Address)
VALUES (304,'Peter Parker', 'Spider St');
```

**Output:**

<img width="1386" height="425" alt="image" src="https://github.com/user-attachments/assets/1e6c4a10-0338-4e6f-98bc-b9ab76d60286" />


**Question 4**
---
<img width="1008" height="345" alt="image" src="https://github.com/user-attachments/assets/33528e68-35db-4949-84f9-f17c1729db08" />


```sql
CREATE TABLE Invoices(
InvoiceID INTEGER PRIMARY KEY,
InvoiceDate DATE,
DueDate DATE,
Amount REAL CHECK (Amount > 0),
CHECK (DueDate > InvoiceDate)
);
```

**Output:**

<img width="1600" height="351" alt="image" src="https://github.com/user-attachments/assets/03871872-aa8b-49b3-a21d-53d707ae35c9" />


**Question 5**
---
<img width="1066" height="612" alt="image" src="https://github.com/user-attachments/assets/697b6d8a-df17-461a-b505-bc64e4a7c6c1" />


```sql
ALTER TABLE Companies ADD COLUMN designation varchar(50);
ALTER TABLE Companies ADD COLUMN net_salary number;
ALTER TABLE Companies ADD COLUMN dob date;
```

**Output:**

<img width="1848" height="472" alt="image" src="https://github.com/user-attachments/assets/35d9af50-892d-4ad4-ae74-3818de17067c" />


**Question 6**
---
<img width="908" height="359" alt="image" src="https://github.com/user-attachments/assets/996d0d91-0cd8-42f2-8ec4-6a680081f70b" />


```sql
INSERT INTO Customers (CustomerID, Name, Address, Email)
SELECT CustomerID, Name, Address, Email
FROM Old_customers;
```

**Output:**

<img width="1689" height="368" alt="image" src="https://github.com/user-attachments/assets/0ae8f4fd-9804-4c3a-940b-856edb1136a4" />


**Question 7**
---
<img width="1513" height="390" alt="image" src="https://github.com/user-attachments/assets/b79686f2-4799-4fe4-b145-f31da66ca347" />


```sql
CREATE TABLE Products(
ProductID INTEGER PRIMARY KEY,
ProductName TEXT UNIQUE NOT NULL,
Price REAL CHECK (Price > 0),
StockQuantity INTEGER CHECK (StockQuantity >= 0)
);
```

**Output:**

<img width="1824" height="271" alt="image" src="https://github.com/user-attachments/assets/228e2470-f1d9-40ab-a26f-7aa052af6d86" />


**Question 8**
---
<img width="868" height="498" alt="image" src="https://github.com/user-attachments/assets/9612b945-3729-4a78-a0ab-9d5db48274e5" />


```sql
INSERT INTO Customers (ID, NAME, AGE, ADDRESS, SALARY) VALUES
(1, 'Ramesh', 32, 'Ahmedabad', 2000),
(2, 'Khilan', 25, 'Delhi', 1500),
(3, 'Kaushik',23, 'Kota', 2000);
```

**Output:**

<img width="1758" height="419" alt="image" src="https://github.com/user-attachments/assets/98862823-75f6-4779-96f8-78af6be976f0" />



**Question 9**
---
<img width="1597" height="315" alt="image" src="https://github.com/user-attachments/assets/87731bc1-d025-4e35-9ce4-4e780607bf93" />


```sql
ALTER TABLE Student_details
ADD COLUMN email TEXT NOT NULL DEFAULT 'Invalid';

```

**Output:**

<img width="1704" height="318" alt="image" src="https://github.com/user-attachments/assets/ce4698b0-e52c-49f8-8519-d51595d1ab56" />


**Question 10**
---
<img width="1648" height="397" alt="image" src="https://github.com/user-attachments/assets/447413c7-52c8-45ec-9d19-81f1517a8e12" />


```sql
CREATE TABLE ProjectAssignments (
    AssignmentID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    ProjectID INTEGER,
    AssignmentDate DATE NOT NULL,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
    FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)
);
    
```

**Output:**

<img width="1767" height="284" alt="image" src="https://github.com/user-attachments/assets/3ad8c535-6e8b-4d16-aef4-76c636b7659a" />




## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
