# SQL notes :

### Association :

In SQL, an association is **a business component that defines a relationship between two entity  objects based on shared attributes**. The relationship can be `one-to-one`, `one-to-many`, or `many-to-many`. Associations allow entity objects to access each other's data through a persistent reference.

- One to One relationship →
    
    xA one-to-one (1:1) relationship in SQL is **a unique association between two tables, where each record in one table is associated with exactly one record in the other table**:

    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/290c2244-a59c-4c25-b23d-395300d6f68d/3eda1028-e0c7-4d08-bdd7-63759ffb402e/Untitled.png)

- One to many relationship →
    
     suppose when we registerted in any E-commerce Website than our unique customer id is generated. So every time we purchase any product on that e-commerce website so that our unique customer id used each and every time so that we can say that this is the one to many relationship. 
    

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/290c2244-a59c-4c25-b23d-395300d6f68d/7fafc8ef-66b0-42d3-97a7-8ebcda12f983/Untitled.png)

- Many to Many relationship → A many-to-many (M:N) relationship in SQL is **when multiple records in one table are related to multiple records in another table**. For example, a blog application might have a many-to-many relationship between posts and authors, where each post can have many authors and each author can write many posts

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/290c2244-a59c-4c25-b23d-395300d6f68d/7ad0daf5-d065-46a0-bfa3-a6fab56574ee/Untitled.png)

## Association : [magic methods]

https://medium.com/@tavilesa12/dealing-with-many-to-many-associations-in-sequelize-bddc34201b80

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/290c2244-a59c-4c25-b23d-395300d6f68d/94582910-8065-4704-9166-27f08526df52/Untitled.png)

### **Advanced M:N Associations :**

- Many to Many relationship with sequelize
```SQL
- The simplest way to define the Many-to-Many relationship is:

User.belongsToMany(Profile, { through: 'User_Profiles' });
Profile.belongsToMany(User, { through: 'User_Profiles' });

### Types of Errors :

- https://sequelize-mock.readthedocs.io/en/stable/api/errors/

> Example :
> 
> - **ValidationError**
> - **DatabaseError**
> - **UniqueConstraint**
> - **ForeignKeyConstraintError**
> - **ConnectionError**
> - **ConnectionRefusedError**
> - **AccessDeniedError**
> - **ClientSideError**

# SQL Queries →

### CREATE DATABASE :

```sql
CREATE DATABASE <DB_NAME>;

//ex 
CREATE TABLE Booking_Service;

```

### USE DATABASE [ SELECT DATABASE ]

```sql
USE <DB_NAME>

//EX
USE Booking_Service;
```

### CREATE TABLE :

```sql
// Syntax
create table <TABLE_NAME>(
Id <DATATYPE> SIZE,
Name <DATATYPE> SIZE,
LastName <DATATYPE> SIZE,
ity <DATATYPE> SIZE
);

//ex ----->
create table user1 (
Id int,
Name varchar(255),
LastName varchar(255),
City varchar(255)
);
```

### IF NOT EXISTS

```sql
CREATE TABLE IF NOT EXISTS user1 (
Name varchar(20) NOT NULL,
Gender ENUM("MALE","FEMALE","TRANSGENDER"),
Salary DECIMAL,
id int AUTO_INCREMENT,
PRIMARY KEY(id)
);

```

### DISTINCT CLAUSE →

```sql
// Diffination :
DISTINCT CLAUSE for different specius or different values of the records.

// Syntax :
SELECT DISTINCT SALARY FROM User1;

```

### Retrieve Everything from the Table :

```sql
SELECT <attributes_1> <attributes_2>... from <NAME_OF_THE TABLE>

// CODE :
 **SELECT NAME , GENDER FROM USER1;** 
```

### WHERE CLAUSE →
```sql
select * from user1 where salary <= 15000;

// output
+---------+--------+--------+----+
| Name    | Gender | Salary | id |
+---------+--------+--------+----+
| Kamlesh | MALE   |  12500 |  1 |
| SHANKAR | MALE   |  13500 |  3 |
+---------+--------+--------+----+
```

### OPERATOR 
```sql
> , < , >= , <= , != , <> (NOT EQUAL TO) , = (Equlas TO), IN , etc. 
```

### LIKE :
```sql
// syntax
SELECT COL1, COL2.... FROM <TABLE_NAME> WHERE COLUMN 1 LIKE %string%;

// code :
select Name from user1 where name like "S%"; // prefix search
 // output :
 +---------+    
| Name    |
+---------+
| SUMAN   |
| SHANKAR |
+---------+


SELECT * from uesr1 where name like "S%"; // SELECT ALL DATA WHICH IS MATCHED
+---------+--------+--------+----+
| Name    | Gender | Salary | id |
+---------+--------+--------+----+
| SUMAN   | FEMALE |  18500 |  2 |
| SHANKAR | MALE   |  13500 |  3 |
+---------+--------+--------+----+

SELECT * FROM USER1 WHERE NAME LIKE "%ESH"; // SUFFIX STRING MATCHING..
+---------+--------+--------+----+
| Name    | Gender | Salary | id |
+---------+--------+--------+----+
| Kamlesh | MALE   |  12500 |  1 |
| MAHESH  | MALE   |  25000 |  5 |
+---------+--------+--------+----+

SELECT * FROM USER1 WHERE NAME LIKE %S% // substring matching..
+---------+--------+--------+----+
| Name    | Gender | Salary | id |
+---------+--------+--------+----+
| Kamlesh | MALE   |  12500 |  1 |
| SUMAN   | FEMALE |  18500 |  2 |
| SHANKAR | MALE   |  13500 |  3 |
| MAHESH  | MALE   |  25000 |  5 |
+---------+--------+--------+----+
```

### ORDER BY - CLAUSE
```sql
 select * from user1 Order By salary;
 +---------+--------+--------+----+
| Name    | Gender | Salary | id |
+---------+--------+--------+----+
| Kamlesh | MALE   |  12500 |  1 |
| SHANKAR | MALE   |  13500 |  3 |
| SUMAN   | FEMALE |  18500 |  2 |
| PANKAJ  | MALE   |  25000 |  4 |
| MAHESH  | MALE   |  25000 |  5 |
+---------+--------+--------+----+
// By defalut Order by arrange the table in Accesding order.

// IF you manully decide the arrangement then -->
select * from user1 Order By salary desc;
+---------+--------+--------+----+
| Name    | Gender | Salary | id |
+---------+--------+--------+----+
| PANKAJ  | MALE   |  25000 |  4 |
| MAHESH  | MALE   |  25000 |  5 |
| SUMAN   | FEMALE |  18500 |  2 |
| SHANKAR | MALE   |  13500 |  3 |
| Kamlesh | MALE   |  12500 |  1 |
+---------+--------+--------+----+
// Vales arranges in Decending order by :-

Note : If two values are same in the table and we arranges the data using that column
       than we use Another column to filter out.

// Ex..
select * from user1 Order By salary desc, Name desc;
+---------+--------+--------+----+
| Name    | Gender | Salary | id |
+---------+--------+--------+----+
| PANKAJ  | MALE   |  25000 |  4 |
| MAHESH  | MALE   |  25000 |  5 |
| SUMAN   | FEMALE |  18500 |  2 |
| SHANKAR | MALE   |  13500 |  3 |
| Kamlesh | MALE   |  12500 |  1 |
+---------+--------+--------+----+
// Here the data are sorted in lexigrophically decending order using `name` Attribute.
// pankaj , mahesh [values] same but sorted in decending order.

select * from user1 Order By salary desc, Name asc;
+---------+--------+--------+----+
| Name    | Gender | Salary | id |
+---------+--------+--------+----+
| MAHESH  | MALE   |  25000 |  5 |
| PANKAJ  | MALE   |  25000 |  4 |
| SUMAN   | FEMALE |  18500 |  2 |
| SHANKAR | MALE   |  13500 |  3 |
| Kamlesh | MALE   |  12500 |  1 |
+---------+--------+--------+----+
// Here the data are sorted in lexigrophically Accending order using the'name'attribute.
// pankaj , mahesh [values] same but sorted in Accending order.
```


## LIMIT , OFFSET - [clauses]

- LIMIT USED FOR SORT THE DATA either Accending or Decending order.
- This two method are use to set the ranges of data to Show.
    - **Limit →** The Limit clause used to set the number of data to print at a time in a WEB page.
    - **Offset →** The OFFSET clause **specifies how many rows to skip from the beginning of a query's results before returning them to the application**.
    - **Note :** This keyword is often used in combination with the LIMIT clause to paginate results, especially when dealing with large datasets

```sql
select * from user1;
+---------+--------+--------+----+
| Name    | Gender | Salary | id |
+---------+--------+--------+----+
| Kamlesh | MALE   |  12500 |  1 |
| SUMAN   | FEMALE |  18500 |  2 |
| SHANKAR | MALE   |  13500 |  3 |
| PANKAJ  | MALE   |  25000 |  4 |
| MAHESH  | MALE   |  25000 |  5 |
+---------+--------+--------+----+

select * from user1 Order by salary , Name desc Limit 3 offset 2;
+--------+--------+--------+----+
| Name   | Gender | Salary | id |
+--------+--------+--------+----+
| SUMAN  | FEMALE |  18500 |  2 |
| PANKAJ | MALE   |  25000 |  4 |
| MAHESH | MALE   |  25000 |  5 |
+--------+--------+--------+----+

select * from user1 Order by salary ,Name desc Limit 3 offset 3;
+--------+--------+--------+----+
| Name   | Gender | Salary | id |
+--------+--------+--------+----+
| PANKAJ | MALE   |  25000 |  4 |
| MAHESH | MALE   |  25000 |  5 |
+--------+--------+--------+----+
```

### Get limit number of data
```sql

select * from user1 Order by salary , Name desc Limit 3;
+--------+--------+--------+----+
| Name   | Gender | Salary | id |
+--------+--------+--------+----+
| SUMAN  | FEMALE |  18500 |  2 |
| PANKAJ | MALE   |  25000 |  4 |
| MAHESH | MALE   |  25000 |  5 |
+--------+--------+--------+----+
```

### UPDATE VALUES :
```sql
 UPDATE USER1 SET NAME = "SHIVANI" WHERE ID = 4;
+---------+--------+--------+----+
| Name    | Gender | Salary | id |
+---------+--------+--------+----+
| Kamlesh | MALE   |  12500 |  1 |
| SUMAN   | FEMALE |  18500 |  2 |
| SHANKAR | MALE   |  13500 |  3 |
| SHIVANI | MALE   |  25000 |  4 |
| MAHESH  | MALE   |  25000 |  5 |
+---------+--------+--------+----+

UPDATE USER1 SET GENDER =  "FEMALE" WHERE ID = 4;
+---------+--------+--------+----+
| Name    | Gender | Salary | id |
+---------+--------+--------+----+
| Kamlesh | MALE   |  12500 |  1 |
| SUMAN   | FEMALE |  18500 |  2 |
| SHANKAR | MALE   |  13500 |  3 |
| SHIVANI | FEMALE |  25000 |  4 |
| MAHESH  | MALE   |  25000 |  5 |
+---------+--------+--------+----+
```

### ALTER TABLE [changes to the table]
```sql
ALTER TABLE USER1 ADD DOB DATETIME;

mysql> select * from user1;
+---------+--------+--------+----+------+
| Name    | Gender | Salary | id | DOB  |
+---------+--------+--------+----+------+
| Kamlesh | MALE   |  12500 |  1 | NULL |
| SUMAN   | FEMALE |  18500 |  2 | NULL |
| SHANKAR | MALE   |  13500 |  3 | NULL |
| SHIVANI | FEMALE |  25000 |  4 | NULL |
| MAHESH  | MALE   |  25000 |  5 | NULL |
+---------+--------+--------+----+------+

// DELETE ADDED NEW COLUMN 
//  CODE :
 ALTER TABLE USER1 DROP DOB;
```

### ALTER TABLE [use for]→ 
```sql
-- ALter table basically use for add column , delete column , modify existing column
-- data.

-- Add Column Syntax ->
Alter Table Table_name
Add column Colum_name;

-- DROP column syntax ->
Alter table table_name
Delete column column_name;

-- Modify/Alter table data ->
Alter table table_name
Alter column column_name datatype;

-- Change column name
ALTER TABLE table_name
RENAME COLUMN oldcolumn_name to newcolumn_name;
```

### DISTINCT CLAUSE
```sql
-- The SQL DISTINCT keyword is used to retrieve unique values from a database table's 
-- column or set of columns. It removes duplicate records, ensuring that only distinct,
-- non-repeated values are returned.

Syntax 
Select DISTINCT [column_name] from [table_name];

```

## SQL Functions →

- Basically in sql there are two types of Funcitons -
    - System defined Function.
    - User defined Funciton.

### System Defined Functions→

- Aggregate function.
```sql
1. abs() →  This returns an absolute number of the given number, which means
				 -> abs(-10.63) = 10.63
2. rand(10) -> This will generate a random number of 10 characters.
3. round(17.56719,3) ->	This will round off the given number to 3 places of 
												decimal meaning 17.567
4. upper('dotnet') ->	This will return the upper case of the given string meaning 'DOTNET'
5. lower('DOTNET') ->	This will return the lowercase of the given string means 'dotnet'
6. ltrim('  dotnet') -> This will remove the spaces from the left-hand side of the 'dotnet' 
											string.
7. convert(int, 15.56) -> 	This will convert the given float value to integer means 15.
8. Length() -> returns the length of the values of the text.
9. now() ->  return the current system date and time.
10. substring() -> extracts a substring from the string.[SQL SERVER Function]
```

### Extract Function→
```sql
Syntax -> Select Extract(month date_field) from table_name;

- Year
- Quater
- Month
- week
- Day 
- Hour 
- Minute
- DOW (Day OF Week)
- DOY (Day OF Year)
```

## JOINS

```sql
- What is Joins.
- types of Joins.
- which type of Joins Use.
- Use of Joins.
- Join Syntax.
```

### SQL joins →

- SQL joins basicallly a concept of join or add two or more than two tables based on related column between them.

### Types of Joins →

1. Inner Join
2. Left Join 
3. Right Join
4. Full join

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/290c2244-a59c-4c25-b23d-395300d6f68d/5b4f4969-576f-4187-a48f-2c9f9353492b/image.png)

## INNER JOIN

## INNER JOIN

```sql
select * from marks;
+------+-------+--------+
| rno  | marks | Status |
+------+-------+--------+
|    1 |   345 | PASS   |
|    1 |   280 | PASS   |
|    1 |   385 | PASS   |
|    2 |   285 | PASS   |
|    4 |   150 | FAIL   |
|    5 |   180 | FAIL   |
|    6 |   320 | PASS   |
+------+-------+--------+

select * from stud;
+------+----------+-----------+--------+--------+---------+------+-------------+--------+
| rno  | name     | city      | active | branch | Passout | Year | PaymentMode | Fee    |
+------+----------+-----------+--------+--------+---------+------+-------------+--------+
|    1 | Adiya    | Bihar     |      0 | MCA    | yes     | NULL | NetBanking  | 150000 |
|    2 | Suraj    | MP        |      1 | BBA    | no      |    1 | Credit Card | 250000 |
|    4 | Mahi     | Jammu     |      1 | LLB    | no      |    1 | Credit Card | 500000 |
|    5 | shruti   | Kathmandu |      0 | BCA    | yes     | NULL | Debit Card  |  80000 |
|    6 | Priya    | Ranchi    |      1 | Btech  | no      |    1 | Netbanking  | 135400 |
|    7 | Mahendra | Ayudhya   |      0 | Btech  | yes     | NULL | Netbanking  | 196500 |
+------+----------+-----------+--------+--------+---------+------+-------------+--------+

select * from stud inner join marks on stud.rno = marks.rno;
+------+--------+-----------+--------+--------+---------+------+-------------+--------+------+-------+--------+
| rno  | name   | city      | active | branch | Passout | Year | PaymentMode | Fee    | rno  | marks | Status |
+------+--------+-----------+--------+--------+---------+------+-------------+--------+------+-------+--------+
|    1 | Adiya  | Bihar     |      0 | MCA    | yes     | NULL | NetBanking  | 150000 |    1 |   345 | PASS   |
|    1 | Adiya  | Bihar     |      0 | MCA    | yes     | NULL | NetBanking  | 150000 |    1 |   280 | PASS   |
|    1 | Adiya  | Bihar     |      0 | MCA    | yes     | NULL | NetBanking  | 150000 |    1 |   385 | PASS   |
|    2 | Suraj  | MP        |      1 | BBA    | no      |    1 | Credit Card | 250000 |    2 |   285 | PASS   |
|    4 | Mahi   | Jammu     |      1 | LLB    | no      |    1 | Credit Card | 500000 |    4 |   150 | FAIL   |
|    5 | shruti | Kathmandu |      0 | BCA    | yes     | NULL | Debit Card  |  80000 |    5 |   180 | FAIL   |
|    6 | Priya  | Ranchi    |      1 | Btech  | no      |    1 | Netbanking  | 135400 |    6 |   320 | PASS   |
+------+--------+-----------+--------+--------+---------+------+-------------+--------+------+-------+--------+
```

## LEFT JOIN

- The `LEFT JOIN` keyword returns all records from the left table (table1), and the matching records from the right table (table2). The result is 0 records from the right side, if there is no match.

```sql
Syntax ->
select * from table_A as A Left Join On Table_A.id = Table_B.id;

Select * from stud Left join marks on stud.rno = marks.rno;
+------+----------+-----------+--------+--------+---------+------+-------------+--------+------+-------+--------+
| rno  | name     | city      | active | branch | Passout | Year | PaymentMode | Fee    | rno  | marks | Status |
+------+----------+-----------+--------+--------+---------+------+-------------+--------+------+-------+--------+
|    1 | Adiya    | Bihar     |      0 | MCA    | yes     | NULL | NetBanking  | 150000 |    1 |   385 | PASS   |
|    1 | Adiya    | Bihar     |      0 | MCA    | yes     | NULL | NetBanking  | 150000 |    1 |   280 | PASS   |
|    1 | Adiya    | Bihar     |      0 | MCA    | yes     | NULL | NetBanking  | 150000 |    1 |   345 | PASS   |
|    2 | Suraj    | MP        |      1 | BBA    | no      |    1 | Credit Card | 250000 |    2 |   285 | PASS   |
|    4 | Mahi     | Jammu     |      1 | LLB    | no      |    1 | Credit Card | 500000 |    4 |   150 | FAIL   |
|    5 | shruti   | Kathmandu |      0 | BCA    | yes     | NULL | Debit Card  |  80000 |    5 |   180 | FAIL   |
|    6 | Priya    | Ranchi    |      1 | Btech  | no      |    1 | Netbanking  | 135400 |    6 |   320 | PASS   |
|    7 | Mahendra | Ayudhya   |      0 | Btech  | yes     | NULL | Netbanking  | 196500 | ***~~NULL~~ |  ~~NULL~~ | ~~NULL~~***   |
+------+----------+-----------+--------+--------+---------+------+-------------+--------+------+-------+--------+
```

## RIGHT JOIN

```sql
mysql> select * from stud Right Join Marks on marks.rno = stud.rno;
+------+--------+-----------+--------+--------+---------+------+-------------+--------+------+-------+--------+
| rno  | name   | city      | active | branch | Passout | Year | PaymentMode | Fee    | rno  | marks | Status |
+------+--------+-----------+--------+--------+---------+------+-------------+--------+------+-------+--------+
|    1 | Adiya  | Bihar     |      0 | MCA    | yes     | NULL | NetBanking  | 150000 |    1 |   345 | PASS   |
|    1 | Adiya  | Bihar     |      0 | MCA    | yes     | NULL | NetBanking  | 150000 |    1 |   280 | PASS   |
|    1 | Adiya  | Bihar     |      0 | MCA    | yes     | NULL | NetBanking  | 150000 |    1 |   385 | PASS   |
|    2 | Suraj  | MP        |      1 | BBA    | no      |    1 | Credit Card | 250000 |    2 |   285 | PASS   |
|    4 | Mahi   | Jammu     |      1 | LLB    | no      |    1 | Credit Card | 500000 |    4 |   150 | FAIL   |
|    5 | shruti | Kathmandu |      0 | BCA    | yes     | NULL | Debit Card  |  80000 |    5 |   180 | FAIL   |
|    6 | Priya  | Ranchi    |      1 | Btech  | no      |    1 | Netbanking  | 135400 |    6 |   320 | PASS   |
+------+--------+-----------+--------+--------+---------+------+-------------+--------+------+-------+--------+
```

## FULL JOIN

- **`MySQL doesn't natively support FULL OUTER JOINs`**, but you can achieve similar results by combining `LEFT` and `RIGHT OUTER JOINs`. A full outer join returns all matching and non-matching rows from the joined tables.

```sql
Select * from stud Left join marks On Stud.rno = marks.rno Union All select * from Stud Right Join Marks On stud.rno = marks.rno;
+------+----------+-----------+--------+--------+---------+------+-------------+--------+------+-------+--------+
| rno  | name     | city      | active | branch | Passout | Year | PaymentMode | Fee    | rno  | marks | Status |
+------+----------+-----------+--------+--------+---------+------+-------------+--------+------+-------+--------+
|    1 | Adiya    | Bihar     |      0 | MCA    | yes     | NULL | NetBanking  | 150000 |    1 |   385 | PASS   |
|    1 | Adiya    | Bihar     |      0 | MCA    | yes     | NULL | NetBanking  | 150000 |    1 |   280 | PASS   |
|    1 | Adiya    | Bihar     |      0 | MCA    | yes     | NULL | NetBanking  | 150000 |    1 |   345 | PASS   |
|    2 | Suraj    | MP        |      1 | BBA    | no      |    1 | Credit Card | 250000 |    2 |   285 | PASS   |
|    4 | Mahi     | Jammu     |      1 | LLB    | no      |    1 | Credit Card | 500000 |    4 |   150 | FAIL   |
|    5 | shruti   | Kathmandu |      0 | BCA    | yes     | NULL | Debit Card  |  80000 |    5 |   180 | FAIL   |
|    6 | Priya    | Ranchi    |      1 | Btech  | no      |    1 | Netbanking  | 135400 |    6 |   320 | PASS   |
|    7 | Mahendra | Ayudhya   |      0 | Btech  | yes     | NULL | Netbanking  | 196500 | ~~***NULL |  NULL | NULL***~~   |
|    1 | Adiya    | Bihar     |      0 | MCA    | yes     | NULL | NetBanking  | 150000 |    1 |   345 | PASS   |
|    1 | Adiya    | Bihar     |      0 | MCA    | yes     | NULL | NetBanking  | 150000 |    1 |   280 | PASS   |
|    1 | Adiya    | Bihar     |      0 | MCA    | yes     | NULL | NetBanking  | 150000 |    1 |   385 | PASS   |
|    2 | Suraj    | MP        |      1 | BBA    | no      |    1 | Credit Card | 250000 |    2 |   285 | PASS   |
|    4 | Mahi     | Jammu     |      1 | LLB    | no      |    1 | Credit Card | 500000 |    4 |   150 | FAIL   |
|    5 | shruti   | Kathmandu |      0 | BCA    | yes     | NULL | Debit Card  |  80000 |    5 |   180 | FAIL   |
|    6 | Priya    | Ranchi    |      1 | Btech  | no      |    1 | Netbanking  | 135400 |    6 |   320 | PASS   |
+------+----------+-----------+--------+--------+---------+------+-------------+--------+------+-------+--------+
```

## Windows Functions

- Window functions apply to aggregate and ranking functions over a particular window (set of rows).
- OVER clause is used with window functions to define that window. OVER clause does two things

### Aggregate Functions -

![WhatsApp Image 2024-08-16 at 17.20.16_9f867abe.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/290c2244-a59c-4c25-b23d-395300d6f68d/b1ff8c22-912a-46ca-9d70-7ee411f157a6/WhatsApp_Image_2024-08-16_at_17.20.16_9f867abe.jpg)

- Aggregate Function - with ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING

![WhatsApp Image 2024-08-16 at 17.20.15_414d8888.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/290c2244-a59c-4c25-b23d-395300d6f68d/52a89eb5-bb0f-42de-a7e8-1b4f153c1c32/WhatsApp_Image_2024-08-16_at_17.20.15_414d8888.jpg)