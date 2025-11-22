Name: Sabarivasan V

Reg No: 212222060206

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
Create a table named Products with the following constraints:
ProductID as INTEGER should be the primary key.
ProductName as TEXT should be unique and not NULL.
Price as REAL should be greater than 0.
StockQuantity as INTEGER should be non-negative.

![Screenshot 2025-04-30 220124](https://github.com/user-attachments/assets/690a314c-8a58-4971-9513-6ba79f75978b)


**Query:**

```sql

CREATE TABLE Products(
ProductID integer primary key,
ProductName varchar(100) unique not null,
Price Real check(price>0),
StockQuantity integer check(StockQuantity>0)
);

```

**Output:**

![Screenshot 2025-04-30 220510](https://github.com/user-attachments/assets/55246a78-9c52-4ed7-a7b7-ec1addcbf07a)


**Question 2**
---
Write a SQL query to Add a new column named "discount" with the data type DECIMAL(5,2) to the "customer" table.

![Screenshot 2025-04-30 220522](https://github.com/user-attachments/assets/68479e39-c908-472b-aa8a-f0d7d801e508)


**Query:**

```sql

ALTER TABLE customer
ADD COLUMN discount DECIMAL(5,2)

```

**Output:**

![Screenshot 2025-04-30 220535](https://github.com/user-attachments/assets/bc416f42-3a2c-47fb-8de5-c21ce6895407)


**Question 3**
---
Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.

![Screenshot 2025-04-30 220547](https://github.com/user-attachments/assets/c0b8305e-734c-42b6-8d17-ab724e65f2db)


**Query:**

```sql

Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.

```

**Output:**

![Screenshot 2025-04-30 220601](https://github.com/user-attachments/assets/6540f06d-27f6-484a-a8b2-3ce46f098abd)


**Question 4**
---
Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

![Screenshot 2025-04-30 220612](https://github.com/user-attachments/assets/c4b7db4b-c2f7-4f52-8f9e-b8fa3791e430)


**Query:**

```sql

CREATE TABLE ProjectAssignments(
AssignmentID integer primary key,
EmployeeID integer,
ProjectID integer,
AssignmentDate date not null,
foreign key(EmployeeID) REFERENCES Employees(EmployeeID),
foreign key(ProjectID) REFERENCES Projects(projectID));

```

**Output:**

![Screenshot 2025-04-30 220620](https://github.com/user-attachments/assets/85332812-a85b-4c27-bc01-53dbb8b51363)


**Question 5**
---
Create a table named Events with the following columns:

EventID as INTEGER
EventName as TEXT
EventDate as DATE

![Screenshot 2025-04-30 220626](https://github.com/user-attachments/assets/3c88bf66-a401-4afd-bd8d-df974e06bc75)

**Query:**

```sql

create table Events(
EventID INTEGER,
EventName TEXT,
EventDate DATE
);

```

**Output:**

![Screenshot 2025-04-30 220634](https://github.com/user-attachments/assets/2bf9f615-be51-4152-92fd-3f4dc647fc1d)


**Question 6**
---
Create a new table named item with the following specifications and constraints:
1.item_id as TEXT and as primary key.
2.item_desc as TEXT.
3.rate as INTEGER.
4.icom_id as TEXT with a length of 4.
5.icom_id is a foreign key referencing com_id in the company table.
6.The foreign key should cascade updates and deletes.
7.item_desc and rate should not accept NULL.

![Screenshot 2025-04-30 220641](https://github.com/user-attachments/assets/a9a89e50-ac9f-48f6-9ea9-0a2f802939e0)

**Query:**

```sql

CREATE TABLE item(
item_id text primary key,
item_desc text,
rate integer ,
icom_id text check(length(icom_id=4)),
foreign key(icom_id) references company(com_id)
on update cascade
on delete cascade
);

```

**Output:**

![Screenshot 2025-04-30 220650](https://github.com/user-attachments/assets/1ba266cc-41c6-41b7-ba3e-4b624cbc3c7a)


**Question 7**
---
Write a SQL Query  to add attribute ISBN as varchar(30) and domain_dept as varchar(30) in the table 'books'

![Screenshot 2025-04-30 220713](https://github.com/user-attachments/assets/beb382f2-49fa-49eb-b89a-8205c364fba0)

**Query:**

```sql

ALTER TABLE books
ADD ISBN varchar(30);
ALTER TABLE books
ADD domain_dept varchar(30);

```

**Output:**

![Screenshot 2025-04-30 220721](https://github.com/user-attachments/assets/00ad40f1-7cb6-4f28-b5a2-ae3b84c0d667)


**Question 8**
---
Insert the below data into the Employee table, allowing the Department and Salary columns to take their default values.

![Screenshot 2025-04-30 220729](https://github.com/user-attachments/assets/fc4edd58-178e-4613-991b-fe1635f99971)

**Query:**

```sql

INSERT INTO Employee (EmployeeID,Name,Position)
VALUES(4, 'Emily White', 'Analyst');

```

**Output:**

![Screenshot 2025-04-30 220736](https://github.com/user-attachments/assets/7c12ed3a-f7ba-494e-8fcb-46e9451fd42b)


**Question 9**
---
Insert all products from Discontinued_products into Products.

Table attributes are ProductID, ProductName, Price, Stock

![Screenshot 2025-04-30 220742](https://github.com/user-attachments/assets/b047fd01-a44f-4951-a231-44d6093863a7)

**Query:**

```sql

INSERT INTO Products(ProductID,ProductName,Price,Stock)
SELECT ProductID, ProductName, Price, Stock FROM Discontinued_products;

```

**Output:**

![Screenshot 2025-04-30 220749](https://github.com/user-attachments/assets/71d585fe-2b76-43d8-8e50-f1ae7ea0567c)

**Question 10**
---
In the Products table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

![Screenshot 2025-04-30 220800](https://github.com/user-attachments/assets/21849162-5472-484a-9d75-1a974393f0bd)

**Query:**

```sql

INSERT INTO Products(ProductID, Name, Category, Price,Stock)
VALUES('106','Fitness Tracker','Wearables',NULL,NULL);
INSERT INTO Products(ProductID, Name, Category, Price,Stock)
VALUES('107','Laptop','Electronic','999.99','50');
INSERT INTO Products(ProductID, Name, Category, Price,Stock)
VALUES('108','Wireless Earbud','Accessorie',NULL,'100');

```

**Output:**

![Screenshot 2025-04-30 220808](https://github.com/user-attachments/assets/1353d9e8-f088-46dc-b2fb-507e20177f1a)

## Module 1 Home Challenge - Grade

![Screenshot 2025-05-01 141022](https://github.com/user-attachments/assets/2cdfa81a-3ba0-4d1a-afdf-9e018931f62c)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.

