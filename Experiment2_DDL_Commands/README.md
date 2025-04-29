# Experiment 2: DDL Commands
Name: ABUBAKKAR SIDDIQ M
# AIM
To study and implement DDL commands and different types of constraints.

# THEORY
1. CREATE
Used to create a new relation (table).

# Syntax:

# CREATE TABLE (
```
  field_1 data_type(size),
  field_2 data_type(size),
  ```
);
# 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation. (a) ADD

```ALTER TABLE std ADD (Address CHAR(10));```
(b) MODIFY

```ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));```
(c) DROP

```ALTER TABLE relation_name DROP COLUMN field_name;```
(d) RENAME

```ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;```
# 3. DROP TABLE
Used to permanently delete the structure and data of a table.

```DROP TABLE relation_name;```
# 4. RENAME
Used to rename an existing database object.

```RENAME TABLE old_relation_name TO new_relation_name;```
# CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).

# 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column. Syntax:

# CREATE TABLE Table_Name (
```
  column_name data_type(size) NOT NULL
```
);
# 2. UNIQUE
Ensures that values in a column are unique. Syntax:

# CREATE TABLE Table_Name (
```
  column_name data_type(size) UNIQUE
```
);
# 3. CHECK
Specifies a condition that each row must satisfy. Syntax:

# CREATE TABLE Table_Name (
```
  column_name data_type(size) CHECK (logical_expression)
```
);
# 4. PRIMARY KEY
Used to uniquely identify each record in a table. Properties: Must contain unique values. Cannot be null. Should contain minimal fields. Syntax:

# CREATE TABLE Table_Name (
```
  column_name data_type(size) PRIMARY KEY
```
);
# 5. FOREIGN KEY
Used to reference the primary key of another table. Syntax:

# CREATE TABLE Table_Name (
```
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
```
);
# 6. DEFAULT
Used to insert a default value into a column if no value is specified.

# Syntax:

# CREATE TABLE Table_Name (
 
  ```col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
```
);
# Question 1
![image](https://github.com/user-attachments/assets/7f9a1e95-9831-460c-bd86-62453852ad1c)

```
alter table  Student_details add  State TEXT;
```
# Output:
![image](https://github.com/user-attachments/assets/b50a185d-9053-4c7e-9b71-dd9a002febad)

# Question 2
![image](https://github.com/user-attachments/assets/c7c63cba-a946-4f3d-b556-60f7329a972a)

```create table jobs(
job_id int primary key,
job_title text,
min_salary integer default(8000),
max_salary int);
```
# Output:
![image](https://github.com/user-attachments/assets/e4bba124-08aa-460e-b807-39ecadc65eda)


# Question 3
![image](https://github.com/user-attachments/assets/978ff121-5d9c-42db-9d9e-692f704f1479)

```create table contacts(
contact_id INTEGER primary key,
first_name TEXT not NULL,
last_name  TEXT  not NULL,
email TEXT,
phone  TEXT  not NULL check(length(phone)=10));
```
# Output:

![image](https://github.com/user-attachments/assets/4ecbf53b-c802-46bc-abb4-583a82507d7e)

# Question 4
![image](https://github.com/user-attachments/assets/31834c8f-fc62-4225-ae14-ec264907ecbe)

```insert into Employee(EmployeeID,Name,Position)values(5,'George Clark','Consultant');
insert into Employee(EmployeeID,Name,Position,Department,Salary)values(7,'Noah Davis','Manager','HR',60000);
insert into Employee(EmployeeID,Name,Position,Department)values(8,'Ava Miller','Consultant','IT');
```
# Output:

![image](https://github.com/user-attachments/assets/8a33467c-2cd8-4604-81b1-434cee8640d4)

# Question 5
![image](https://github.com/user-attachments/assets/a441413c-b417-43cd-bea5-0577cfffdbd3)

```create table Orders(
OrderID INTEGER primary key,
OrderDate  DATE not NULL,
CustomerID INTEGER, 
foreign key(CustomerID) references Customers(CustomerID));
```
# Output:

![image](https://github.com/user-attachments/assets/d077ecfb-ae50-4146-a831-ec54696450ad)

# Question 6
![image](https://github.com/user-attachments/assets/c37a2b56-04e8-4e6e-a797-772db23414a4)

```create table Tasks(
TaskID  INTEGER,
TaskName TEXT,
DueDate DATE);
```
# Output:

![image](https://github.com/user-attachments/assets/03c0cca0-1335-4e1a-9a92-1b154f7d25d1)

# Question 7
![image](https://github.com/user-attachments/assets/bf6adf62-cd5a-402f-8453-5856f3048791)

```insert into Employee(EmployeeID,Name,Position)values(4,'Emily White','Analyst');
```
# Output:

![image](https://github.com/user-attachments/assets/b14e185d-4396-40c0-a287-dd9e396f998f)

# Question 8
![image](https://github.com/user-attachments/assets/a57e4c34-602b-446e-9a18-b9f0cbb28c67)


```insert into  Customers(CustomerID, Name, Address, Email)
select CustomerID, Name, Address, Email
from Old_customers;
```
# Output:

![image](https://github.com/user-attachments/assets/34039a07-56dd-472f-ae2f-bebf3a2e3daa)

# Question 9
![image](https://github.com/user-attachments/assets/aaa6f1c9-2714-4dae-95c0-f829e69a7ece)


``alter table Employees add salary INTEGER check(salary>0);``
# Output:

![image](https://github.com/user-attachments/assets/ac8b4ff3-741e-4894-827d-f2beea6c76d5)

# Question 10
![image](https://github.com/user-attachments/assets/267e2072-8815-4dab-ba82-fb03e96b8084)

```create table Invoices(
InvoiceID INTEGER  primary key,
InvoiceDate DATE,
Amount  REAL check(Amount>0),
DueDate  DATE check(DueDate>InvoiceDate),
OrderID  INTEGER,
foreign key(OrderID) references Orders(OrderID));
```
# Output:
![image](https://github.com/user-attachments/assets/7413bd8d-a3e2-4dac-a506-77c8561f1984)

# GRADE
![image](https://github.com/user-attachments/assets/9affa934-b4e9-4736-bdae-2e6714921ae0)


# RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
