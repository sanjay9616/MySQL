<h2>1. Write an SQL query to fetch `FIRST_NAME` from worker table using the alias name as <WORKER_NAME>.</h2>

```sql
SELECT first_name AS WORKER_NAME FROM worker;
```

<h2>2. Write an SQL query to fetch `FIRST_NAME` from worker table in upper case.</h2>

```sql
SELECT UPPER(FIRST_NAME) FROM worker;
```

<h2>3. Write an SQL query to fetch unique values of DEPARTMENT from worker table.</h2>

```sql
SELECT distinct(DEPARTMENT) FROM worker;
```

<h2>4. Write an SQL query to print the first three characters of FIRST_NAME from worker table.</h2>

```sql
SELECT SUBSTRING(FIRST_NAME, 1, 3) FROM worker;
```

<h2>5. Write an SQL query to find the position of the alphabet (`b`) in the first name column `Amitabh` from worker table.</h2>

```sql
SELECT INSTR(FIRST_NAME, 'b') FROM worker WHERE FIRST_NAME = 'Amitabh';
```

<h2>6. Write an SQL query to print the FIRST_NAME from worker table after removing white spaces from the right side.</h2>

```sql
SELECT RTRIM(FIRST_NAME) FROM worker;
```

<h2>7. Write an SQL query to print the DEPARTMENT from worker table after removing white spaces from the left side.</h2>

```sql
SELECT LTRIM(DEPARTMENT) FROM wroker;
```

<h2>8. Write an SQL query that fetches the unique values of DEPARTMENT from Worker table and prints its length.</h2>

```sql
SELECT DISTINCT(DEPARTMENT), LENGTH(DEPARTMENT) FROM worker;
```

<h2>9. Write an SQL query to print the FIRST_NAME from Worker table after replacing `a` with `A`.</h2>

```sql
SELECT REPLACE(FIRST_NAME, 'a', 'A') FROM worker;
```

<h2>10. Write an SQL query to print the FIRST_NAME and LAST_NAME from Worker table into a single column COMPLETE_NAME.</h2>

```sql
SELECT CONCAT(FIRST_NAME, " ", LAST_NAME) as COMPLETE_NAME FROM worker;
```

<h2>11. Write an SQL query to print all worker details from the Worker table order by FIRST_NAME Ascending.</h2>

```sql
SELECT * FROM worder ORDER BY FIRST_NAME;
```

<h2>12. Write an SQL query to print all Worker details from the Worker table order by FIRST_NAME Ascending and DEPARTMENT Descending.</h2>

```sql
SELECT * FROM worker ORDER BY FIRST_NAME ASC, DEPARTMENT DESC;
```

<h2>13. Write an SQL query to print details for Workers with the first name as “Vipul” and “Satish” from Worker table.</h2>

```sql
SELECT * FROM worker WHERE FIRST_NAME IN ("Vipul", "Satish");
```

<h2>14. Write an SQL query to print details of workers excluding first names, “Vipul” and “Satish” from Worker table.</h2>

```sql
SELECT * FROM worker WHERE FIRST_NAME NOT IN ("Vipul", "Satish");
```

<h2>15. Write an SQL query to print details of Workers with DEPARTMENT name as “Admin*”.</h2>

```sql
SELECT * FROM worker WHERE DEPARTMENT LIKE 'Admin%';
```

<h2>16. Write an SQL query to print details of the Workers whose FIRST_NAME contains "a".</h2>

```sql
SELECT * FROM worker WHERE FIRST_NAME LIKE '%a%';
```

<h2>17. Write an SQL query to print details of the Workers whose FIRST_NAME ends with "a".</h2>

```sql
SELECT * FROM worker WHERE FIRST_NAME LIKE '%a';
```

<h2>18. Write an SQL query to print details of the Workers whose FIRST_NAME ends with "h" and contains six alphabets.</h2>

```sql
SELECT * FROM worker WHERE FIRST_NAME LIKE '_____h';

-- OR

SELECT * FROM Workers WHERE FIRST_NAME LIKE '%h' AND LENGTH(FIRST_NAME) = 6;
```

<h2>19. Write an SQL query to print details of the Workers whose SALARY lies between 100000 and 500000.</h2>

```sql
SELECT * FROM worker WHERE SALARY BETWEEN 100000 AND 500000;
```

<h2>20. Write an SQL query to print details of the Workers who have joined in Feb'2014.</h2>

```sql
SELECT * FROM worker WHERE YEAR(joining_date) = 2014 AND MONTH(joining_date) = 02;
```

<h2>21. Write an SQL query to fetch the count of employees working in the department "Admin".</h2>

```sql
SELECT DEPARTMENT, COUNT(*) FROM worker WHERE DEPARTMENT = "Admin";
```

<h2>22. Write an SQL query to fetch worker full names with salaries >= 50000 and <= 100000.</h2>

```sql
SELECT concat(FIRST_NAME, ' ', LAST_NAME) FROM worker WHERE salary BETWEEN 50000 and 100000;
```

<h2>23. Write an SQL query to fetch the no. of workers for each department in the descending order.</h2>

```sql
SELECT DEPARTMENT, count(worker_id) AS no_of_worker FROM worker
GROUP BY department
ORDER BY count(*) DESC  ;
```

<h2>24. Write an SQL query to print details of the Workers who are also Managers.</h2>

```sql
SELECT w.* FROM worker as w
INNER JOIN title as t
ON w.worker_id = t.worker_ref_id
WHERE t.worker_title = 'Manager';
```

<h2>25. Write an SQL query to fetch number (more than 1) of same titles in the ORG of different types.</h2>

```sql
SELECT worker_title, count(*) as count FROM title
GROUP BY worker_title HAVING count > 1;
```

<h2>26. Write an SQL query to show only odd rows from a table.</h2>

```sql
SELECT * FROM worker WHERE MOD (WORKER_ID, 2) != 0
-- OR
SELECT * FROM worker WHERE MOD (WORKER_ID, 2) <> 0;
```

<h2>27. Write an SQL query to show only even rows from a table.</h2>

```sql
SELECT * FROM worker WHERE MOD (WORKER_ID, 2) = 0;
```

<h2>28. Write an SQL query to clone a new table from another table.</h2>

```sql
CREATE TABLE worker_clone LIKE worker;
INSERT INTO worker_clone select * FROM worker;
select * FROM worker_clone;
```

<h2>29. Write an SQL query to fetch intersecting records of two tables.</h2>

```sql
SELECT * FROM TableA
INTERSECT
SELECT * FROM TableB;
```
If your database does not support INTERSECT, you can achieve the same result using an INNER JOIN

```sql
SELECT a.* FROM TableA AS a
INNER JOIN TableB AS b
ON a.id = b.id;
```

<h2>30. Write an SQL query to show records from one table that another table does not have.</h2>

```sql
SELECT a.*
FROM TableA AS a
LEFT JOIN TableB AS b ON a.id = b.id
WHERE b.id IS NULL;
```

<h2>31. Write an SQL query to show the current date and time.</h2>

```sql
SELECT NOW(); -- For MySQL
SELECT CURRENT_TIMESTAMP; -- For PostgreSQL
SELECT GETDATE(); -- For SQL Server
SELECT SYSDATE FROM dual; -- For Oracle:
```

<h2>32. Write an SQL query to show the top n (say 5) records of a table order by descending salary.</h2>

```sql
SELECT * FROM worker ORDER BY salary DESC LIMIT 5;
```

<h2>33. Write an SQL query to determine the nth (say n=5) highest salary from a table.</h2>

```sql
SELECT MAX(salary ) FROM Employee e1
WHERE 4 = (SELECT COUNT(DISTINCT(salary)) FROM Employee e2 WHERE e2.salary > e1.salary);
```
OR
```sql
-- It will not work if salary is not distinct
SELECT * from Employee ORDER BY salary DESC LIMIT 4, 1; -- starting from 4th row, return 5th row (from sorted records)
```
OR
```sql
-- It will work if salary in not distinct
SELECT DISTINCT salary FROM Employee ORDER BY DESC LIMIT 4, 1
```

<h2>34. Write an SQL query to determine the nth (say n=5) highest salary from a table.</h2>

```sql
SELECT MAX(salary ) FROM Employee e1
WHERE 4 = (SELECT COUNT(DISTINCT(salary)) FROM Employee e2 WHERE e2.salary > e1.salary);
```

<h2>35. Write an SQL query to fetch the list of employees with the same salary.</h2>

```sql
SELECT w1.* FROM worker w1, worker w2
WHERE w1.salary = w2.salary AND w1.worker_id != w2.worker_id;
```

<h2>36. Write an SQL query to show the second highest salary from a table using sub-query.</h2>

```sql
SELECT MAX(salary) FROM Employee
WHERE salary != (SELECT MAX(salary) FROM Employee);
-- OR
SELECT MAX(salary) FROM Employee
WHERE salary NOT IN (SELECT MAX(salary) FROM Employee);
-- OR
SELECT MAX(salary) FROM Employee
WHERE salary < (SELECT MAX(salary) FROM Employee);
```

<h2>37. Write an SQL query to show one row twice in results from a table.</h2>

```sql
SELECT * FROM worker
UNION ALL
SELECT * FROM worker ORDER BY worker_id;
```

<h2>38. Write an SQL query to list worker_id who does not get bonus.</h2>

```sql
SELECT worker_id FROM worker WHERE worker_id NOT IN (SELECT worker_ref_id FROM bonus);
```

<h2>39. Write an SQL query to fetch the first 50% records from a table.</h2>

```sql
SELECT * FROM worker WHERE worker_id <= (SELECT COUNT(worker_id)/2 FROM worker);
```

<h2>40. Write an SQL query to fetch the departments that have less than 4 people in it.</h2>

```sql
SELECT department, count(department) AS depCount FROM worker
GROUP BY department HAVING depCount < 4;
```

<h2>41. Write an SQL query to show all departments along with the number of people in there.</h2>

```sql
SELECT department, count(department) AS depCount FROM worker
GROUP BY department;
```

<h2>42. Write an SQL query to show the last record from a table.</h2>

```sql
SELECT * FROM worker WHERE worker_id = (SELECT MAX(worker_id) FROM worker);
```

<h2>43. Write an SQL query to show the first record from a table.</h2>

```sql
SELECT * FROM worker WHERE worker_id = (SELECT MIN(worker_id) FROM worker);
```

<h2>44. Write an SQL query to fetch the last five records from a table.</h2>

```sql
SELECT * FROM worker ORDER BY worker_id DESC LIMIT 5;
```

<h2>45. Write an SQL query to print the name of employees having the highest salary in each department.</h2>

```sql
(SELECT MAX(salary) AS maxsal, department FROM worker GROUP BY department) temp
INNER JOIN worker w
ON temp.department = w.department AND temp.maxsal = w.salary;
```

<h2>46. Write an SQL query to fetch three max salaries from a table using co-related subquery</h2>

```sql
SELECT DISTINCT salary FROM worker w1
WHERE 3 >= (SELECT count(DISTINCT salary) FROM worker w2
WHERE w1.salary <= w2.salary) ORDER BY w1.salary DESC;
```

<h2>47. Write an SQL query to fetch three min salaries from a table using co-related subquery.</h2>

```sql
SELECT DISTINCT salary FROM worker w1
WHERE 3 >= (SELECT count(DISTINCT salary) FROM worker w2
WHERE w1.salary >= w2.salary) ORDER BY w1.salary DESC;
```

<h2>48. Write an SQL query to fetch nth max salaries from a table.</h2>

```sql
SELECT DISTINCT salary FROM worker w1
WHERE n >= (SELECT count(DISTINCT salary) FROM worker w2
WHERE w1.salary <= w2.salary) ORDER BY w1.salary desc;
```

<h2>49. Write an SQL query to fetch departments along with the total salaries paid for each of them.</h2>

```sql
SELECT department ,SUM(salary) AS depSal FROM worker
GROUP BY department ORDER BY depSal DESC;
```

<h2>50. Write an SQL query to fetch the names of workers who earn the highest salary.</h2>

```sql
SELECT first_name, salary FROM worker WHERE salary = (SELECT max(Salary) FROM worker);
```












