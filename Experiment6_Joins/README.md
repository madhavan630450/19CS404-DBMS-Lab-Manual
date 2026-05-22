# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**

Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), the
"cust_name," "city," "grade," and "salesman_id" columns from the "customer" table (aliased as "c"), with a left join on the
"salesman_id" column and a condition filtering for customers with a grade less than or equal to 100.

```
select s.name,c.cust_name, c.city,c.grade,c.salesman_id
from Salesman s
left join Customer c
on c.salesman_id = s.salesman_id
where c.grade <=100;
```

**Output:**

<img width="841" height="264" alt="image" src="https://github.com/user-attachments/assets/1ade7684-cf36-4c1f-bb38-c68943e0abcc" />


**Question 2**

From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade,
Salesman, salesmancity. The result should be ordered by ascending customer_id. 

```
select  c.cust_name, c.city,c.grade,s.name as Salesman,s.city
from Customer c
join salesman s
on c.salesman_id = s.salesman_id
where c.grade<300
order by customer_id;
```

**Output:**

<img width="833" height="348" alt="image" src="https://github.com/user-attachments/assets/a02f8a41-1438-4068-88b7-97fead525090" />


**Question 3**

From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.

```
SELECT
    c.cust_name AS "Customer Name",
    c.city,
    s.name AS "Salesman",
    s.commission
FROM customer c
JOIN salesman s
ON c.salesman_id = s.salesman_id;

```
**Output:**

<img width="1239" height="310" alt="image" src="https://github.com/user-attachments/assets/bf8126b2-1480-4f17-a201-3b78bea5ecd6" />


**Question 4**

Write the SQL query that achieves the selection of all columns from the "nurses" table (aliased as "n") and the
"department_name" column from the "departments" table, with an inner join on the "department_id" column.

```
select n.*,
d.department_name
from NURSES n
inner join DEPARTMENTS d
on n.department_id = d.department_id;
```

**Output:**

<img width="834" height="236" alt="image" src="https://github.com/user-attachments/assets/4504914e-fde5-43e6-af67-2db376c5ce1b" />


**Question 5**

From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no,
purch_amt, cust_name, city


```
select o.ord_no ,o.purch_amt,c.cust_name,c.city
from orders o
left join customer c
on o.customer_id =c.customer_id
where o.purch_amt between 500 and 2000;
```

**Output:**

<img width="838" height="197" alt="image" src="https://github.com/user-attachments/assets/e455a4af-d152-4ed3-b9f6-20af30ceb719" />


**Question 6**

Write a SQL statement to join the tables salesman, customer and orders so that the same column of each table appears once and only
the relational rows are returned.

```
select o.ord_no,o. purch_amt , o.ord_date,c.cust_name,c.city as customer_city , c.grade, s.name as  salesman_na
from orders o
left outer join customer c
on c.customer_id = o. customer_id
left outer join salesman s
on s. salesman_id =o. salesman_id ;
```

**Output:**

<img width="829" height="820" alt="image" src="https://github.com/user-attachments/assets/7340081c-dcbc-4021-b8b9-c3092719d103" />


**Question 7**

Write an SQL query to retrieve all columns from the 'customer' table (aliased as 'c') using a LEFT JOIN with the 'orders' table on
the 'customer_id' column, and filter the results to include only those orders placed between '2012-07-01' and '2012-07-30'.

```
select c.*
from customer c
left join orders o
on c.customer_id =o.customer_id
where o.ord_date between '2012-07-01' and  '2012-07-30';
```

**Output:**

<img width="838" height="295" alt="image" src="https://github.com/user-attachments/assets/78551e07-d7b7-4ef8-9474-091bddf45bf8" />


**Question 8**

From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id.

```
SELECT
    c.cust_name,
    c.city,
    c.grade,
    s.name AS Salesman,
    s.city
FROM customer c
JOIN salesman s
ON c.salesman_id = s.salesman_id
WHERE c.grade < 300
ORDER BY c.customer_id ASC;
```

**Output:**

<img width="844" height="257" alt="image" src="https://github.com/user-attachments/assets/634d708b-97d6-4cdd-bb2c-45edd736ab73" />


**Question 9**

Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all
columns from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column.

```
select p.first_name as patient_name, t.*
from PATIENTS p
inner join test_results t
on p.patient_id = t.patient_id;
```

**Output:**

<img width="832" height="233" alt="image" src="https://github.com/user-attachments/assets/5a5cbc60-5530-4ffa-879e-cc1c3aca5555" />


**Question 10**

Write the SQL query that accomplishes the selection of all columns from the "patients" table and the first name of doctors from
the "doctors" table, with an inner join on the "doctor_id" column.

```
select p.*, d.first_name as doctor_name
from PATIENTS p
inner join DOCTORS d
on p.doctor_id = d.doctor_id;
```
**Output:**

<img width="798" height="309" alt="image" src="https://github.com/user-attachments/assets/a90a80dd-ac2e-4eab-9ce6-8175d86d2633" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
