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
How many appointments are scheduled for each doctor?

Sample table:Appointments Table

```sql
select DoctorID,count(*) as TotalAppointments from Appointments
group by DoctorID

```

**Output:**

![Output1]![image](https://github.com/user-attachments/assets/ce80c9c0-3353-41ab-9fb6-d4b5eebb1493)


**Question 2**
---
What is the most common diagnosis among patients?

Sample table:MedicalRecords Table

```sql
select Diagnosis , count(*) as DiagnosisCount from MedicalRecords
group by Diagnosis
order by DiagnosisCount DESC
limit 1
```

**Output:**

![Output2]![image](https://github.com/user-attachments/assets/0c0d324f-c344-4ac1-aef6-3121bb9fe223)


**Question 3**
---
How many male and female doctors are there in each medical specialty?

Sample table:Doctors Table

```sql
SELECT Specialty   ,       Gender  , count(*) as TotalDoctors from Doctors
group by Specialty, Gender
```

**Output:**

![Output3]![image](https://github.com/user-attachments/assets/8f0a8d2c-357d-4e17-9f63-bc0129ed6dda)


**Question 4**
---
Write a SQL query to find the customer with longest name?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER

```sql
SELECT name , LENGTH(name) as "length" from customer
order by "length" DESC
limit 1
```

**Output:**

![Output4]![image](https://github.com/user-attachments/assets/c6177100-28e1-45b9-8daa-27645041a577)


**Question 5**
---
Write a SQL query to find the total number of unique cities in the customer table?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER

```sql
SELECT count(DISTINCT city) as unique_cities from customer
```

**Output:**

![Output5]![image](https://github.com/user-attachments/assets/fa7ef797-1c09-4bbd-9a28-136815665526)


**Question 6**
---
Write a SQL query to find how many employees have an income greater than 50K?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER

```sql
select count(income) as employees_count from employee
where income>=50000
```

**Output:**

![Output6]![image](https://github.com/user-attachments/assets/efc15e08-d4c9-4ecd-bf49-e1d2c807253b)

**Question 7**
---
Write a SQL query that counts the number of unique salespeople. Return number of salespeople.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

```sql
select count(distinct salesman_id) as "COUNT" from orders
```

**Output:**

![Output7]![image](https://github.com/user-attachments/assets/cdfa948a-2d9f-4a11-8908-94c3f505b4f6)


**Question 8**
---
Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 400,000.

Sample table: employee

```sql
select age,MIN(income) as "MIN(income)" from employee
group by age
having "MIN(income)"<400000
```

**Output:**

![Output8]![image](https://github.com/user-attachments/assets/5f85df88-17b9-4628-9df7-9a14a8f02257)


**Question 9**
---
Write the SQL query that accomplishes the grouping of data by addresses, calculates the sum of salaries for each address, and excludes addresses where the total salary sum is not greater than 2000.

Sample table: customer1

```sql
select address, SUM(salary) as "SUM(salary)" from customer1
group by address 
having "SUM(salary)">2000
```

**Output:**

![Output9]![image](https://github.com/user-attachments/assets/00b4d553-f202-49db-8627-9f559ba997c2)


**Question 10**
---
Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 1,000,000.

Sample table: employee

```sql
select age, min(income) as Income from employee
group by age
having Income<1000000
```

**Output:**

![Output10]![image](https://github.com/user-attachments/assets/380f8311-bf38-4c6e-b41e-a5078852e0bc)



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
