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
**Question 1**
--
How many appointments are scheduled for each doctor?

Sample table:Appointments Table


```sql
select DoctorID, count(*) as TotalAppointments from Appointments Group by DoctorID;
```

**Output:**

<img width="1307" height="550" alt="image" src="https://github.com/user-attachments/assets/dcff31ef-c559-45ce-828e-d8cd2e8bea06" />


**Question 2**
---
Write SQL query to extract the email domain from each patient's email address and count the number of patients with the same email domain.

Sample table: Patients Table



```sql
select 
    substr(Email,instr(Email,'@')+1) as EmailDomain,
    count(*) as TotalPatients
from Patients
group by EmailDomain;
```

**Output:**
<img width="1307" height="332" alt="image" src="https://github.com/user-attachments/assets/5f3bd4d7-21e5-464e-9578-39fe97e9e073" />

**Question 3**
---
Write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001



```sql
select sum(purch_amt) as TOTAL from orders;
```

**Output:**

<img width="1310" height="308" alt="image" src="https://github.com/user-attachments/assets/6412b5a7-6421-4897-80bd-f75251dd81cc" />


**Question 4**
---
Write a SQL query to find the maximum purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

 

```sql
select max(purch_amt) as MAXIMUM from orders;
```

**Output:**

<img width="1313" height="306" alt="image" src="https://github.com/user-attachments/assets/83f05ac5-33d1-4a68-b4e5-03d9a1c84495" />


**Question 5**
---
Write a SQL query to calculate total available amount of fruits that has a price greater than 0.5 . Return total Count. 

Note: Inventory attribute contains amount of fruits

Table: fruits

name        type
----------  ----------
id          INTEGER
name        TEXT
unit        TEXT
inventory   INTEGER
price       REAL
 

```sql
select sum(inventory) as total_available_amount 
from fruits
where price>0.5 ;
```

**Output:**
<img width="1318" height="306" alt="image" src="https://github.com/user-attachments/assets/93b083db-dd26-4050-9d17-fa73a98a86e1" />


**Question 6**
---
Write a SQL query that counts the number of unique salespeople. Return number of salespeople.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

 

```sql
select count(distinct salesman_id) as COUNT from orders;
```

**Output:**

<img width="1307" height="305" alt="image" src="https://github.com/user-attachments/assets/ce48f515-c366-4772-bc15-bb913b363240" />


**Question 7**
---
Write the SQL query that accomplishes the grouping of data by age, calculates the average income for each age group, and includes only those age groups where the average income falls between 300,000 and 500,000.

Sample table: employee

```sql
select age, AVG(income)
from employee
group by age
having AVG(income) between 300000 and 500000;
```

**Output:**

<img width="1313" height="337" alt="image" src="https://github.com/user-attachments/assets/bae7b798-ba2f-4e20-b29d-9774c16d210d" />


**Question 8**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the total work hours for each date, and excludes dates where the total work hour sum is not greater than 40.

Sample table: employee1



```sql
SELECT jdate,SUM(workhour)
from employee1
group by jdate
having SUM(workhour)>40;
```

**Output:**

<img width="1315" height="362" alt="image" src="https://github.com/user-attachments/assets/8bddb350-416a-434a-b3d6-257d1c251598" />


**Question 9**
---
Write the SQL query that achieves the grouping of data by city, calculates the total income for each city, and includes only those cities where the total income sum is greater than 200,000.

Sample table: employee


```sql
SELECT city,SUM(income) as Income
from employee
group by city
having SUM(income) > 200000;
```

**Output:**
<img width="1321" height="471" alt="image" src="https://github.com/user-attachments/assets/7d9ba0df-530f-4830-8a5e-c592a699e086" />


**Question 10**
---
Write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.

Sample table: orders

```sql
select sum(purch_amt) as TOTAL from orders;
```

**Output:**

<img width="1310" height="308" alt="image" src="https://github.com/user-attachments/assets/6412b5a7-6421-4897-80bd-f75251dd81cc" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
