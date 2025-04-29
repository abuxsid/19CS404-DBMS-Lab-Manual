# Experiment 3: DML Commands
NAME:ABUBAKKAR SIDDIQ M
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
![image](https://github.com/user-attachments/assets/176bf6fe-b617-4cdd-8d50-bb40da5cc97a)

```sql
update sales
set sell_price= sell_price*1.05
where product_id =15;
```

**Output:**

![image](https://github.com/user-attachments/assets/3f4b2a86-5dfa-471b-9de4-8d5583db1f34)

**Question 2**
---
![image](https://github.com/user-attachments/assets/4caf7575-91b5-4496-bfea-c27f47b33c4b)

```sql
update sales
set sell_price = sell_price +3
where product_id in(
select product_id
from PRODUCTS
where supplier_id=4);
```

**Output:**

![image](https://github.com/user-attachments/assets/7af08efa-3dc1-4af8-8006-70f81d734728)

**Question 3**
---
![image](https://github.com/user-attachments/assets/419b8752-f76f-48d7-9302-7b6f49722a0e)

```sql
update Employees
set EMAIL= 'not available' ,
COMMISSION_PCT =0.55
where department_id =110;
```

**Output:**

![image](https://github.com/user-attachments/assets/064ea511-38db-461b-95f2-7481c21bb41e)

**Question 4**
---
![image](https://github.com/user-attachments/assets/5016ebc7-21e9-4108-82a5-66007120f624)

```sql
update products
set reorder_lvl=reorder_lvl*1.30
where category = 'Food' and quantity<50;
```

**Output:**

![image](https://github.com/user-attachments/assets/fa247c2b-5e8e-4254-8405-2d7e81ea06bf)

**Question 5**
---
![image](https://github.com/user-attachments/assets/ce1c0339-bb39-40e5-b199-a0cf071e8330)

```sql
update PRODUCTS
set reorder_lvl= reorder_lvl*0.7
where product_name like '%cream%' and quantity >reorder_lvl;
```

**Output:**

![image](https://github.com/user-attachments/assets/daf9f69e-ab6d-41bf-9178-764f58a9c6bc)

**Question 6**
---
![image](https://github.com/user-attachments/assets/42b7b57b-37ac-45df-9ae6-dcaee7ae9a8c)

```sql
delete from Doctors
where specialization ='Cardiology';
```

**Output:**

![image](https://github.com/user-attachments/assets/ac473a63-9587-4f76-9c59-994dc280ca28)

**Question 7**
---
![image](https://github.com/user-attachments/assets/f607a65f-9622-445b-9864-b3710ad73de1)

```sql
delete from Doctors
where doctor_id  = 1;
```

**Output:**

![image](https://github.com/user-attachments/assets/76c63ed2-d107-4472-ade5-7cac855befec)

**Question 8**
---
![image](https://github.com/user-attachments/assets/7a6dc459-5ee4-4dd9-8860-8f47638b64a0)

```sql
delete from Surgeries
where surgery_id = 3;
```

**Output:**

![image](https://github.com/user-attachments/assets/48742919-6577-4fe6-b545-f8b3c7c53c21)

**Question 9**
---
![image](https://github.com/user-attachments/assets/495c8fa3-b7ee-4372-a77f-9c3332677458)

```sql
delete from Customer
where (GRADE=2 and CUST_NAME like 'M%')
and PAYMENT_AMT<3000;
```

**Output:**

![image](https://github.com/user-attachments/assets/d1d71b4c-d901-481c-8d84-777e27739434)

**Question 10**
---
![image](https://github.com/user-attachments/assets/a77caf71-c81b-4e8f-9cda-c30f77bee85c)

```sql
delete from Customer
where GRADE >2 
and PAYMENT_AMT <(select avg(PAYMENT_AMT)from Customer)
or OUTSTANDING_AMT>8000;
```

**Output:**

![image](https://github.com/user-attachments/assets/78500804-f675-4171-b8e3-a9f392100002)

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
