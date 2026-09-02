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

For products with a profit % less than 30% of selling price, update the selling price to provide a profit margin of 35% over cost price of the product in the products table.

PRODUCTS TABLE

name type

product_id INT product_name VARCHAR(100) category VARCHAR(50) cost_price DECIMAL(10,2) sell_price DECIMAL(10,2) reorder_lvl INT quantity INT supplier_id INT

```sqlUPDATE products
SET sell_price = cost_price * 135/100
WHERE ((sell_price - cost_price) / sell_price) * 100 < 30;
```

**Output:**

<img width="1257" height="833" alt="image" src="https://github.com/user-attachments/assets/36259465-f91d-4233-9a34-2ff196e9cb4a" />

**Question 2**
Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.

Suppliers Table

name type

supplier_id INT supplier_name VARCHAR(100) contact_person VARCHAR(100) phone_number VARCHAR(20) email VARCHAR(100) address VARCHAR(250)

```sql
UPDATE suppliers
SET address = '58 Lakeview, Magnolia'
WHERE supplier_id = 5;
```

**Output:**

<img width="1229" height="843" alt="image" src="https://github.com/user-attachments/assets/52336ddf-6bab-44f3-b57b-5ece51524e12" />

**Question 3**
Write a SQL query to reduce the reorder level by 30% where cost price is more than 50 and quantity in stock is less than 100 in the products table.

Products Table

name type

product_id INT PRIMARY KEY
product_name VARCHAR(10) category VARCHAR(50) cost_price DECIMAL(10) sell_price DECIMAL(10) reorder_lvl INT
quantity INT
supplier_id INT

```sqlUPDATE products
SET reorder_lvl = reorder_lvl * 70 / 100
WHERE cost_price > 50
  AND quantity < 100;
```

**Output:**

<img width="1204" height="850" alt="image" src="https://github.com/user-attachments/assets/5dc36d8a-371e-420c-9c03-9da41b7b5462" />

**Question 4**
Update the reorder level to 40 pieces for all products belonging to the 'Grocery' category in the products table.

PRODUCTS TABLE

name type

product_id INT product_name VARCHAR(100) category VARCHAR(50) cost_price DECIMAL(10,2) sell_price DECIMAL(10,2) reorder_lvl INT quantity INT supplier_id INT

```sql
UPDATE products
SET reorder_lvl = 40
WHERE category = 'Grocery';
```

**Output:**

<img width="1233" height="851" alt="image" src="https://github.com/user-attachments/assets/85e372c6-3afa-4f56-beb7-afb9f84c0463" />

**Question 5**
Write a SQL statement to Increase the salary by 500 and email as 'updated' for employees with job ID 'SA_REP' and commission percentage greater than 0.15

Employees table

employee_id first_name last_name email phone_number hire_date job_id salary commission_pct manager_id department_id
```sql
UPDATE employees
SET salary = salary + 500,
    email = 'updated'
WHERE job_id = 'SA_REP'
  AND commission_pct > 0.15;
```

**Output:**

<img width="1216" height="851" alt="image" src="https://github.com/user-attachments/assets/1e11afca-ab90-4088-bef9-d28bb40358b9" />


**Question 6**
Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' has exactly 6 characters.



```sql
DELETE FROM customer
WHERE LENGTH(CUST_NAME) = 6;
```

**Output:**

<img width="1246" height="846" alt="image" src="https://github.com/user-attachments/assets/445491d4-db44-4b64-a979-afc37f2bc808" />


**Question 7**
Write a SQL query to remove rows from the table 'customer' with the following condition -

'cust_city' should begin with the letter 'L',

```sql
DELETE FROM customer
WHERE cust_city LIKE 'L%';
```

**Output:**

<img width="1239" height="831" alt="image" src="https://github.com/user-attachments/assets/b8297750-213b-4adb-98d5-b59fcddafdd8" />

**Question 8**
Write a SQL query to Delete All Doctors with a NULL Last Name

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization For example:

Test Result SELECT * FROM doctors; doctor_id first_name last_name specialization

1 John Smith Cardiology 2 Emily Johnson Orthopedics 3 Michael Brown Pediatrics 4 Febin Cardiology doctor_id first_name last_name specialization

1 John Smith Cardiology 2 Emily Johnson Orthopedics 3 Michael Brown Pediatrics

```sql
DELETE FROM doctors
WHERE last_name IS NULL;
```

**Output:**

<img width="1240" height="858" alt="image" src="https://github.com/user-attachments/assets/bd37e029-e1d6-4023-8657-2843877b6403" />


**Question 9**
Write a SQL query to Delete customers whose 'GRADE' is greater than 2 and have a 'PAYMENT_AMT' less than the average 'PAYMENT_AMT' for all customers, or whose 'OUTSTANDING_AMT' is greater than 8000:

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
|CUST_CODE | CUST_NAME | CUST_CITY | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO | AGENT_CODE | +-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+ | C00013 | Holmes | London | London | UK | 2 | 6000.00 | 5000.00 | 7000.00 | 4000.00 | BBBBBBB | A003 | | C00001 | Micheal | New York | New York | USA | 2 | 3000.00 | 5000.00 | 2000.00 | 6000.00 | CCCCCCC | A008 | | C00020 | Albert | New York | New York | USA | 3 | 5000.00 | 7000.00 | 6000.00 | 6000.00 | BBBBSBB | A008

```sql
DELETE FROM customer
WHERE (grade > 2
       AND payment_amt < (SELECT AVG(payment_amt) FROM customer))
   OR outstanding_amt > 8000;
```

**Output:**

<img width="1220" height="843" alt="image" src="https://github.com/user-attachments/assets/0e7b0771-7e0c-41a3-a968-0abc09e6d3be" />


**Question 10**
Show the categoryName and description from the categories table sorted by categoryName.

name type

CategoryID INTEGER CategoryName VARCHAR(25) Description VARCHAR(255)

```sql
SELECT CategoryName, Description
FROM categories
ORDER BY CategoryName;
```

**Output:**

<img width="1207" height="846" alt="image" src="https://github.com/user-attachments/assets/e85a7881-aafc-4ae2-9ffe-2602a69f597f" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
