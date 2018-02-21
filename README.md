# SQL Cheat sheet

## Labor 1

__select sum of a column from employee table__  
 ~~~~SQL
SELECT SUM(SALARY) FROM EMPLOYEES
~~~~
__NVL ->  replace null values with zero__  
 ~~~~SQL
SELECT AVG(NVL(SALARY,0)) avg_salary from EMPLOYEES
~~~~

__Get the number  of rows__
 ~~~~SQL
SELECT COUNT(*) FROM EMPLOYEES
~~~~

__Get the number elements in a col__  
 ~~~~SQL
SELECT COUNT(COL_name) FROM EMPLOYEES
~~~~

__example for filtering by date__  
 ~~~~SQL
SELECT COUNT(*), COUNT(MANAGER_id)
  FROM EMPLOYEES
  WHERE HIRE_DATE > TRUNC(SYSDATE);

SELECT COUNT(*), COUNT(MANAGER_id)
  FROM EMPLOYEES
  WHERE HIRE_DATE > TRUNC(SYSDATE - 12*365); -- this substract days from sysdate
~~~~

__DISTINCT -> Get only the unique value__  
 ~~~~SQL
SELECT COUNT (DISTINCT MANAGER_id) NUM_DISTINCT_MANAGERS FROM EMPLOYEES
~~~~
__Query min/max values and giving them a name__
~~~~SQL
SELECT 
  MAX(SALARY) as minimum,
  MIN(SALARY) as maximum
FROM EMPLOYEES
~~~~

__Query employee ID-s grouping them and ordering them by department id__
~~~~SQL
SELECT COUNT(EMPLOYEE_ID), DEPARTMENT_ID
 FROM EMPLOYEES
 GROUP BY DEPARTMENT_ID
 ORDER BY DEPARTMENT_ID DESC -- this will be ordered into descending order
 ~~~~
 
 __Group by deparment id, order by hire_id__
 ~~~~SQL
 SELECT COUNT(EMPLOYEE_ID), DEPARTMENT_ID, HIRE_DATE
  FROM EMPLOYEES
  GROUP BY DEPARTMENT_ID, HIRE_DATE 
  -- if we order by a col, it must be included in the group by.
  -- Don't use order by if you don't use the it in the select statement
  ORDER BY HIRE_DATE DESC 
 ~~~~
 __example for filtering group by categories__  
 ~~~SQL
 SELECT COUNT(EMPLOYEE_ID), DEPARTMENT_ID
  FROM EMPLOYEES
  GROUP BY DEPARTMENT_ID
    HAVING COUNT(EMPLOYEE_ID) > 1 
    -- HAVING : add criteria to the group, WHERE: add condition to specific rows
  ORDER BY DEPARTMENT_ID
~~~~
__example for joining tables together and indexing__ 
~~~~SQL
SELECT d.DEPARTMENT_id, d.DEPARTMENT_NAME, AVG(SALARY)
  AS "avG" 
  FROM EMPLOYEES E
  INNER JOIN DEPARTMENTS D
  ON E.DEPARTMENT_ID = D.DEPARTMENT_ID
  GROUP BY D.DEPARTMENT_NAME, D.DEPARTMENT_ID
~~~~

## Labor 2
__inner join example__ 
Without inner join:
 ~~~~SQL
SELECT
  e.employee_id,
  e.last_name,
  d.department_name
FROM
  employees e,
  departments d
WHERE
  e.department_id=d.department_id;
~~~~
With inner join:
 ~~~~SQL
SELECT
  e.employee_id,
  e.last_name,
  d.department_name
FROM
  employees e
INNER JOIN
  departments d
ON
  e.department_id=d.department_id;
~~~~
__a__  
 ~~~~SQL

~~~~
