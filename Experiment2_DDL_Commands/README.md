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
<img width="1202" height="240" alt="image" src="https://github.com/user-attachments/assets/ba357bff-84e3-4762-9489-8a31464e5470" />

```sql
INSERT INTO Customers (CustomerID, Name, Address, City, ZipCode)
VALUES(301, 'Michael Jordan', '123 Maple St', 'Chicago', 60616);
```

**Output:**

<img width="1201" height="232" alt="image" src="https://github.com/user-attachments/assets/eba22ecd-0fc0-4d96-89ec-fda3a6084fde" />

**Question 2**
---
<img width="933" height="259" alt="image" src="https://github.com/user-attachments/assets/1f99ac8c-46e5-4d7f-a14b-75b204704fab" />

```sql
ALTER TABLE customer 
RENAME city to location;

```

**Output:**

<img width="1179" height="330" alt="image" src="https://github.com/user-attachments/assets/ba9efb0e-42cd-4611-b232-fcc7aabb020f" />

**Question 3**
---
<img width="1207" height="66" alt="image" src="https://github.com/user-attachments/assets/9cc2d73e-6bc5-491b-bff8-ea6ca14ac682" />

```sql
ALTER TABLE Companies RENAME name to first_name;
ALTER TABLE Companies ADD column mobilenumber number;
alter table Companies add column DOB Date;
alter table Companies add column State varchar(30);
```

**Output:**

<img width="1220" height="422" alt="image" src="https://github.com/user-attachments/assets/bdb3f246-1a66-4a43-968b-4aa3b3bb4ebf" />

**Question 4**
---
<img width="563" height="168" alt="image" src="https://github.com/user-attachments/assets/6c091a3a-955c-43f4-a177-9424aba292c8" />

```sql
CREATE TABLE Reviews(
    ReviewID INTEGER,
    ProductID INTEGER,
    Rating REAL,
    ReviewText TEXT
);
```

**Output:**

<img width="1192" height="399" alt="image" src="https://github.com/user-attachments/assets/775c351f-f696-47be-9f1d-a7fab1bcb368" />

**Question 5**
---
<img width="923" height="248" alt="image" src="https://github.com/user-attachments/assets/7752760c-a198-4433-a25e-d5b873c80d35" />

```sql
CREATE TABLE item (
    item_id TEXT primary key,
    item_desc TEXT NOT NULL,
    rate INTEGER NOT NULL,
    icom_id TEXT CHECK (length(icom_id)=4),
    FOREIGN KEY (icom_id) REFERENCES company(com_id)  
    on update set null  on delete  set null);
```

**Output:**

<img width="1190" height="350" alt="image" src="https://github.com/user-attachments/assets/f29b1303-39bf-44e2-aa21-bea9105be39a" />

**Question 6**
---
<img width="987" height="201" alt="image" src="https://github.com/user-attachments/assets/d81fa7a6-e4f8-4820-9471-9aa9d1f5590e" />

```sql
CREATE TABLE contacts(
    contact_id INTEGER primary key,
    first_name TEXT not NULL,
    last_name TEXT not NULL,
    email TEXT,
    phone TEXT not NULL CHECK (length(phone)>=10)
    );
```

**Output:**

<img width="1199" height="310" alt="image" src="https://github.com/user-attachments/assets/b374efb9-4db2-428c-b9d7-4cdc69682ff4" />

**Question 7**
---
<img width="468" height="101" alt="image" src="https://github.com/user-attachments/assets/24e3d9b0-8f55-42b2-89e8-c088fc6d1146" />

```sql
INSERT INTO Customers(CustomerID, Name, Address, Email)
SELECT CustomerID, Name, Address, Email
FROM Old_customers
```

**Output:**

<img width="1203" height="286" alt="image" src="https://github.com/user-attachments/assets/7eaf857f-5af4-4ce8-95e2-4f1b77b0d8c4" />

**Question 8**
---
<img width="793" height="165" alt="image" src="https://github.com/user-attachments/assets/39793172-0d78-488d-9a5e-923577296074" />

```sql
CREATE TABLE Shipments(
    ShipmentID INTEGER primary key,
    ShipmentDate DATE,
    SupplierID INTEGER,
    OrderID INTEGER,
    FOREIGN KEY (SupplierID) REFERENCES Suppliers(SupplierID),
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
    );
```

**Output:**

<img width="1204" height="227" alt="image" src="https://github.com/user-attachments/assets/213cb587-a930-487a-9b7a-ac9c98a6712b" />

**Question 9**
---
<img width="470" height="146" alt="image" src="https://github.com/user-attachments/assets/b93af86a-1114-4d39-b4fb-eb312eb81ca6" />

```sql
insert into products(Name,Category,Price,Stock)
values("Smartphone","Electronics",800,150),("Headphones" ,"Accessories",200,300)
```

**Output:**

  <img width="1187" height="358" alt="image" src="https://github.com/user-attachments/assets/c1ef4dff-41a0-4f62-afb3-b2d58bbf102c" />

**Question 10**
---
<img width="1058" height="177" alt="image" src="https://github.com/user-attachments/assets/cee7f4d2-9357-41cc-9b09-4bd52dcf93cc" />

```sql
create table Attendance(
AttendanceID int primary key,
EmployeeID int ,
AttendanceDate date,
Status text check(status in('Present', 'Absent', 'Leave')),
foreign key (EmployeeID) references Employees(EmployeeID));
```

**Output:**

<img width="1188" height="279" alt="image" src="https://github.com/user-attachments/assets/5c84d6cc-291b-48d8-bcf8-923832af193d" />

## Grade
<img width="1373" height="75" alt="image" src="https://github.com/user-attachments/assets/0cdf878b-7e74-4fc7-a2ec-602bc1a185b7" />

## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
