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
![image](https://github.com/user-attachments/assets/8f44d699-7c17-4fc0-9a0a-0d9c1fae85e1)

```sql
select 
PatientID,
count(*) as TotalAppointments
from
Appointments
group by
PatientID
order by
PatientID;
```

**Output:**

![image](https://github.com/user-attachments/assets/822a0a64-12f6-4b3c-bb14-4e23beeecba1)

**Question 2**
---
![image](https://github.com/user-attachments/assets/309ad6f8-ecb4-4b5d-b30a-def0b995e6b0)

```sql
select
strftime('%H',AppointmentDateTime) as "HourOfDay",
count(*) as "TotalAppointments"
from
Appointments
group by
strftime('%H',AppointmentDateTime)
order by
HourOfDay;
```

**Output:**

![image](https://github.com/user-attachments/assets/10813034-1f42-4ba6-95a5-8b2e496fab29)

**Question 3**
---
![image](https://github.com/user-attachments/assets/32c864c4-e9ec-4739-bd05-6595639cec76)

```sql
select
strftime('%Y',ValidityPeriod) as "ValidityYear",
count(*) as "TotalPatients"
from
Insurance 
group by
strftime('%Y',ValidityPeriod)
order by
ValidityYear;
```

**Output:**

![image](https://github.com/user-attachments/assets/831d9a3a-5558-4627-a89c-c07b8d26d192)

**Question 4**
---
![image](https://github.com/user-attachments/assets/71906ed7-78ea-44d4-9990-e8c074c748ca)

```sql
select
count(*) as "COUNT"
from
customer
where
city!= 'Noida';
```

**Output:**

![image](https://github.com/user-attachments/assets/6342c50b-70a2-4905-9ee9-ed6129b70079)

**Question 5**
---
![image](https://github.com/user-attachments/assets/3528539b-aabc-4bd5-850f-f9a7d61aacf7)

```sql
select
name as "fruit_name",
min(inventory) as "lowest_quantity"
from
fruits
group by
name
order by
min(inventory)asc
limit 1;
```

**Output:**

![image](https://github.com/user-attachments/assets/0fbb8401-cfb1-4e7e-a6f2-bd14869b93a3)

**Question 6**
---
![image](https://github.com/user-attachments/assets/5f791993-62f7-4019-91b7-3b6f558cfebd)

```sql
select
name,
max(length(name)) as "length"
from
customer
order by
max(length(name))asc
 limit 1;
```

**Output:**

![image](https://github.com/user-attachments/assets/cf43eee9-fdd3-49ea-b2d2-fc0b0218d84a)

**Question 7**
---
![image](https://github.com/user-attachments/assets/18fd99cb-8f07-415c-995a-a8e17f538726)

```sql
select
name,
email,
min(length(email)) as"min_email_length"
from
customer
order by
min(length(email))
limit 1;
```

**Output:**

![image](https://github.com/user-attachments/assets/fcf5f746-ee16-46e1-b188-d9d89603db48)

**Question 8**
---
![image](https://github.com/user-attachments/assets/efa2ff91-65b8-47ab-8952-6fe988945f5b)

```sql
select 
(age/5)*5 as "age_group",
min(salary) as"MIN(salary)"
from
customer1
group by
(age/5)*5
having
min(salary)<2000
order by
age_group;
```

**Output:**

![image](https://github.com/user-attachments/assets/31ba049c-0018-4167-a768-57f8720b1181)

**Question 9**
---
![image](https://github.com/user-attachments/assets/61e5f54f-5831-4c83-b7b6-b4685763a205)

```sql
select
jdate,
sum(workhour) as "SUM(workhour)"
from
employee1
group by
jdate
having
sum(workhour)>40
order by
jdate;
```

**Output:**

![image](https://github.com/user-attachments/assets/953ddc6a-4440-4471-a0b9-d68882161c4d)

**Question 10**
---
![image](https://github.com/user-attachments/assets/78b34b18-8d19-4a9b-b3c5-d90f9be395df)

```sql
select
address,
sum(salary) as "SUM(salary)"
from
customer1
group by
address
having
sum(salary)>2000
order by
address;
```

**Output:**

![image](https://github.com/user-attachments/assets/d77ff3a2-c1c2-4843-8e4b-26c41ad2ecda)


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
