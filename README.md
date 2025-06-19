# Incubator-Hub---Data-Analysis-SQL-Training

## Definition

_**SQL**_ which stands for Structured Query Language, is used for storing and managing data in a relational database management system (RDMS). It enables a user to relate with relational databases and tables using basic languages also known as _**syntax**_

Some examples of RDMS like _**MySQL**, **PostgreSQL**, **SQL Server**, **MSAccess**, **Oracle**_ all use SQL as their standard language 

## Advantages of SQL

  * Easy to understand
  * Can be used to analyze multiple tables at once
  * Can be used to analyze more complex questions than dashboard tools

## SQL Command

They are instruction lines used to communicate with databases. They are used to perform specific task, functions and queries of data

### Types of SQL

  * DDL: Data Definition Language _i.e_ **Create**, **Alter**, **Drop**, **Truncate**
  * DML: Data Manipulation language _i.e_ **Update**, **Insert**, **Delete**, **Merge**
  * DCL: Data Control Language _i.e_ **Grant**, **Revoke**
  * TCL: Transaction Control Language _i.e_ **Commit**, **Rollback**
  * DQL: Data Query Language _i.e_ **Select**

### Examples of using DDL

~~~ SQL
create database DSA_DB

---- Table
create table EMPLOYEE( 
staffid varchar(10),
FirstName varchar (10),
LastName varchar (100),
Gender nvarchar (10),
Date_of_birth date,
HireDate date,
primary key (staffid)
)

Alter table employee
Add [State of Origin] varchar (100)

select * from employee 
~~~

### Examples of using DML

~~~ SQL
----create table for payment

Create table Payment(
paymentid int identity (1,1) primary key,
Account_No bigint not null,
staffid int,
Bank varchar (255) default 'Zenith Bank',
Payment_Method varchar (50) check (Payment_Method = 'Cash' or Payment_Method = 'Transfer')
)

---How to use Update----Staffid AB234

Update Employee
set LastName = 'Abubakar'
where staffid = 'AB234' 



Update Payment
set Account_No = '2198773830', Bank = 'GT bank'
where paymentid = 19

select * from Payment

Update salary
set department = 'Information Tech'
where staffid = 'AB223'

select * from salary
~~~

### Examples of using DQL

~~~ SQL
----calculate total number of staff from each state---

select [State of Origin], count(distinct staffid) as TotalEmployee
from employee
group by [State of Origin]

select count (*) from employee
~~~

### SQL Data Types

We have 
 - String datatype e.g _**char**_, _**varchar**_, _**nchar**_, _**varbinary**_, _**nvarchar**_
 - Binary datatype e.g _**True/False**_, _**Yes/No**_
 - Numeric datatype e.g _**bit**_, _**tinyint**_, _**smallint**_, _**int**_, _**bigint**_, _**decimal**_, _**money**_, _**float**_
 - Date datatype e.g _**date**_, _**datetime**_, _**timestamp**_

### SQL Keys

SQL Keys are special field in a table that helps to:
 - Create relationship between tables
 - Maintain uniqueness
 - Ensure data is consistent and valid

#### Primary Key:
A special type of key that uniquely identifies each record in a table. Each table can have only one
primary key.
Example: _**Employee_id**_ in the Employee table.

#### Foreign Key:
A field in one table that uniquely identifies a row of another table, creating a relationship between the
two tables.
Example: _**Employee_id**_ in the Salary table is a foreign key (FK) that references the _**Employee_id**_ in the Employee table (PK)

#### Surrogate Key:
A surrogate key is a unique identifier for each record in a table, typically created by the database
itself (e.g. an auto-incrementing integer)

#### Composite Key:
Composite key (also known as compound key concatenated key) is a group of two or more columns that
identifies each row of a table uniquely.
Example: In salary tables, _**Employee_id**_ and _**Salary_month_year**_ are combined to identify each row uniquely in salary table

#### Candidate Key:
Candidate key is a key of a table which can be selected as primary key. A table can have
multiple candidate keys, out of which one can be selected as a primary key.
Example: _**Employee_id**_, _**License_Number**_, and _**Passport_Number**_

#### Alternate Key:
Alternate key is a candidate key, currently not selected as a primary key of the table
Example: _**License_Number**_ and _**Passport_Number**_

### SQL Clauses

SQL clauses are essential components of SQL (Structured Query Language) that define how
queries interact with the database. They are used to specify conditions, modify data, and
control how results are returned.

#### Group BY Clause
SQL GROUP BY statement is used to arrange identical data into groups.
 - The **GROUP BY** statement is used with the SQL SELECT statement.
 - The **GROUP BY** statement follows the **WHERE** clause in a **SELECT** statement and precedes the
**ORDER** BY clause.
 - The GROUP BY statement is used with aggregation function

#### Having Clause
 - **HAVING** clause is used to specify a search condition for a group or an aggregate.
 - Having is used in a **GROUP BY** clause. If you are not using GROUP BY clause then you
can use **HAVING** function like a **WHERE** clause

#### Order BY
 - The **ORDER BY** clause sorts the result-set in ascending or descending order.
 - It sorts the records in ascending order by default. DESC keyword is used to sort the

#### Examples:

~~~ SQL

----Use of Order by---

select [State of Origin], count(distinct staffid) as TotalEmployee
from employee
group by [State of Origin]
Order by TotalEmployee desc

----Calculate total number for staff by department----

select department, count(distinct staffid) as TotalEmployee
from salary
group by department
Order by TotalEmployee asc

select * from salary

----We noticed that the department have 2 spellings of Info Tech----
----So we needed to correct that error, so I use Update-----
Update salary
set department = 'Information Tech'
where Staffid = 'AB401'

---OR----

Update salary
set department = 'Information Tech'
where Staffid in ('AB401', 'ABXXX')

-----Having clause----

select department, count(distinct staffid) as TotalEmployee
from salary
group by department
having count(distinct staffid) >=3

~~~
#### Examples of relational operators:

~~~ SQL
-----Relational Operator/Comparison Operator----
----They are Less than <
----Greater than >

select * from salary
where salary > 500000

select * from salary
where salary < 500000

----- Range Operators----
----Between----
----Not Between---

select * from salary
where salary between 50000 and 200000

select * from salary
where salary not between 50000 and 200000

~~~

#### More Examples on operators:

~~~ SQL
---19/05/2025
---List Operators
---1. IN
---2. NOT IN

Select * from Employee
where Staffid in ('AB270', 'AB286', 'AB401')

Select * from Employee
where Firstname in ('Johnson', 'Mercy', 'Okorie')

Select * from Employee
where Staffid not in ('AB270', 'AB286', 'AB401')

----Logical Operator----
----AND
----OR

Select * from Employee
where Firstname = 'Adebowale' and Gender = 'Female'
----Returns empty table

Select * from Employee
where Firstname = 'Adebowale' and Gender = 'Male'

----Use of OR
Select * from Employee
where Firstname = 'Adebowale' or Gender = 'Female'

Select * from Employee
where Firstname = 'Adebowale' or Gender = 'Boy'

Select * from Salary
where Firstname = 'Johnson' or Department = 'Account'

Select * from Salary
where Firstname = 'Johnson' or Department = 'Information Tech'

~~~
### SQL Joins:

SQL JOIN means "to combine two or more tables". In SQL, JOIN clause is used to combine the
records from two or more tables in a database.

**INNER JOIN**

In SQL, INNER JOIN selects records that have matching values in both tables as long as the condition is satisfied.
It returns the combination of all rows from both the tables where the condition satisfies.

~~~ SQL
SELECT EMPLOYEE.EMP_NAME, PROJECT.DEPARTMENT FROM EMPLOYEE
INNER JOIN
PROJECT ON PROJECT.EMP_ID = EMPLOYEE.EMP_ID

~~~

**LEFT JOIN**

The SQL left join returns all the values from left table and the matching values from the right table. If there is
no matching join value, it will return NULL.

~~~ SQL
SELECT EMPLOYEE.EMP_NAME, PROJECT.DEPARTMENT FROM EMPLOYEE
LEFT JOIN
PROJECT ON PROJECT.EMP_ID = EMPLOYEE.EMP_ID

~~~

**RIGHT JOIN**

In SQL, RIGHT JOIN returns all the values from the rows of right table and the matched values from
the left table. If there is no matching in both tables, it will return NULL.

~~~ SQL
SELECT EMPLOYEE.EMP_NAME, PROJECT.DEPARTMENT FROM EMPLOYEE
RIGHT JOIN
PROJECT ON PROJECT.EMP_ID = EMPLOYEE.EMP_ID

~~~

**FULL JOIN**

In SQL, FULL JOIN is the result of a combination of both left and right outer join. Join tables have all the records
from both tables. It puts NULL on the place of matches not found.

~~~ SQL

SELECT EMPLOYEE.EMP_NAME, PROJECT.DEPARTMENT FROM EMPLOYEE
FULL JOIN
PROJECT ON PROJECT.EMP_ID = EMPLOYEE.EMP_ID
~~~

**More Examples**

~~~ SQL

----JOIN----

Select employee.staffid,
       employee.FirstName,
	   employee.gender,
	   employee.hiredate,
	   salary.salary_id,
	   salary.department,
	   salary.salary
from employee
join salary
on salary.Staffid = employee.staffid ---(this is creating a cnxtn for the 2 tables)

---Or


----Inner Join
----below writeup is called sql optimization---
Select e.staffid,
       e.FirstName,
	   e.gender,
	   e.hiredate,
	   s.salary_id,
	   s.department,
	   s.salary
from employee e
inner join salary s
on s.Staffid = e.staffid

Select e.staffid,
       e.FirstName,
	   e.gender,
	   e.hiredate,
	   s.salary_id,
	   s.department,
	   s.salary
from employee e
full outer join salary s
on s.Staffid = e.staffid

---Joining 3 tables

Select employee.staffid,
	   salary.salary_id,
	   payment.paymentid,
       employee.FirstName,
	   employee.gender,
	   employee.hiredate,	 
	   salary.department,
	   salary.salary,
	   payment.account_no,
	   payment.bank,
	   payment.payment_method
from employee
join salary
on salary.Staffid = employee.staffid
join payment
on payment.staffid = employee.staffid ---or payment.staffid = salary.staffid

----We can also left join---
--- I wrote this on my own----

select e.staffid,s.salary_id,p.paymentid,
       e.FirstName,e.gender,e.hiredate,
	   s.department,s.salary,p.account_no,
	   p.bank,p.payment_method
from employee e
left join salary s
on s.staffid = e.staffid
left join payment p
on p.staffid = e.staffid

~~~

**SQL Aggregate Functions**

SQL aggregate functions are powerful tools used to perform calculations on a set of
values, returning a single value that summarizes the data. They are commonly used in
conjunction with the **GROUP BY** clause to group the data by one or more columns before
applying the aggregate function.

**Examples**

~~~ SQL
Select * from Employee

select sum(Age) as [Sum of Age] from Employee

Select Avg(Age) as [Average Age] from Employee 

Select Min(Age) as [Min Age] from Employee

Select Max(Age) as [Eldest] from Employee 

Select top 3 (Age) as [Top Three] from Employee
Order by Age desc

Select top 3 (Age) as [Top Three] from Employee
where Age < (select max(Age) from Employee)
Order by Age desc
~~~

**More examples of syntaxes**

~~~ SQL


--- Analysis

select * from salary 

--- Get Top 3 highest paid employee

select top 3 * from (
	select staffid, firstname, lastname, salary
		from salary) as Sal
order by salary desc

select top 3 * from salary 
order by salary desc

-----Get second highest paid employee----

select max(salary) as secondhighestsalary
from salary
where salary < (select max(salary) from salary)

select top 1 staffid, firstname, lastname

---OR----

select top 3 staffid, firstname, lastname, salary
from salary
order by salary desc

---Lowest--

select top 3 staffid, firstname, lastname, salary
from salary
order by salary asc

----Average salary by department

select department, avg(salary) as AvgSalary
	from (
		select department, salary
			from salary) as Deptsalary
group by department
order by department

---OR----

select department, avg(salary) as AvgSalary
from salary
group by department

~~~

**View in SQL**

* An SQL View is a virtual table that is created based on the result set of a SQL query. Unlike a regular table, a view does not store data itself; instead, it dynamically retrieves data from one or more underlying tables whenever the view is queried.
  
* A view behaves like a table in SQL, allowing you to select, update, insert, and delete data (with some
limitations).

* The data in a view is not stored physically; it is generated dynamically when the view is accessed.

* A view is defined using a SELECT statement that can join multiple tables, filter rows, and select specific columns.

_**Security**_

* Views can be used to restrict access to certain data in a table by exposing only specific columns or rows to the user.

* For example, you can create a view that only shows certain fields of a sensitive table, hiding the rest from the user.

_**Simplicity**_

* Views simplify complex queries. Instead of writing a complex query repeatedly, you can create a view and use it as a simple table.

* This is particularly useful in applications where complex logic needs to be reused.

**Example**

~~~ SQL

-----sql view----

create view vw_emplysala_tbl
as
Select employee.staffid,
       employee.FirstName,
	   employee.gender,
	   employee.hiredate,
	   salary.salary_id,
	   salary.department,
	   salary.salary
from employee
join salary
on salary.Staffid = employee.staffid

select * from vw_emplysala_tbl

~~~

**Lessons on Union and Union all**

**Union** will remove duplicates from the two or more tables _while_ **Union all** will not

**Example**

~~~ SQL

-----Union lesson----

select * from [DSA Mall Ikeja]
union
select * from [DSA Mall Lekki]
union
select * from [DSA Mall Marina]

----Union All lesson-----

select * from [DSA Mall Ikeja]
union all
select * from [DSA Mall Lekki]
union all
select * from [DSA Mall Marina]

~~~

~~~ SQL

Create view vw_DSA_Mall_Transaction as
select
	'DSA MALL IKEJA' as Branch, customerid as [Customer Id],
	firstname as [First Name], lastname as [Last Name],
	Customer_gender as [Gender], TransactionDate as [Date],
	[Address], Transaction_Amount as [Transaction Amount]
from [DSA Mall Ikeja]
union
select
	'DSA MALL LEKKI' as Branch, customerid as [Customer Id],
	firstname as [First Name], lastname as [Last Name],
	Customer_gender as [Gender], TransactionDate as [Date],
	[Address], Transaction_Amount as [Transaction Amount]
from [DSA Mall Lekki]
union
select
	'DSA MALL MARINA' as Branch, customerid as [Customer Id],
	firstname as [First Name], lastname as [Last Name],
	Customer_gender as [Gender], TransactionDate as [Date],
	[Address], Transaction_Amount as [Transaction Amount]
from [DSA Mall Marina]

select * from vw_DSA_Mall_Transaction

~~~

**Result**

<img width="500" alt="image" src="https://github.com/user-attachments/assets/f032d008-f272-4396-8903-31ffc0632b7a" />
