# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
![image](https://github.com/user-attachments/assets/8c9b9bab-95e2-468c-a33b-13b67b919879)


```
SELECT 
    p.first_name AS patient_name,
    d.specialization AS Doctor_specialization
FROM 
    patients p
INNER JOIN 
    doctors d ON p.doctor_id = d.doctor_id
WHERE 
    p.admission_date BETWEEN '2024-01-01' AND '2024-01-31';
```

**Output:**

![image](https://github.com/user-attachments/assets/dda69781-18ab-4215-a00c-c4537c95bd81)


**Question 2**
---
![image](https://github.com/user-attachments/assets/75f68ace-9d9f-4382-9834-6ba65a967926)


```sql
SELECT 
    c.cust_name, 
    c.city, 
    c.grade, 
    s.name AS Salesman, 
    s.city AS city
FROM 
    customer c
INNER JOIN 
    salesman s ON c.salesman_id = s.salesman_id
ORDER BY 
    c.customer_id ASC;
```

**Output:**

![image](https://github.com/user-attachments/assets/3fee3a18-5544-4760-8cec-c0f40dc49b88)


**Question 3**
---
![image](https://github.com/user-attachments/assets/30d6cba7-8f43-4738-93ff-44e67094ee30)


```
SELECT 
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt AS "Order Amount",
    s.name,
    s.commission
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
LEFT JOIN 
    salesman s ON o.salesman_id = s.salesman_id
ORDER BY 
    c.cust_name, o.ord_date;
```

**Output:**

![image](https://github.com/user-attachments/assets/638d9122-475c-43be-84d5-32d4f28ee803)


**Question 4**
---
![image](https://github.com/user-attachments/assets/72bcae44-e12d-4b78-9ec7-1474ef0b208e)


```
SELECT 
    o.ord_no,
    o.ord_date,
    o.purch_amt,
    c.cust_name AS "Customer Name",
    c.grade,
    s.name AS "Salesman",
    s.commission
FROM 
    orders o
JOIN 
    customer c ON o.customer_id = c.customer_id
JOIN 
    salesman s ON o.salesman_id = s.salesman_id
ORDER BY 
    o.ord_no;
```

**Output:**

![image](https://github.com/user-attachments/assets/5296c3eb-c55e-4b7f-a969-0fbae4222fa7)


**Question 5**
---
![image](https://github.com/user-attachments/assets/e987741a-2caf-45a3-807f-d75c4e201d80)


```
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.city AS "city",
    s.commission
FROM 
    customer c
JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    c.city <> s.city
    AND s.commission > 0.12;
```

**Output:**

![image](https://github.com/user-attachments/assets/bfd6081a-bd9f-4432-9c40-85a39899e733)


**Question 6**
---
![image](https://github.com/user-attachments/assets/72b956f9-36fe-4064-b010-00169d90d13b)


```
SELECT 
    c.*
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
WHERE 
    o.ord_date BETWEEN '2012-08-01' AND '2012-08-30';
```

**Output:**

![image](https://github.com/user-attachments/assets/2b52b0ca-b9d7-442f-8c5a-b4f3b59299a4)


**Question 7**
---
![image](https://github.com/user-attachments/assets/ab3b7f3e-19be-4115-8f40-5be3ea2cea9e)


```
SELECT 
    p.first_name AS "patient_name",
    t.*
FROM 
    patients p
INNER JOIN 
    test_results t ON p.patient_id = t.patient_id
WHERE 
    t.test_name = 'Blood Pressure';
```

**Output:**

![image](https://github.com/user-attachments/assets/13b48b31-4829-45f4-861a-a73190d48e7b)


**Question 8**
---
![image](https://github.com/user-attachments/assets/3cf42792-ff9b-439f-81ac-473c58cc3bf2)


```
SELECT 
    c.cust_name,
    c.city AS "city",
    c.grade,
    s.name AS "Salesman",
    s.city AS "city"
FROM 
    customer c
JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    c.grade < 300
ORDER BY 
    c.customer_id ASC;
```

**Output:**

![image](https://github.com/user-attachments/assets/f717966c-d16e-4a6b-b6e7-051a771ecc7b)


**Question 9**
---
![image](https://github.com/user-attachments/assets/25348352-648f-4687-a3c0-54b2b0b48b84)


```sql
-SELECT 
    p.first_name AS "patient_name",
    t.*
FROM 
    patients p
INNER JOIN 
    test_results t ON p.patient_id = t.patient_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/47588c41-7aa1-47cb-87c6-e5e2f4c0fc2f)


**Question 10**
---
![image](https://github.com/user-attachments/assets/abf28d6f-ad66-49d1-977f-dcdc05d4438e)


```
SELECT 
    c.cust_name,
    o.ord_no,
    o.ord_date,
    o.purch_amt
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/17a48d00-797e-4cbe-8449-665baa52c7cb)



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
