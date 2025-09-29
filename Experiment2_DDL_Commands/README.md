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
Create a table named Tasks with the following columns:

TaskID as INTEGER

TaskName as TEXT

DueDate as DATE

```sql
create table Tasks(
    TaskID INTEGER,
    TaskName TEXT,
    DueDate DATE
);
```

**Output:**

<img width="1328" height="295" alt="image" src="https://github.com/user-attachments/assets/ffdef3b2-e8b5-4cd2-bac7-95096d02a401" />


**Question 2**
---
Create a new table named item with the following specifications and constraints:

item_id as TEXT and as primary key.

item_desc as TEXT.

rate as INTEGER.

icom_id as TEXT with a length of 4.

icom_id is a foreign key referencing com_id in the company table.

The foreign key should cascade updates and deletes.

item_desc and rate should not accept NULL.

```sql
create table item(
    item_id TEXT PRIMARY KEY,
    item_desc TEXT NOT NULL,
    rate INTEGER NOT NULL,
    icom_id TEXT(4),
    
    FOREIGN KEY (icom_id) REFERENCES company(com_id) ON UPDATE CASCADE ON DELETE CASCADE
);
```

**Output:**



**Question 3**
---
Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.

InvoiceDate as DATE.

Amount as REAL should be greater than 0.

DueDate as DATE should be greater than the InvoiceDate.

OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
create table Invoices(
      InvoiceID integer primary key,
      InvoiceDate Date,
      Amount real not null check (Amount>0),
      DueDate Date not null check (DueDate>InvoiceDate),
      OrderID integer,
      
      foreign key (OrderId) references Orders(OrderID)
);
```

**Output:**

<img width="1305" height="160" alt="image" src="https://github.com/user-attachments/assets/4e10226a-b846-427b-9538-fb5a38d89633" />


**Question 4**
---
create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.

```sql
create table jobs(
     job_id int primary key,
     job_title varchar(255) default '',
     min_salary int default 8000,
     max_salary int default null
);
```

**Output:**

<img width="1135" height="140" alt="image" src="https://github.com/user-attachments/assets/1937dff1-5ce8-4723-8e74-4afda1358a1f" />

**Question 5**
---
In the Employee table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

| EmployeeID | Name          | Position    | Department | Salary |
|------------|---------------|-------------|------------|--------|
| 5          | George Clark  | Consultant  | NULL       | NULL   |
| 7          | Noah Davis    | Manager     | HR         | 60000  |
| 8          | Ava Miller    | Consultant  | IT         | NULL   |


```sql
insert into Employee (EmployeeID,Name,Position,Department,Salary)
values (5,'George Clark','Consultant',NULL,NULL);

insert into Employee (EmployeeID,Name,Position,Department,Salary)
values (7,'Noah Davis','Manager','HR',60000);

insert into Employee (EmployeeID,Name,Position,Department,Salary)
values (8,'Ava Miller','Consultant','IT',NULL); 
```

**Output:**
<img width="1303" height="227" alt="image" src="https://github.com/user-attachments/assets/6adb7569-35a5-4608-801d-61065aabd1fb" />



**Question 6**
---
Write an SQL query to add two new columns, designation and net_salary, to the table Companies. The designation column should have a data type of varchar(50), and the net_salary column should have a data type of number.

```sql
ALTER TABLE Companies 
ADD COLUMN designation varchar(50);

ALTER TABLE Companies
ADD COLUMN net_salary number;
```

**Output:**
<img width="1298" height="355" alt="Screenshot 2025-09-29 134620" src="https://github.com/user-attachments/assets/a7c90b6a-cace-4e5a-ab38-54498306ad2a" />


**Question 7**
---
Write a SQL Query to add an attribute designation in the employee table with the data type VARCHAR(50).

```sql
ALTER TABLE employee add column designation varchar(50);
```

**Output:**

<img width="1297" height="311" alt="image" src="https://github.com/user-attachments/assets/c412fc20-4e83-47d9-b431-8652a750c876" />


**Question 8**
---
Insert a customer with CustomerID 301, Name Michael Jordan, Address 123 Maple St, City Chicago, and ZipCode 60616 into the Customers table.

```sql
insert into Customers (CustomerID, Name, Address, City, Zipcode)
values(301, 'Michael Jordan', '123 Maple St', 'Chicago',60616);
```

**Output:**

<img width="1297" height="223" alt="image" src="https://github.com/user-attachments/assets/a1de874b-7257-4e61-a3d9-a2c4c552ae95" />


**Question 9**
---
Create a new table named orders with the following specifications:

ord_id as TEXT with a length of 4.

item_id as TEXT.

ord_date as DATE.

ord_qty as INTEGER.

cost as INTEGER.

The primary key is a composite key consisting of item_id and ord_date.

ord_id and item_id should not accept NULL

```sql
create table orders(
    ord_id TEXT not null check (length(ord_id)=4),
    item_id TEXT not null,
    ord_date DATE,
    ord_qty INTeger,
    cost integer,
    primary key(item_id, ord_date)
);
```

**Output:**

<img width="1352" height="325" alt="image" src="https://github.com/user-attachments/assets/6300056f-e2b0-40be-921f-ad1031e15b8e" />


**Question 10**
---
Insert all products from Discontinued_products into Products.

Table attributes are ProductID, ProductName, Price, Stock

```sql
insert into Products select * from Discontinued_products;
```

**Output:**
<img width="1080" height="302" alt="image" src="https://github.com/user-attachments/assets/ecb5dfb5-ea44-47c8-96ef-f01b9fcbf82f" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
