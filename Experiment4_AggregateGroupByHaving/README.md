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

Write a SQL query to Identify customers whose city is different from the city of the customer with the highest ID

SAMPLE TABLE: customer

name             type
---------------  ---------------
id               INTEGER
name             TEXT
city             TEXT
email            TEXT
phone            INTEGER
For example:

Result
id     name             city             email            phone
-----  ---------------  ---------------  ---------------  ----------
6      Aarti Desai      Pune             aarti@gmail.com  890123456
7      Vivek Sharma     Chandigarh       vivek@gmail.com  980154021
8      Nisha Patel      Noida            nisha@gmail.com  901234567
9      Rajesh Singh     Hyderabad        rajesh@gmail.co  917654301

```select * from customer s
where city<>(
select city 
from customer
order by id desc
)
```

**Output:**

![image](https://github.com/user-attachments/assets/01b0d740-af48-4cbc-a8c5-782c5b63edaf)

**Question 2**

Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is LESS than $2500.

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000

For example:

Result
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1           Ramesh      32          Ahmedabad   2000
2           Khilan      25          Delhi       1500
3           Kaushik     23          Kota        2000

```select * from customers
where salary <2500;
```

**Output:**

![image](https://github.com/user-attachments/assets/7002e19e-c583-4a7b-9067-6dc1099b2884)


**Question 3**

Write a SQL query that retrieves the names of students and their corresponding grades, where the grade is equal to the minimum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)

For example:

Result
student_name     grade
---------------  ---------------
Bob              85
Frank            85
John             85

```select student_name,grade
from GRADES s
where grade=(
select min(grade)
from GRADES
where subject =s.subject
)
```
**Output:**

![image](https://github.com/user-attachments/assets/afeb77be-87cb-4d55-a8f8-e54d4211014c)


**Question 4**

Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $1500.

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000

For example:

Result
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1           Ramesh      32          Ahmedabad   2000
3           Kaushik     23          Kota        2000
4           Chaitali    25          Mumbai      6500
5           Hardik      27          Bhopal      8500
6           Komal       22          Hyderabad   4500
7           Muffy       24          Indore      10000

```select * from customers
where salary>1500;
```

**Output:**

![image](https://github.com/user-attachments/assets/6e0016db-5294-4dcb-9665-310739c07044)


**Question 5**

From the following tables, write a SQL query to find all the orders generated in New York city. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

SALESMAN TABLE

name               type
-----------        ----------
salesman_id  numeric(5)
name             varchar(30)
city                 varchar(15)
commission   decimal(5,2)

ORDERS TABLE

name            type
----------      ----------
ord_no          int
purch_amt    real
ord_date       text
customer_id  int
salesman_id  int

For example:

Result
ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70002       65.26       2012-10-05  3002         5001
70005       2400.6      2012-07-27  3007         5001
70008       5760.0      2012-09-10  3002         5001
70013       3045.6      2012-04-25  3002         5001
```
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM ORDERS o
JOIN SALESMAN s ON o.salesman_id = s.salesman_id
WHERE s.city = 'New York';
```

**Output:**

![image](https://github.com/user-attachments/assets/8c464e5d-042e-426a-8423-f0c6e61939c3)


**Question 6**

Write a SQL query that retrieves the all the columns from the Table Grades, where the grade is equal to the minimum grade achieved in each subject.
Sample table: GRADES (attributes: student_id, student_name, subject, grade)
For example:

Result
student_id       student_name     subject          grade
---------------  ---------------  ---------------  ---------------
2                Bob              Math             85
6                Frank            Science          85
7                John             Social           85

```SELECT *
FROM GRADES g
WHERE (g.subject, g.grade) IN (
    SELECT subject, MIN(grade)
    FROM GRADES
    GROUP BY subject
);
```
**Output:**

![image](https://github.com/user-attachments/assets/95ee7b07-7903-48b9-b7c2-fa92d33bfe43)


**Question 7**

Write a SQL query to List departments with names longer than the average length

Departments Table (attributes: department_id, department_name)
For example:

Result
depar  department_name
-----  ---------------
5      Anesthesiologis

```SELECT department_id, department_name
FROM Departments
WHERE LENGTH(department_name) > (
    SELECT AVG(LENGTH(department_name))
    FROM Departments
);
```

**Output:**

![image](https://github.com/user-attachments/assets/a733a8ad-8b7b-43ea-ac36-395d51ed039f)


**Question 8**

From the following tables, write a SQL query to find those salespeople who earned the maximum commission. Return ord_no, purch_amt, ord_date, and salesman_id.

salesman table

name             type
---------------  ---------------
salesman_id      numeric(5)
name                 varchar(30)
city                    varchar(15)
commission       decimal(5,2)

orders table

name             type
---------------  --------
order_no         int
purch_amt        real
order_date       text
customer_id      int
salesman_id      int

```SELECT o.ord_no, o.purch_amt, o.ord_date, o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.commission = (
    SELECT MAX(commission)
    FROM salesman
);
```
**Output:**

![image](https://github.com/user-attachments/assets/dd1f0715-359c-4c28-a113-22e662c57301)


**Question 9**

Write a SQL query that retrieve all the columns from the table "Grades", where the grade is equal to the maximum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)
For example:

Result
student_id       student_name     subject          grade
---------------  ---------------  ---------------  ---------------
3                Charlie          Math             95
5                Emma             Science          92
7                John             Social           85

```SELECT *
FROM GRADES g
WHERE (g.subject, g.grade) IN (
    SELECT subject, MAX(grade)
    FROM GRADES
    GROUP BY subject
);
```

**Output:**

![image](https://github.com/user-attachments/assets/08a76dba-a5ba-484d-bc11-17284303c90f)


**Question 10**

Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 2.5 Lakh
Employee Table
name             type
------------   ---------------
id                    INTEGER
name              TEXT
age                 INTEGER
city                 TEXT
income           INTEGER

For example:
Result
id     name             age              city             income
-----  ---------------  ---------------  ---------------  ----------
101    Peter            32               NewYork          200000
102    Mark             32               California       300000
103    Donald           25               Arizona          1000000
104    Obama            35               Florida          5000000
105    Linklon          32               Georgia          250000
107    Adam             35               California       5000000

```SELECT id, name, age, city, income
FROM Employee
WHERE age < (
    SELECT AVG(age)
    FROM Employee
    WHERE income > 250000
);
```
**Output:**

![image](https://github.com/user-attachments/assets/fb2c8049-b675-4d53-9f32-008da058247d)



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
