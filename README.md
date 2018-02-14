# db

__select sum of a column from employee table__  
 ~~~~sql
SELECT SUM(SALARY) FROM EMPLOYEES
~~~~
__NVL ->  replace null values with zero__  
 ~~~~sql
SELECT AVG(NVL(SALARY,0)) avg_salary from EMPLOYEES
~~~~

__Get the number  of rows__
 ~~~~sql
SELECT COUNT(*) FROM EMPLOYEES
~~~~

__Get the number elements in a col__  
 ~~~~sql
SELECT COUNT(COL_name) FROM EMPLOYEES
~~~~

__example for filtering by date__  
 ~~~~sql
SELECT COUNT(*), COUNT(MANAGER_id)
  FROM EMPLOYEES
  WHERE HIRE_DATE > TRUNC(SYSDATE);

SELECT COUNT(*), COUNT(MANAGER_id)
  FROM EMPLOYEES
  WHERE HIRE_DATE > TRUNC(SYSDATE - 12*365); ## this substract days from sysdate
~~~~

__DISTINCT -> Get only the unique value__  
 ~~~~sql
SELECT COUNT (DISTINCT MANAGER_id) NUM_DISTINCT_MANAGERS FROM EMPLOYEES
~~~~
