
# POSTGRE SQL


## *Create table* ##

    CREATE TABLE DAY1
    (

    'ID' INT8 UNIQUE PRIMARY KEY,
    'SERIAL_NO' INT8 AUTO INCREMENT,
    'EMAIL' VARCHAR(50) NOT NULL,
    'CITY' char(8)
    )


## *Insert into table* ##

    INSERT INTO DAY1
    (ID,SERIAL_NO,EMAIL,CITY)
    values
    (1, ,prerna@gmail.com,Nagda),
    (2, ,palu@gmail.com,Ujjain)


## *Update table* ##

    update day1
    set city='Vadodara'
    where id=2;

## *Delete from table* ##

    Delete FROM day1
    where id=2;

## *Alter table -> ADD column,DROP column, Change datatype of column* ##

## *Alter to ADD column* ##

    ALTER TABLE DAY1
    ADD COLUMN phone_no VARCHAR(20);

## *Alter to DROP column* ##

    ALTER TABLE DAY1
    DROP COLUMN phone_no;

## *Alter to change datatype of column* ##

    ALTER TABLE DAY1
    ALTER COLUMN city SET DATA TYPE VARCHAR(20);

## *TRUNCATE table-> Delete data of table* ##

    TRUNCATE TABLE DAY1;

## *DROP table-> Delete the table* ##

    DROP TABLE DAY1;

## *Select ALL* ##

    SELECT * FROM DAY1;

## *Select specific column* ##

    SELECT NAME FROM DAY1;

## *Select UNIQUE values* ##

    SELECT DISTINCT NAME FROM DAY1;

## *Select multiple columns* ##

    SELECT NAME ,CITY,ID FROM DAY1;

## *Where Clause->Used for filtering* ##

    SELECT NAME FROM DAY1
    WHERE ID=1;

## *Orderby->Used for ordering* ##

    SELECT NAME FROM DAY1
    ORDER BY ID ASC;

## *Limit->Used for selecting n number of columns* ##

    SELECT NAME FROM DAY1
    LIMIT 1;

## *Importing data fro csv file* ##

### *1)Create table with column names of CSV file* ###

    create table tabl1
    (
	customer_id int8 Primary key,
	first_name varchar(50),
	last_name varchar(50),
	email varchar(100),
	address_id int8
    );

### *2)Import table from CSV file* ###

    COPY tabl1(customer_id,first_name,last_name,email,address_id)
    from 'D:\customer.csv'
    DELIMITER ','
    CSV HEADER;










