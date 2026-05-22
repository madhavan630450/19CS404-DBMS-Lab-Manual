# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
### Question 1
--
--Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.

```sql
-- UPDATE Suppliers
set address='58 Lakeview, Magnolia'
where supplier_id=5;
```

### Output:

![image](https://github.com/user-attachments/assets/781d2536-1091-44dc-9613-398ae3f13205)


### Question 2
---
-- Write a SQL statement to double the availability of the product with product_id 1.

```sql
update products
set availability=availability*2
where product_id=1;
```

### Output:
![image](https://github.com/user-attachments/assets/36bdadbc-1095-4879-bf47-d984c622de7b)


### Question 3
---
--  Update the total selling price to quantity sold multiplied by updated selling price per unit where product id is 10 in the sales table.

```sql
update SALES
set total_sell_price=quantity*sell_price
where product_id=10;
```

### Output:
![image](https://github.com/user-attachments/assets/ca547d63-5b6f-42e8-8fa9-520e35431f5c)


### Question 4
---
-- Write a SQL query to Delete customers from 'customer' table where 'GRADE' is not equal to 3.

```sql
DELETE FROM Customer
where GRADE<>3;
```

### Output:
![image](https://github.com/user-attachments/assets/ba99906b-bbb2-4834-8383-621acb16548f)


### Question 5
---
--Write a SQL query to delete a doctor from Doctors table whose Specialization is 'Pediatrics' and First name is 'Michael'.

```sql
DELETE FROM Doctors
where specialization='Pediatrics' and first_name='Michael';
```

### Output:
![image](https://github.com/user-attachments/assets/c08ad2ca-5121-4fbb-9eb4-fd9dbf526915)


### Question 6
---
--Write a SQL query to Delete customers from 'customer' table where 'GRADE' is less than 2.
```sql
DELETE FROM Customer 
where GRADE<2;
```

### Output:

![image](https://github.com/user-attachments/assets/d0a5a975-1384-42d1-9dd0-e36c036da8c0)

### Question 7
---
-- Write a SQL query to label rows in the Calculations table as 'Even' if value1 is even, otherwise 'Odd'.

```sql
SELECT id,value1,
case when (value1%2=0) THEN 'Even' else 'Odd'
end as parity
from Calculations;
```

### Output:=
![image](https://github.com/user-attachments/assets/9d3a847c-16d3-4b6f-a9dd-3a927382060a)


### Question 8
---
--Write a SQL query to find all employees who were hired in the year 2022 from emp table.

```sql
SELECT * from emp
where hiredate like '%2022%';
```

### Output:
![image](https://github.com/user-attachments/assets/8d0fb572-e9ab-422c-9420-93a177cd0b45)


### Question 9
---
-- Write a query to fetch the number of employees working in the department ‘HR’.
```sql
SELECT COUNT(*) 
from EmployeeInfo
where department='HR';
```

### Output:
![image](https://github.com/user-attachments/assets/649f436b-38e1-404e-a848-2920e73a6667)


### Question 10
---
--Write a SQL query to calculate the discounted price for products where the discount percentage is greater than 0, and order the results by discounted_price in ascending order. Return product_id, original_price, discount_percentage, and discounted_price.
```sql
SELECT product_id,original_price,discount_percentage,original_price*(1-discount_percentage) as discounted_price
from Products
where discount_percentage>0 
ORDER BY discounted_price ASC;
```

### Output:
![image](https://github.com/user-attachments/assets/d0fe0ae6-63a3-40d9-8105-b79dba0adb99)

## 


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
