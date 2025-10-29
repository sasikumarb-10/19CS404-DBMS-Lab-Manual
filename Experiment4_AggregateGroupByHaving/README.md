# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
<img width="1422" height="495" alt="image" src="https://github.com/user-attachments/assets/584fa548-dcba-4c30-b71f-d2eddf464cb9" />


```sql
select 
  SUBSTR(Email,INSTR(Email,'@')+1) as EmailDomain,
  count(*) as TotalPatients
from Patients
group by EmailDomain;
```

**Output:**

<img width="1245" height="423" alt="image" src="https://github.com/user-attachments/assets/08532096-d1fd-4736-865a-37a8422216b6" />


**Question 2**
---<img width="1408" height="662" alt="image" src="https://github.com/user-attachments/assets/2ad29a13-9ab3-40fe-a94e-7328c9029c26" />


```sql
Select 
   InsuranceCompany,
   count(*) as TotalExpiredPatients
from Insurance
where TRIM(SUBSTR(ValidityPeriod, INSTR(ValidityPeriod,'to')+2)) < DATE('now')
group by InsuranceCompany;
```

**Output:**

<img width="1322" height="768" alt="image" src="https://github.com/user-attachments/assets/9e267e49-ae7f-4f93-ac2d-7b5545c57039" />


**Question 3**
---
<img width="1426" height="593" alt="image" src="https://github.com/user-attachments/assets/592b8437-db24-4d9c-9c3e-48c60730922f" />


```sql
select
    DoctorID,
    strftime('%H:%M', AppointmentDateTime) as TimeSlot,
    count(*) as TotalAppointments
from Appointments
group by DoctorID, TimeSlot
order by TotalAppointments DESC, DoctorID;
```

**Output:**
<img width="1403" height="735" alt="image" src="https://github.com/user-attachments/assets/8621fcba-a007-40c2-a47b-fbdcc853ecec" />


**Question 4**
---
<img width="1148" height="474" alt="image" src="https://github.com/user-attachments/assets/04504278-639f-490c-a466-1eee96276abe" />


```sql
select count(*) as employees_count
from employee
where income>50000;
```

**Output:**
<img width="1350" height="363" alt="image" src="https://github.com/user-attachments/assets/832142b1-c38d-4dbc-9957-3aea8fa28b3d" />


**Question 5**
---
<img width="1282" height="566" alt="image" src="https://github.com/user-attachments/assets/12a9f344-b859-4fa1-a680-5bfa2a5b2f5c" />


```sql
select name as fruit_name, inventory as lowest_quantity from fruits
where 
   inventory=(
     select
        MIN(inventory)
     from 
        fruits
    );
```

**Output:**

<img width="1353" height="336" alt="image" src="https://github.com/user-attachments/assets/e7e471fc-a815-40b4-8fc4-1954a7272abb" />


**Question 6**
---
<img width="1282" height="485" alt="image" src="https://github.com/user-attachments/assets/660de8ba-0bbe-4e3b-a01f-59c1d84ebfe8" />


```sql
select SUM(income) as total_income from employee
where age>=40;
```

**Output:**
<img width="1289" height="271" alt="image" src="https://github.com/user-attachments/assets/553b7d99-25c3-45cd-a2d5-514cd47d70f5" />


**Question 7**
---
<img width="1318" height="474" alt="image" src="https://github.com/user-attachments/assets/289c30d4-4faf-43fe-9b78-5c9902b6b88a" />


```sql
select max(age)-min(age) as age_difference from employee;
```

**Output:**
<img width="1364" height="385" alt="image" src="https://github.com/user-attachments/assets/0b1759b3-614c-4d37-adb5-2df9869a4291" />


**Question 8**
---
<img width="1442" height="487" alt="image" src="https://github.com/user-attachments/assets/6f8f2a57-c119-4e2b-902a-4c73875eca58" />


```sql
select (age/5)*5 as age_group, AVG(age) from customer1
group by age_group
Having avg(age)<24;
```

**Output:**

<img width="1398" height="369" alt="image" src="https://github.com/user-attachments/assets/4af52807-a132-4794-a37b-4dd5317a5902" />


**Question 9**
---
<img width="1421" height="501" alt="image" src="https://github.com/user-attachments/assets/8b74e688-1834-449b-a19c-496bda091887" />


```sql
select age, MAX(income) from employee
group by age
having MAX(income)>2000000;
```

**Output:**

<img width="1399" height="390" alt="image" src="https://github.com/user-attachments/assets/54d6484b-d355-4e4a-ab5a-8a61f52f7d9b" />


**Question 10**
---<img width="1392" height="532" alt="image" src="https://github.com/user-attachments/assets/a64637c5-11c2-46aa-be78-5fd5a8160a4f" />

```sql
select occupation, AVG(workhour) as "AVG(workhour)" from employee1
group by occupation
having AVG(workhour) between 10 and 12;
```
**Output:**

<img width="1512" height="422" alt="Screenshot 2025-10-29 105259" src="https://github.com/user-attachments/assets/2176756e-4be1-4ff6-9349-4dbea03c7ca6" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
