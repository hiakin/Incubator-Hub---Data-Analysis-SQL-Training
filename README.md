# Incubator-Hub---Data-Analysis-SQL-Training

## Definition

_SQL_ which stands for Structured Query Language, is used for storing and managing data in a relational database management system (RDMS). It enables a user to relate with relational databases and tables using basic languages also known as _syntax_

Some examples of RDMS like _MySQL, PostgreSQL, SQL Server, MSAccess, Oracle_ all use SQL as their standard language 

## Advantages of SQL

  * Easy to understand
  * Can be used to analyze multiple tables at once
  * Can be used to analyze more complex questions than dashboard tools

## SQL Command

They are instruction lines used to communicate with databases. They are used to perform specific task, functions and queries of data

### Types of SQL

  * DDL: Data Definition Language _i.e_ Create, Alter, Drop, Truncate
  * DML: Data Manipulation language _i.e_ Update, Insert, Delete, Merge
  * DCL: Data Control Language _i.e_ Grant, Revoke
  * TCL: Transaction Control Language _i.e_ Commit, Rollback
  * DQL: Data Query Language _i.e_ Select

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

