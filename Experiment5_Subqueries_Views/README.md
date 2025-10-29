# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
<img width="1055" height="493" alt="image" src="https://github.com/user-attachments/assets/5fca8183-c229-4a1b-a1fe-d0542fa5dcce" />

```sql
SELECT *
FROM Grades g
WHERE grade = (
    SELECT MAX(grade)
    FROM Grades
    WHERE subject = g.subject
);

```

**Output:**
<img width="1303" height="418" alt="image" src="https://github.com/user-attachments/assets/46c62627-3b5b-461e-a2f9-66ccf3bb51ed" />


**Question 2**
---
<img width="1328" height="497" alt="image" src="https://github.com/user-attachments/assets/4ae5d134-46c3-408d-8834-d77313e15d81" />

```sql
SELECT *
FROM Grades g
WHERE grade = (
    SELECT MIN(grade)
    FROM Grades
    WHERE subject = g.subject
);

```

**Output:**

<img width="1314" height="432" alt="image" src="https://github.com/user-attachments/assets/e5506134-b008-4fb0-9f3e-84bb4928ff75" />


**Question 3**
---
<img width="1211" height="549" alt="image" src="https://github.com/user-attachments/assets/853fff59-182b-4e15-86b9-7000a7ad73c6" />



```sql
SELECT * FROM CUSTOMERS WHERE SALARY > 4500;

```

**Output:**
<img width="1253" height="424" alt="image" src="https://github.com/user-attachments/assets/253f23dc-21f4-40ba-a4f5-c468b31a82bd" />


**Question 4**
---
<img width="1148" height="589" alt="image" src="https://github.com/user-attachments/assets/1bfb0707-d897-4b18-8c5e-11297a0740d5" />

 

```sql
SELECT *
FROM customer
WHERE customer_id = (
    SELECT salesman_id - 2001
    FROM salesman
    WHERE name = 'Mc Lyon'
);

```

**Output:**

<img width="1282" height="300" alt="image" src="https://github.com/user-attachments/assets/426370ad-dd11-4267-9aa2-b91b6cedf300" />


**Question 5**
---
<img width="1450" height="585" alt="image" src="https://github.com/user-attachments/assets/02731e0b-a7c8-491d-bbc2-d974a8906fd5" />



```sql
SELECT orders.ord_no, orders.purch_amt, orders.ord_date, orders.customer_id, orders.salesman_id
FROM orders
JOIN salesman ON orders.salesman_id = salesman.salesman_id
WHERE salesman.city = 'London';

```

**Output:**
<img width="1226" height="429" alt="image" src="https://github.com/user-attachments/assets/6aa2d99d-b87f-4762-8005-5911f839e6e4" />


**Question 6**
---
<img width="1162" height="511" alt="image" src="https://github.com/user-attachments/assets/3871e4ff-b7bf-4714-baa8-7121324b2dc0" />


```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY < 2500;

```

**Output:**
<img width="1274" height="406" alt="image" src="https://github.com/user-attachments/assets/fe2d7b82-389d-4ee5-93ce-4eeb1ec64407" />


**Question 7**
---
<img width="1088" height="498" alt="image" src="https://github.com/user-attachments/assets/6881e340-1a86-4e76-b3bd-295187392f0c" />

```sql
SELECT * FROM Employee
WHERE age < (
    SELECT AVG(age) FROM Employee
    WHERE income > 1000000
);

```

**Output:**

<img width="1140" height="294" alt="image" src="https://github.com/user-attachments/assets/9b5e9f90-f7ed-4930-9953-4f1a97b95b3a" />


**Question 8**
---
<img width="1204" height="551" alt="image" src="https://github.com/user-attachments/assets/fae4e9c2-09f4-415c-85aa-1e496f876e9a" />



```sql
SELECT orders.ord_no, orders.purch_amt, orders.ord_date, orders.customer_id, orders.salesman_id
FROM orders
JOIN salesman ON orders.salesman_id = salesman.salesman_id
WHERE salesman.name = 'Paul Adam';

```

**Output:**

<img width="1154" height="311" alt="image" src="https://github.com/user-attachments/assets/17a218d5-0c1c-40c4-afc2-0923316d74b5" />


**Question 9**
---
<img width="1362" height="634" alt="image" src="https://github.com/user-attachments/assets/9787a073-8627-4038-b1eb-d936b3dd9021" />



```sql
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM orders
WHERE salesman_id IN (
    SELECT salesman_id
    FROM salesman
    WHERE city = 'New York'
);

```

**Output:**
<img width="1132" height="331" alt="image" src="https://github.com/user-attachments/assets/03aec3ed-5a4c-467e-b7ea-48b395e97907" />


**Question 10**
---
<img width="1226" height="588" alt="image" src="https://github.com/user-attachments/assets/0513e435-e1d0-4b8f-a316-6e7dae71f2a4" />

```sql
SELECT *
FROM CUSTOMERS
WHERE AGE < 30;

```

**Output:**

<img width="1024" height="439" alt="image" src="https://github.com/user-attachments/assets/78c30927-6423-4513-9f1d-8108c8d4a343" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
