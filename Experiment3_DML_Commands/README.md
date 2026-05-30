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
--
<img width="1032" height="287" alt="image" src="https://github.com/user-attachments/assets/8df36e91-1bc4-4c7c-88f8-600e5a094784" />

```sql
UPDATE sales
SET sell_price = sell_price * 1.05
WHERE product_id = 15
  AND sale_date = '2023-01-31';
```

**Output:**

<img width="1193" height="453" alt="image" src="https://github.com/user-attachments/assets/ea78ca60-edb1-437d-b74f-7c7fb4ca4a19" />

**Question 2**
---
<img width="1050" height="544" alt="image" src="https://github.com/user-attachments/assets/bd91a755-a383-47c2-89ee-d0f71f4cdb7b" />

```sql
UPDATE products
SET sell_price = ROUND(sell_price * 1.10, 2)
WHERE supplier_id = 6; 

```

**Output:**

<img width="1217" height="525" alt="image" src="https://github.com/user-attachments/assets/5d5bb903-9bed-4d4f-8e3b-aff638700acb" />

**Question 3**
---
<img width="1250" height="940" alt="image" src="https://github.com/user-attachments/assets/5ed3e33f-7165-4f5d-ae20-e48bfe40b756" />

```sql
UPDATE employees
SET salary = ROUND(CASE
WHEN department_id = 40 THEN salary * 1.25
WHEN department_id = 90 THEN salary * 1.15
WHEN department_id = 110 THEN salary * 1.10
ELSE salary
END, 0);
```

**Output:**

<img width="1190" height="457" alt="image" src="https://github.com/user-attachments/assets/d2e929d1-cc11-423c-b465-8d9cb2612351" />

**Question 4**
---
<img width="1048" height="333" alt="image" src="https://github.com/user-attachments/assets/85715249-2a0c-4985-ab29-74270049143e" />

```sql
update suppliers 
set supplier_name ='A1 Suppliers'
where supplier_id=8;
```

**Output:**

<img width="1206" height="403" alt="image" src="https://github.com/user-attachments/assets/21101c5d-c398-43f2-99f4-62b48dd6b225" />

**Question 5**
---
<img width="1169" height="573" alt="image" src="https://github.com/user-attachments/assets/ece32ff1-3c1a-4ecc-93fd-4e84fe3356a6" />

```sql
UPDATE products
SET reorder_lvl = reorder_lvl * 0.70
WHERE cost_price > 50
  AND quantity < 100;
```

**Output:**

<img width="1185" height="443" alt="image" src="https://github.com/user-attachments/assets/3ce7f997-fe12-4cd8-8e77-73e1a66c0a1b" />

**Question 6**
---
<img width="822" height="479" alt="image" src="https://github.com/user-attachments/assets/d50d6f79-1f27-4f4e-b349-4825b7bb88f6" />

```sql
DELETE FROM doctors
WHERE doctor_id BETWEEN 2 AND 4;
```

**Output:**

<img width="1198" height="792" alt="image" src="https://github.com/user-attachments/assets/b3968838-baa4-48de-9376-7efffb8b3707" />

**Question 7**
---
<img width="1215" height="476" alt="image" src="https://github.com/user-attachments/assets/ba3acfac-c254-4346-82ce-7517c82cd66c" />

```sql
delete from customer
where  CUST_COUNTRY not in ( 'India', 'USA');
```

**Output:**

<img width="1209" height="555" alt="image" src="https://github.com/user-attachments/assets/3830c607-26cd-4be1-b7da-876e1f69df31" />

**Question 8**
---
<img width="1223" height="279" alt="image" src="https://github.com/user-attachments/assets/8dcb7e24-8e3c-4b8c-bf7c-16d4eb8e14c4" />

```sql
delete from customer 
where OPENING_AMT between 4000 and 6000;
```

**Output:**

<img width="1184" height="612" alt="image" src="https://github.com/user-attachments/assets/f1793811-8551-4cd3-bf11-f0748caac85c" />

**Question 9**
---
<img width="1212" height="306" alt="image" src="https://github.com/user-attachments/assets/4a61b39d-3c41-4ca7-8a14-d3ff16d80791" />

```sql
delete from customer
where (grade>2 and payment_amt<(select avg(payment_amt)
from customer))
or outstanding_amt>8000;
```

**Output:**

<img width="1183" height="659" alt="image" src="https://github.com/user-attachments/assets/76daa8f9-f73f-4d8f-8124-af3b40bce3c5" />

**Question 10**
---
<img width="1207" height="301" alt="image" src="https://github.com/user-attachments/assets/85360bfc-eccb-4a75-8348-d0b1fad0dfa3" />

```sql
delete from customer
where GRADE >=2;
```

**Output:**

<img width="693" height="534" alt="image" src="https://github.com/user-attachments/assets/4bc3fa7c-8139-429a-b9cb-b883857a54b7" />

## Grade
<img width="1350" height="70" alt="image" src="https://github.com/user-attachments/assets/2cbe5762-511e-4f8c-bcde-226f1ab63609" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
