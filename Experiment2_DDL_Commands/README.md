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

<img width="1289" height="292" alt="image" src="https://github.com/user-attachments/assets/4cb2ec0b-3017-45fa-9864-e90f96651117" />

```sql
CREATE TABLE Bonuses(
BonusID INT PRIMARY KEY,
EmployeeID INT,
BonusAmount REAL CHECK(BonusAmount>0),
BonusDate DATE,
Reason TEXT NOT NULL
);
```

**Output:**

<img width="920" height="199" alt="image" src="https://github.com/user-attachments/assets/6c165d3c-6463-4947-a7cb-c3fe450091f3" />


**Question 2**


<img width="920" height="199" alt="438734499-560ebfe7-6a54-41b1-a177-84d9a5353047" src="https://github.com/user-attachments/assets/60660e3b-2f8d-4bc7-8849-93769173dc77" />




```sql
INSERT INTO Products(ProductID,Name,Category,Price,Stock)
VALUES(101,'Laptop','Electronics',1500,50);
```

**Output:**

<img width="1243" height="174" alt="image" src="https://github.com/user-attachments/assets/e43a5545-5c91-489d-a93b-9c630213e392" />



**Question 3**


<img width="850" height="355" alt="image" src="https://github.com/user-attachments/assets/b42ee6d3-67d0-4233-ae7d-9dd1efc928b3" />



```sql
CREATE TABLE item(
item_id TEXT PRIMARY KEY,
item_desc TEXT NOT NULL,
rate INT NOT NULL,
icom_id TEXT(4),
FOREIGN KEY (icom_id) REFERENCES company(com_id)
ON UPDATE CASCADE
ON DELETE CASCADE
);
```

**Output:**


<img width="1152" height="250" alt="image" src="https://github.com/user-attachments/assets/37c27297-15bf-452d-9824-95771033c6e0" />




**Question 4**

<img width="1256" height="260" alt="image" src="https://github.com/user-attachments/assets/8e56d377-7627-4b3f-837f-0541c86bae04" />



```sql
CREATE TABLE ProjectAssignments(
AssignmentID INT PRIMARY KEY,
EmployeeID INT,
ProjectID INT,
AssignmentDate DATE NOT NULL,
FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)
);
```

**Output:**

<img width="1246" height="211" alt="image" src="https://github.com/user-attachments/assets/acfc34c1-ec21-46d3-a125-fc7bcd82a42d" />



**Question 5**

<img width="796" height="266" alt="image" src="https://github.com/user-attachments/assets/909deb95-7445-4a2e-a02d-dabe6a070fbb" />



```sql
INSERT INTO Books(ISBN,Title,Author,Publisher,YearPublished)
SELECT  ISBN, Title, Author, Publisher, YearPublished
FROM  Out_of_print_books;
```

**Output:**

<img width="1238" height="220" alt="image" src="https://github.com/user-attachments/assets/65dd490b-d884-4c0b-8861-d799fa77e859" />


**Question 6**

<img width="754" height="313" alt="image" src="https://github.com/user-attachments/assets/eb760487-5d85-4175-9c22-52a2b9c2b970" />



```sql
CREATE TABLE Events(
EventID INTEGER,
EventName TEXT,
EventDate DATE
);
```

**Output:**

<img width="1245" height="294" alt="image" src="https://github.com/user-attachments/assets/a534daf1-9fe3-40b0-82f6-09e040444546" />

**Question 7**

<img width="1257" height="396" alt="image" src="https://github.com/user-attachments/assets/3162b6db-ad5e-4546-8d10-45ab8f6cd7ae" />


```sql
INSERT INTO Products(ProductID,Name,Category,Price,Stock)
VALUES(106,'Fitness Tracker','Wearables',NULL,NULL);
INSERT INTO Products(ProductID,Name,Category,Price,Stock)
VALUES(107,'Laptop','Electronics',999.99,50);
INSERT INTO Products(ProductID,Name,Category,Price,Stock)
VALUES(108,'Wireless Earbuds','Accessories',NULL,100);
```

**Output:**

<img width="1244" height="201" alt="image" src="https://github.com/user-attachments/assets/6339f9d3-4dee-4876-ae0f-fbd71c56b7d5" />


**Question 8**

<img width="846" height="467" alt="image" src="https://github.com/user-attachments/assets/262dbce8-8369-4b22-8650-efa6c7c5841b" />


```sql
ALTER TABLE Companies ADD COLUMN designation varchar(50);
ALTER TABLE Companies ADD COLUMN net_salary number;
ALTER TABLE Companies ADD COLUMN dob date;
```

**Output:**

<img width="1247" height="321" alt="image" src="https://github.com/user-attachments/assets/c8a3a674-d1ba-4df5-97f6-18af6af1af0c" />


**Question 9**

<img width="1258" height="197" alt="image" src="https://github.com/user-attachments/assets/aa597f98-5662-4006-9787-c6da53fd95f0" />


```sql
CREATE TABLE jobs(
job_id INT,
job_title TEXT DEFAULT '',
min_salary INT DEFAULT 8000,
max_salary INT DEFAULT NULL);
```

**Output:**

<img width="1249" height="252" alt="image" src="https://github.com/user-attachments/assets/3c3b4dec-187d-48db-8546-44f3488d2157" />

**Question 10**

<img width="1210" height="182" alt="image" src="https://github.com/user-attachments/assets/f1e9e81e-a5d9-4d8c-a13e-05c4d75a4bc4" />


```sql
ALTER TABLE Student_details ADD COLUMN Email VARCHAR(50);
ALTER TABLE Student_details ADD COLUMN MARKS INT DEFAULT 0;
```

**Output:**

<img width="1246" height="183" alt="image" src="https://github.com/user-attachments/assets/c86442d0-6dc7-4514-98cd-0bd7c6ccb726" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
