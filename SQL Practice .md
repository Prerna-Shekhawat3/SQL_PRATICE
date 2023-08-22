## *1.)	Write an SQL query to fetch “FIRST_NAME” from the Worker table using the alias name <WORKER_NAME>* ##

    SELECT FIRST_NAME FROM WORKER;

## *2.)	Write an SQL query to fetch “FIRST_NAME” from the Worker table in upper case.* ## 

    SELECT UPPER(FIRST_NAME ) FROM WORKER;

## *3.)	Write an SQL query to fetch unique values of DEPARTMENT from the Worker table.* ## 

    SELECT DISTINCT DEPARTMENT FROM WORKER;

## *4.)	Write an SQL query to print the first three characters of  FIRST_NAME from the Worker table.* ## 
 
    SELECT SUBSTRING(FIRST_NAME,1,3) FROM WORKER;

    SELECT LEFT(FIRST_NAME,3) FROM WORKER;

## *5.)	Write an SQL query to find the position of the alphabet (‘a’) in the first name column ‘Amitabh’ from the Worker table.* ## 

    SELECT INSTR(FIRST_NAME,”A” ) FROM WORKER WHERE               
    FIRST_NAME=’Amitabh’;

    SELECT POSITION(‘A’ IN FIRST_NAME) FROM WORKER WHERE       
    FIRST_NAME=’Amitabh’;

## *6.)	Write an SQL query to print the FIRST_NAME from the Worker table after removing white spaces from the right side.## * 

    SELECT REPLACE(FIRST_NAME,” “,””) FROM WORKER;

    SELECT RTRIM(FIRST_NAME) FROM WORKER;

## *7.)	Write an SQL query to print the DEPARTMENT from the Worker table after removing white spaces from the left side.## * 

    SELECT LTRIM(FIRST_NAME) FROM WORKER;

## *8.)	Write an SQL query that fetches the unique values of DEPARTMENT from the Worker table and prints its length.* ## 

    SELECT DISTINCT DEPARTMENT,LENGTH(DEPARTMENT) FROM WORKER;

## *9.)	Write an SQL query to print the FIRST_NAME from the Worker table after replacing ‘a’ with ‘A’.* ## 

    SELECT REPLACE(FIRST_NAME,’a’,’A’) FROM WORKER;

## *10.)Write an SQL query to print the FIRST_NAME and LAST_NAME from the Worker table into a single column COMPLETE_NAME. A space char should separate them.* ## 

    SELECT CONCAT(FIRST_NAME,+” “+LAST_NAME) AS FULL_NAME FROM WORKER;

## *11.)Write an SQL query to print all Worker details from the Worker table order by FIRST_NAME Ascending.* ## 

    SELECT * FROM WORKER ORDER BY FIRST_NAME ASC;

## *12.)Write an SQL query to print all Worker details from the Worker table order by FIRST_NAME Ascending and DEPARTMENT Descending.* ## 

    SELECT * FROM WORKER ORDER BY FIRST_NAME ASC, DEPARTMENT DESC;

## *13.)Write an SQL query to print details for Workers with the first names “Vipul” and “Satish” from the Worker table.* ## 

    SELECT FIRST_NAME FROM WORKER WHERE FIRST_NAME IN (“VIPUL”,”SATISH”);

## *14.)Write an SQL query to print details of workers excluding first names, “Vipul” and “Satish” from the Worker table.* ## 

    SELECT FIRST_NAME FROM WORKER WHERE FIRST_NAME NOT IN (“VIPUL”,”SATISH”);

## *15.)Write an SQL query to print details of Workers with DEPARTMENT name as “Admin”.* ## 

    SELECT * FROM WORKER WHERE DEPARTMENT='ADMIN';

## *16.)Write an SQL query to print details of the Workers whose FIRST_NAME contains ‘a’.* ##

    SELECT * FROM WORKER WHERE FIRST_NAME LIKE ‘%A%’;
 
## *17.)Write an SQL query to print details of the Workers whose FIRST_NAME ends with ‘a’.* ## 


    SELECT * FROM WORKER WHERE FIRST_NAME LIKE ‘%A’;

## *18.)Write an SQL query to print details of the Workers whose FIRST_NAME ends with ‘h’ and contains six alphabets.* ## 

    SELECT * FROM WORKER WHERE FIRST_NAME LIKE ‘_____H’;S

    SELECT * FROM WORKER WHERE FIRST_NAME=’_____H’ AND LENGTH(FIRST_NAME=6);

## *19.)Write an SQL query to print details of the Workers whose SALARY lies between 100000 and 500000.* ## 

    SELECT * FROM WORKER WHERE SALARY BETWEEN 50000 AND 100000;

## *20.)Write an SQL query to print details of the Workers who joined in Feb’2014.* ##

    SELECT * FROM WORKER WHERE YEAR(JOINING_DATE)=2014 AND MONTH(JOINING_DATE)=2; 

    SELECT * FROM WORKER WHERE JOINING_DATE LIKE ‘2014-02%’;

## *21.)Write an SQL query to fetch the count of employees working in the department ‘Admin’.* ## 

    SELECT COUNT(*) FROM WORKER WHERE DEPARTMENT="ADMIN";

## *22.)Write an SQL query to fetch worker names with salaries >= 50000 and <= 100000.* ## 

    SELECT CONCAT(FIRST_NAME+’ ‘+LAST_NAME) AS FULL_NAME FROM      
    WORKER
    WHERE WORKER_ID IN
    (SELECT WORKER_ID FROM WORKER WHERE SALARY BETWEEN 50000 AND   
    100000);

## *23.)Write an SQL query to fetch the no. of workers for each department in descending order.* ## 

    SELECT DEPARTMENT,COUNT(DEPARTMENT) 'WORKERS_COUNT'
    FROM WORKER
    GROUP BY DEPARTMENT
    ORDER BY WORKERS_COUNT DESC;

## *24.)Write an SQL query to print details of the Workers who are also Managers.* ## 

    SELECT DISTINCT W.FIRST_NAME,T.WORKER_TITLE
    FROM WORKER W
    INNER JOIN TITLE T
    ON W.WORKER_ID=T.WORKER_REF_ID
    AND T.WORKER_TITLE IN (‘MANAGER’);


    SELECT * FROM WORKER 
    WHERE WORKER_ID IN
    (SELECT WORKER_REF_ID FROM TITLE WHERE WORKER_TITLE=’MANAGER’);

## *25.)Write an SQL query to fetch duplicate records having matching data in some fields of a table.* ## 

    SELECT WORKER_TITLE,AFFECTED_FROM,COUNT(*)  
    FROM TITLE
    GROUP BY WORKER_TITLE,AFFECTED_FROM
    HAVING COUNT(*)>1;

## *26.)Write an SQL query to show only odd rows from a table.* ## 

    SELECT * FROM WORKER
    WHERE MOD(WORKER_ID,2) <> 0;

## *27.)Write an SQL query to show only even rows from a table.* ## 

    SELECT * FROM WORKER
    WHERE MOD(WORKER_ID,2) =0;

## *28.)Write an SQL query to clone a new table from another table.* ## 

    CREATE TABLE WORKER2 LIKE WORKER


## *29.)Write an SQL query to fetch intersecting records of two tables.* ## 

    SELECT * FROM TABLE1    
    INTERSECT
    SELECT * FROM TABLE2

## *30.)Write an SQL query to show records from one table that another table does not have.* ## 


    SELECT * FROM TABLE1    
    UNION
    SELECT * FROM TABLE2

## *31.)Write an SQL query to show the current date and time.* ## 

    SELECT now()  "Current Time";

## *32.)Write an SQL query to show the top n (say 10) records of a table.* ## 

    SELECT * FROM WORKER
    LIMIT 10;

## *33.)Write an SQL query to determine the nth (say n=5) highest salary from a table.* ##

    SELECT FIRST_NAME,SALARY FROM WORKER    
    ORDER BY SALARY DESC
    LIMIT 1 OFFSET 2;

## *34.)Write an SQL query to determine the 5th highest salary without using the TOP or limit method.* ##


    SELECT FIRST_NAME,SALARY FROM WORKER W1
    WHERE 1= (SELECT COUNT(DISTINCT SALARY ) FROM WORKER W2
			WHERE W2.SALARY>W1.SALARY)



