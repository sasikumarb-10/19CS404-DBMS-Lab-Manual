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
**Question 1**
--
Write a SQL statement to update the `product_name` as 'Grapefruit' whose `product_id` is 4 in the `products` table.

**products table**

| product_id | product_name | category_id | availability |
|-------------|---------------|--------------|---------------|


```sql
UPDATE products
SET product_name = 'Grapefruit'
WHERE product_id = 4;

```

**Output:**

<img width="1238" height="262" alt="image" src="https://github.com/user-attachments/assets/55d34b1c-6cd8-4da8-869e-0e47c033888b" />


**Question 2**
---
<img width="1120" height="523" alt="image" src="https://github.com/user-attachments/assets/04e2febf-9b0c-4629-8ab2-145ef7dc51a6" />


```sql
update Products
set sell_price=sell_price*1.15
where quantity<50 and supplier_id=10;
```

**Output:**
<img width="1295" height="243" alt="image" src="https://github.com/user-attachments/assets/18180597-b006-4db7-b5c1-34accbd447ad" />


**Question 3**
---
<img width="1232" height="663" alt="image" src="https://github.com/user-attachments/assets/2a06ec57-a8b7-4a82-afd3-5eef2ed799e2" />


```sql
update Employees
set salary=
    case
       when department_id=40 then CAST(ROUND(salary*1.25)as int)
       when department_id=90 then CAST(ROUND(salary*1.15)as int)
       when department_id=110 then CAST(ROUND(salary*1.10)as int)
       else salary
    end
where department_id IN (40,90,110);
```

**Output:**



**Question 4**
---
<img width="983" height="390" alt="image" src="https://github.com/user-attachments/assets/4305db3c-92e0-473d-925d-c0e0427f8a3f" />


```sql
update Products 
set reorder_lvl=reorder_lvl*0.70
where cost_price>50 and quantity<100;
```

**Output:**
<img width="1431" height="337" alt="image" src="https://github.com/user-attachments/assets/8e66a079-2cfd-4b7b-8c18-7d933e26504c" />


**Question 5**
---
<img width="751" height="193" alt="image" src="https://github.com/user-attachments/assets/6ef0c9e6-d20a-4a56-b7d4-e773e65e6740" />


```sql
update products 
set availability=availability*2
where product_id=1;
```

**Output:**
<img width="1267" height="201" alt="image" src="https://github.com/user-attachments/assets/2f94f6f3-12c1-4c62-934c-5725ba87ec9d" />

**Question 6**
---
<img width="1231" height="510" alt="image" src="https://github.com/user-attachments/assets/22e7b7cf-d8be-413a-8b67-6af83aefa714" />


```sql
delete from customer where grade<2;
```

**Output:**

<img width="1101" height="411" alt="image" src="https://github.com/user-attachments/assets/c59c4d74-fdca-423a-bac3-f717ee3d9853" />


**Question 7**
---<img width="1331" height="243" alt="image" src="https://github.com/user-attachments/assets/ab6256fd-bfca-4ead-bcd4-7b469f24a7e0" />


```sql
delete from customer where OPENING_AMT between 4000 and 6000;
```

**Output:**

<img width="1358" height="533" alt="image" src="https://github.com/user-attachments/assets/1db08354-b061-4ca4-ae81-861df23165e5" />


**Question 8**
---
<img width="981" height="184" alt="image" src="https://github.com/user-attachments/assets/a888806e-266d-4cf1-a827-54f2602e0fd0" />


```sql
delete from Customer where (Grade>2 and PAYMENT_AMT < (select AVG(PAYMENT_AMT) from Customer))
or OUTSTANDING_AMT>8000;
```

**Output:**

<img width="1314" height="231" alt="image" src="https://github.com/user-attachments/assets/da85e1dc-3573-49b2-b517-2d26badf49b5" />


**Question 9**
---
<img width="774" height="189" alt="image" src="https://github.com/user-attachments/assets/7bf17d07-e75b-4212-945a-20a1349ff303" />


```sql
DELETE from Customer where CUST_COUNTRY='UK' and WORKING_AREA='London' and GRADE<3;
```

**Output:**

<img width="1352" height="171" alt="image" src="https://github.com/user-attachments/assets/19ac31f6-b339-4182-a7e0-98aba5234a6f" />


**Question 10**
---
<img width="839" height="243" alt="image" src="https://github.com/user-attachments/assets/7923a22f-dd3a-438d-ad57-107ee71a4fe0" />


```sql
DELETE FroM Customer where GRADE<>3;
```

**Output:**

<img width="791" height="198" alt="image" src="https://github.com/user-attachments/assets/db91d3d6-f291-4379-88ae-28e5d92e780b" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
