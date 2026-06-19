#DDL
     
create database EMP_MANAGEMENT;
use emp_management;
create table EMP_SYSTEM(
emp_id int primary key auto_increment,
emp_name varchar(20) not null,
emp_add varchar(50) not null,
emp_salary decimal(8,2)not null
 );
 
 
use EMP_MANAGEMENT;
alter table  EMP_SYSTEM add emp_dept varchar(50);
select * from  EMP_SYSTEM;
alter table EMP_SYSTEM add emp_mob int;
alter table EMP_SYSTEM drop emp_mob;
select * from  EMP_SYSTEM;
rename table  EMP_SYSTEM to COMPANY_MANAGEMENT;
select* from COMPANY_MANAGEMENT;


#DML
create table EMPLOYEES(
EMP_ID int primary key auto_increment,
EMP_NAME varchar(20),
EMP_ADD varchar(50),
EMP_SALARY decimal(8,2),
EMP_DEPT varchar(50)
);

insert into EMPLOYEES value
(101,'Sanjana','Delhi',90000,'DATA ANALYST'),
(102,'Mohan','Chennai',95000,'DATA SCIENCE'),
(103,'Shanmugham','Bangalore',70000,'DATA ANALYST'),
(104,'Ashika','Kerala',55000,'HR'),
(105,'Rohan','Chennai',85000,'DATA SCIENCE'),
(106,'Chetna','Noida',75000,'HR');

SET SQL_SAFE_UPDATES =0;
update EMPLOYEES set EMP_NAME ='Charu' where EMP_NAME = 'Ashika';
delete from EMPLOYEES where EMP_ID= 106;
insert into EMPLOYEES value(106,'Chetna','Noida',78000,'HR');
select * from EMPLOYEES;


 # (AGGREAGET FUNCTIONS) COUNT, MIN, MAX, SUM, AVG
 select count(EMP_SALARY)from EMPLOYEES;
 select min(EMP_SALARY) from EMPLOYEES;
 select max(EMP_SALARY) from EMPLOYEES;
 select sum(EMP_SALARY) from EMPLOYEES;
 select avg(EMP_SALARY) from EMPLOYEES;

#JOIN 
#TYPES OF JOINS 
#JOIN / INNER JOIN
#LEFT JOIN 
#RIGHT JOIN

use  EMP_MANAGEMENT;
create table CUSTOMERS(
cus_id int primary key auto_increment,
cus_name varchar(50)not null,
cus_mail varchar(50)not null,
cus_add varchar(50) not null
);

insert into CUSTOMERS values
(101,'sanjana','sgmail.com','delhi'),
(102,'shanmugham','shgmail.com','noida'),
(103,'mohan','mgmail.com','chennai'),
(104,'chetna','cgmail.com','delhi'),
(105,'perumal','pgmail.com','kerala'),
(106,'nato','ngmail.com','noida');
select * from CUSTOMERS;

create table PRODUCT(
pro_id int primary key auto_increment,
pro_name varchar(50) not null,
pro_price decimal(8,2) not null,
pro_desc varchar(50) not null
);

insert into PRODUCT values
(201,'HARD DISK',7685,'gold hard disk'),
(202,'MOUSE',85676,'small mouse'),
(203,'SSD',74567,'use ssd'),
(204,'CABINET',65487,'use cabinet'),
(205,'CPU',56476,'use cpu'),
(206,'LAPTOP',89767,'use laptop');
select * from PRODUCT;

create table ORDERS(
o_id int primary key auto_increment,
c_id int not null,
pro_id int not null,
qty int default 1
);

insert into ORDERS (c_id,pro_id,qty)values
(101,203,6),
(102,202,8),
(103,205,3),
(104,204,4),
(105,201,10),
(106,206,5);
select * from ORDERS;


#JOIN/INNER JOIN (SHOW COMMEN VALUE)

select* from CUSTOMERS
join ORDERS
on CUSTOMERS.cus_id = orders.c_id ;

select * from customers
join ORDERS
on CUSTOMERS.cus_id = orders.c_id
join product
on orders.pro_id = product.pro_id;


select customers.cus_id,cus_name,cus_add,product.pro_name,pro_price,qty,pro_price*qty AS AMOUNT ,pro_price*qty*0.18 AS GST from customers
join orders
on customers.cus_id = orders.c_id
join product
on product.pro_id = orders.pro_id;   
 
# RIGHT JOIN
select customers.cus_id,cus_name,cus_add ,qty from customers
right join orders
on customers.cus_id = orders.c_id;

#LEFT JOIN
select customers.cus_id,cus_name,cus_add ,qty from customers
left join orders
on customers.cus_id = orders.c_id;

#UNION      
select customers.cus_id,cus_name,cus_add ,qty from customers
right join orders
on customers.cus_id = orders.c_id
union
select customers.cus_id,cus_name,cus_add ,qty from customers
left join orders
on customers.cus_id = orders.c_id;
     
select customers.cus_id,cus_name,cus_add ,qty from customers
left join orders
on customers.cus_id = orders.c_id;


#ORDER BY 
select * from EMPLOYEES;
select * from EMPLOYEES order by EMP_SALARY asc limit 2;
select * from EMPLOYEES order by EMP_SALARY desc limit 2;
select * from EMPLOYEES order by EMP_NAME asc;

#GROUP BY 
select * from EMPLOYEES;
select EMP_DEPT,count(*) from EMPLOYEES group by EMP_DEPT;
select EMP_DEPT,sum(EMP_SALARY) from EMPLOYEES group by EMP_DEPT;
select * from EMPLOYEES;
select EMP_ADD ,sum(EMP_SALARY) from EMPLOYEES group by EMP_ADD;


#WILECARDS % , _
select * from EMPLOYEES where EMP_ADD like "N%";
select * FROM EMPLOYEES WHERE EMP_ADD LIKE "_E%";


# SUB QUERY
SELECT MAX(EMP_SALARY) FROM EMPLOYEES WHERE EMP_SALARY <(SELECT MAX(EMP_SALARY) FROM EMPLOYEES WHERE EMP_SALARY);
select MIN(EMP_SALARY) FROM EMPLOYEES WHERE EMP_SALARY>(select MIN(EMP_SALARY) FROM EMPLOYEES WHERE EMP_SALARY);
SELECT SUM(EMP_SALARY) FROM EMPLOYEES WHERE EMP_SALARY< (SELECT AVG(EMP_SALARY) FROM EMPLOYEES WHERE EMP_SALARY);

#LIMIT , OFFSET
SELECT * FROM EMPLOYEES ORDER BY EMP_SALARY asc LIMIT 2;

# SCALLER FUNCTION
#LOWER , UPPER,LENGTH/LEN ,SUBSTRING
SELECT LOWER(EMP_NAME) FROM EMPLOYEES;
SELECT UPPER(EMP_NAME) FROM EMPLOYEES;
SELECT length(EMP_NAME)FROM EMPLOYEES;
select substring(EMP_NAME,1,3) FROM EMPLOYEES;


#INDEX
create index index_dept on employees(emp_dept);
select * from employees where emp_dept = 'hr';


# FOREIGN KEY

USE EMP_MANAGEMENT;


CREATE TABLE COURSE(
CO_ID INT PRIMARY KEY auto_increment,
CO_NAME VARCHAR(20) NOT NULL ,
CO_PRICE decimal(8,2) NOT NULL
);

CREATE TABLE STUDENT(
ST_ID INT primary KEY auto_increment,
ST_NAME VARCHAR(50) NOT NULL,
ST_ADD VARCHAR(50)NOT NULL,
CO_ID INT NOT NULL,foreign key(CO_ID) references COURSE(CO_ID)
 ON UPDATE CASCADE ON delete cascade
 );
 
 INSERT INTO COURSE VALUE
 (201,'PYTHON',57683),
 (202,'DATA SCIENCE',256547),
 (203,'DATA ANALYST',54783),
 (204,'JAVA',568707),
 (205,'EXCEL ADVANCED',34567),
 (206,'SQL',674856);
 
 INSERT INTO STUDENT values
 (101,'SANJANA','NOIDA',201),
 (102,'SHANMUGHAM','DELHI',201),
 (103,'MOHAN','KERALA',203),
 (104,'CHETNA','UTTAR PRADESH',202),
 (105,'PRINCE','PUNE',204),
 (106,'ASHIKA','TAMILNADU',204);

 SELECT * FROM STUDENT;


SELECT * FROM STUDENT
JOIN COURSE 
ON STUDENT.CO_ID = COURSE.CO_ID;

UPDATE COURSE SET CO_ID = 201 WHERE CO_ID =1;

# TRIGGERS 
# BEFORE INSERT     # BEFORE DELETE       # BEFORE UPDATE
# AFTER INSERT      # AFTER  DELETE       # AFTER UPDATE

use EMP_MANAGEMENT;
show tables;
select * from EMPLOYEES;  

CREATE TABLE DATA(
ID INT PRIMARY KEY auto_increment,
EMP_ID INT NOT NULL,
EMP_OLD_SALARY DECIMAL(8,2),
EMP_NEW_SALARY DECIMAL(8,2)
);

DELIMITER $$
CREATE TRIGGER EMP_DATA
BEFORE UPDATE ON EMPLOYEES
for each row 
begin
      INSERT INTO DATA (EMP_ID,EMP_OLD_SALARY,EMP_NEW_SALARY) VALUE(OLD.EMP_ID,OLD.EMP_SALARY,NEW.EMP_SALARY);
END $$
DELIMITER ;

UPDATE EMPLOYEES SET EMP_SALARY = 875365 WHERE EMP_ID = 101;
UPDATE EMPLOYEES SET EMP_SALARY = 784445 WHERE EMP_ID =106;
SELECT * FROM DATA;


CREATE TABLE NEW_ENTRY(
ID INT PRIMARY KEY auto_increment,
EMP_ID INT NOT NULL,
EMP_NAME VARCHAR(30),
STATUS VARCHAR(20)
);
 
 DELIMITER $$ 
CREATE TRIGGER NEW_EMP
AFTER INSERT ON EMPLOYEES
FOR EACH ROW
BEGIN 
     INSERT INTO NEW_ENTRY(EMP_ID ,EMP_NAME,STATUS) VALUE(NEW.EMP_ID,NEW.EMP_NAME,'ENTRY');
END $$ 
DELIMITER ;

INSERT INTO EMPLOYEES VALUE(107,'SAKSHI','NOIDA',533567,'HR');
SELECT * FROM EMPLOYEES;
SELECT * FROM NEW_ENTRY;

CREATE TABLE EX_EMP(
ID INT PRIMARY KEY auto_increment,
EMP_ID INT NOT NULL,
EMP_NAME VARCHAR(20),
EMP_DEPT VARCHAR(50)
);

DELIMITER $$
CREATE TRIGGER DELETED
BEFORE DELETE ON EMPLOYEES
FOR EACH ROW
BEGIN 
      INSERT INTO EX_EMP(EMP_ID,EMP_NAME,EMP_DEPT) value(OLD.EMP_ID,OLD.EMP_NAME,OLD.EMP_DEPT);
END $$
DELIMITER ;

DELETE FROM EMPLOYEES WHERE EMP_ID =106;
SELECT * FROM EX_EMP;

### Procedures 
USE EMP_MANAGEMENT;

DELIMITER $$ 
CREATE procedure HISTORY()
begin 
      SELECT * FROM EX_EMP;
END $$
DELIMITER ; 

CALL HISTORY();

SELECT * FROM EMPLOYEES WHERE EMP_DEPT= 'HR';

DELIMITER //
CREATE procedure DEPARTMENT(IN DEPT VARCHAR(50))
BEGIN
      SELECT * FROM EMPLOYEES WHERE EMP_DEPT = DEPT;
END //
DELIMITER ;

CALL DEPARTMENT('DATA SCIENCE');

DROP procedure DEPARTMENT;

# HAVING
use EMP_MANAGEMENT;
SELECT EMP_NAME,SUM(EMP_SALARY) FROM EMPLOYEES
GROUP BY EMP_NAME HAVING SUM(EMP_SALARY) > 10000;









