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
-- Write an SQL command can to add a column named email of type TEXT to the customers table

```sql
ALTER table Customers 
ADD COLUMN email TEXT;
```

**Output:**

<img width="870" height="373" alt="image" src="https://github.com/user-attachments/assets/aab95464-f064-4f2b-93ce-55e86e013ad1" />


**Question 2**
---
 Write a SQL Query for inserting the below values in the table Customers

ID               NAME             AGE  ADDRESS     SALARY      
---------------  ---------------  ---  ----------  ----------  
1                Ramesh           32   Ahmedabad   2000
2                Khilan           25   Delhi       1500
3                Kaushik          23   Kota        2000

```
insert into  Customers(ID,NAME,AGE,ADDRESS,SALARY) VALUES (1,"Ramesh",32,"Ahmedabad",2000),
(2,"Khilan",25,"Delhi",1500),(3,"Kaushik",23,"Kota",2000)
```

**Output:**

<img width="863" height="378" alt="image" src="https://github.com/user-attachments/assets/3d32bd53-c72b-4833-97c3-4239e4f67efd" />


**Question 3**
---
Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

```sql
CREATE TABLE ProjectAssignments(
    AssignmentID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    ProjectID  INTEGER,
    AssignmentDate DATE NoT NULL,
    
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
    FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)
);
```

**Output:**

<img width="858" height="364" alt="image" src="https://github.com/user-attachments/assets/dedc7761-dd90-45b0-94d9-db39aae25b2b" />


**Question 4**
---
Write a SQL query to Add a new column Mobilenumber as number in the Student_details table.

Sample table: Student_details

 cid              name             type             notnu  dflt_value  pk
---------------  ---------------  ---------------  -----  ----------  ----------
0                RollNo           int              0                  1
1                Name             VARCHAR(100)     1                  0
2                Gender           TEXT             1                  0
3                Subject          VARCHAR(30)      0                  0
4                MARKS            INT (3)          0                  0

```sql
ALTER table  Student_details  
ADD COLUMN Mobilenumber number;
```

**Output:**

<img width="1197" height="413" alt="image" src="https://github.com/user-attachments/assets/eb91d111-8db8-43f8-8415-fd46b5cbd2cc" />


**Question 5**
---
Create a table named Employees with the following columns:

EmployeeID as INTEGER
FirstName as TEXT
LastName as TEXT
HireDate as DATE

```sql
create table  Employees(
     EmployeeID INTEGER,
     FirstName TEXT,
     LastName TEXT,
    HireDate DATE
);
```

**Output:**

<img width="1231" height="408" alt="image" src="https://github.com/user-attachments/assets/f7652479-35cd-4612-b846-85f9a34db1b2" />


**Question 6**
---
Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.

```sql
create table Department(
DepartmentID  integer primary key,
DepartmentName  text unique not null,
Location  TEXT
);
```

**Output:**

<img width="1237" height="380" alt="image" src="https://github.com/user-attachments/assets/29ca7fda-f23f-44f4-a761-0fff66f6816a" />


**Question 7**
---
Insert the below data into the Employee table, allowing the Department and Salary columns to take their default values.

EmployeeID  Name         Position
----------  -----------  ----------
4           Emily White  Analyst

Note: The Department and Salary columns will use their default values.    
```sql
insert into Employee (EmployeeID,Name,Position) 
values (4,"Emily White","Analyst");
```

**Output:**

<img width="1234" height="407" alt="image" src="https://github.com/user-attachments/assets/c85822fc-0e00-467c-82d5-967e81c46702" />


**Question 8**
---
Create a table named Bonuses with the following constraints:
BonusID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
BonusAmount as REAL should be greater than 0.
BonusDate as DATE.
Reason as TEXT should not be NULL.

```sql
create table Bonuses(
BonusID integer primary key,
EmployeeID integer ,
BonusAmount real check (BonusAmount > 0),
BonusDate date,
Reason text not null,
foreign key (EmployeeID) references Employees(EmployeeID)

);
```

**Output:**

<img width="1222" height="362" alt="image" src="https://github.com/user-attachments/assets/14a866e1-3bbe-4c48-8682-f405699365c4" />


**Question 9**
---
Insert all students from Archived_students table into the Student_details table.

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           RollNo      INT           0                       1
1           Name        VARCHAR(100)  0                       0
2           Gender      VARCHAR(10)   0                       0
3           Subject     VARCHAR(50)   0                       0
4           MARKS       INT           0                       0
```sql
insert into Student_details (RollNo,Name,Gender,Subject,MARKS)
select RollNo,Name,Gender,Subject,MARKS
from Archived_students 
```

**Output:**

<img width="1226" height="378" alt="image" src="https://github.com/user-attachments/assets/f99bc044-a355-4892-9095-aef417daf912" />


**Question 10**
---
Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.

```sql
create table Employees(
    EmployeeID integer primary key,
    FirstName text not null,
    LastName text not null,
    Email text unique ,
    Salary integer check(Salary>0),
    DepartmentID integer,
    foreign key (EmployeeID) references Departments(DepartmentID)
);
```

**Output:**

<img width="1225" height="517" alt="image" src="https://github.com/user-attachments/assets/0d682a51-140a-4eab-b791-60b591e0a21f" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
