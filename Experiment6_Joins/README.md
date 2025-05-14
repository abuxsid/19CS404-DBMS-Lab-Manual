![image](https://github.com/user-attachments/assets/58cc93fe-8ed3-4a5a-8b99-9422297f3825)# Experiment 6: Joins

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

![image](https://github.com/user-attachments/assets/915e2261-6370-45a2-9705-add2398206da)



```
SELECT patients.first_name, surgeries.*
FROM patients
INNER JOIN surgeries
ON patients.patient_id = surgeries.patient_id
WHERE patients.date_of_birth > '1990-01-01';
```
**Output:**

![image](https://github.com/user-attachments/assets/0bb473c7-5b7d-4ffc-8451-3bef6a52f811)


**Question 2**
![image](https://github.com/user-attachments/assets/2bc69307-8240-409b-a0ea-77c21e39425a)

```
SELECT orders.ord_no, 
       orders.purch_amt, 
       orders.ord_date, 
       customer.cust_name, 
       customer.city AS customer_city, 
       customer.grade, 
       salesman.name AS salesman_name, 
       salesman.city AS salesman_city, 
       salesman.commission
FROM orders
INNER JOIN customer ON orders.customer_id = customer.customer_id
INNER JOIN salesman ON orders.salesman_id = salesman.salesman_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/7bf92119-41ef-43c8-9a79-1a200e02a2df)


**Question 3**
![image](https://github.com/user-attachments/assets/ac030b49-a827-4b7b-8c87-b265bfc832ba)


```
SELECT customer.cust_name, 
       customer.city AS city, 
       customer.grade, 
       salesman.name AS Salesman, 
       salesman.city AS city
FROM customer
INNER JOIN salesman ON customer.salesman_id = salesman.salesman_id
WHERE customer.grade < 300
ORDER BY customer.customer_id ASC;
```

**Output:**

![image](https://github.com/user-attachments/assets/55692db2-7f7f-496b-83b3-53617b0243fa)


**Question 4**
---
![image](https://github.com/user-attachments/assets/8242b0fb-6f71-4e7b-9949-b8ec9d046876)


```sql
SELECT n.nurse_id, d.department_name
FROM nurses n
INNER JOIN departments d ON n.department_id = d.department_id
WHERE n.first_name = 'David' AND n.last_name = 'Moore';
```

**Output:**

![image](https://github.com/user-attachments/assets/45c97af2-e253-4ddd-8cbd-faaf04b2db8a)


**Question 5**
---
![image](https://github.com/user-attachments/assets/25a28562-e2d4-4088-a57b-fe931fe2fa88)


```
SELECT o.ord_no, o.ord_date, o.purch_amt, c.cust_name AS "Customer Name", c.grade, s.name AS Salesman, s.commission
FROM orders o
INNER JOIN customer c ON o.customer_id = c.customer_id
INNER JOIN salesman s ON o.salesman_id = s.salesman_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/122f4897-8290-4805-aeda-094b8f08ff81)



**Question 6**
---
![image](https://github.com/user-attachments/assets/aaf97073-015a-4110-8d7b-10fbc1b5de59)


```
SELECT c.*
FROM customer c
LEFT JOIN orders o ON c.customer_id = o.customer_id
WHERE o.ord_date > '2012-08-17';
```

**Output:**

![image](https://github.com/user-attachments/assets/964ec6e8-9a22-40b4-9579-f85b051aebeb)


**Question 7**
---
![image](https://github.com/user-attachments/assets/c36c8b20-0f04-4434-ae20-505614e8857c)


```
SELECT c.cust_name, s.name
FROM customer c
LEFT JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE c.city = s.city;
```

**Output:**

![image](https://github.com/user-attachments/assets/1cd2c9ee-73ab-4cb9-8f2f-574f116bc4c5)


**Question 8**
---
![image](https://github.com/user-attachments/assets/13109e65-1cfd-4f3c-8635-fb23d02fb5dc)


```
SELECT c.cust_name AS "Customer Name", 
       c.city AS "city", 
       s.name AS "Salesman", 
       s.commission AS "commission"
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/dbae8599-c177-4aa8-92f7-d3fd92425bbb)


**Question 9**
---
![image](https://github.com/user-attachments/assets/a760b087-e220-45ed-bc94-9ef7c565c971)


```
SELECT n.*
FROM nurses n
INNER JOIN departments d ON n.department_id = d.department_id
WHERE d.department_name = 'Pediatrics';
Output:
```

**Output:**

![image](https://github.com/user-attachments/assets/e02d3799-7cbb-4104-bc35-8c7dbcbc62fd)


**Question 10**
---
![image](https://github.com/user-attachments/assets/96e244f9-9cce-444a-a59e-398924dff458)


```
SELECT c.cust_name as "Customer Name", c.city AS city, s.name AS Salesman, s.city AS city, s.commission
FROM customer c
INNER JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE c.city != s.city
AND s.commission > 0.12;
```

**Output:**

![image](https://github.com/user-attachments/assets/1a219b9e-0284-48f7-8ebb-55d1b64dee52)



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
