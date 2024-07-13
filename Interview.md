### Table of Contents

| S No. | Question                                                                                                                                                        |
| ----- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1     | [What is difference between drop truncate and delete](#What-is-difference-between-drop-truncate-and-delete)                                                     |
| 2     | [Find max salary from Employee table](#Find-max-salary-from-Employee-table)                                                                                     |
| 3     | [Find employee name who taking max salary](#Find-employee-name-who-taking-max-salary)                                                                           |
| 4     | [Find min salary from Employee table](#Find-min-salary-from-Employee-table)                                                                                     |
| 5     | [Find employee name who taking min salary](#Find-employee-name-who-taking-min-salary)                                                                           |
| 6     | [Find second highest salary from Employee table](#Find-second-highest-salary-from-Employee-table)                                                               |
| 7     | [Find employee name who taking second highest salary from Employee table](#Find-employee-name-who-taking-second-highest-salary-from-Employee-table)             |
| 8     | [Display all the dept names along with number of Employee working in that](#Display-all-the-dept-names-along-with-number-of-Employee-working-in-that)           |
| 9     | [Display all the dept name where number of Employee are working in less then 2](#Display-all-the-dept-name-where-number-of-Employee-are-working-in-less-then-2) |
| 10    | [Display nth highest salary from Empoyee table](#Display-nth-highest-salary-from-Empoyee-table)                                                                 |
| 11    | [Difference between DBMS and RDBMS](#Difference-between-DBMS-and-RDBMS)                                                                                         |


### <h2>What is difference between drop truncate and delete</h2>

| Features          | DROP                           | TRUNCATE                                                     | DELETE                                    |
| ----------------- | ------------------------------ | ------------------------------------------------------------ | ----------------------------------------- |
| Purpose           | Remove table or database       | Remove all rows from a table                                 | Remove specific rows from a table         |
| Structure Removal | Yes                            | No                                                           | No                                        |
| Rollback          | No                             | No                                                           | Yes (if used in a transaction)            |
| Performance       | Fast (removes whole structure) | Fast (removes all rows without logging individual deletions) | Slower (logs each row deletion)           |
| Syntax            | `DROP TABLE table_name;`       | `TRUNCATE TABLE table_name;` or `TRUNCATE table_name;`       | `DELETE FROM table_name WHERE condition;` |

**[⬆ Back to Top](#table-of-contents)**

### <h2>Find max salary from Employee table</h2>

```sql
SELECT MAX(salary) FROM Employee;
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Find  employee name who taking max salary</h2>

```sql
SELECT name FROM Employee
WHERE salary = (SELECT MAX(salary) FROM Employee);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Find min salary from Employee table</h2>

```sql
SELECT MIN(salary) FROM Employee;
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Find employee name who taking min salary</h2>

```sql
SELECT name FROM Employee
WHERE salary = (SELECT MIN(salary) FROM Employee);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Find second highest salary from Employee table</h2>

```sql
SELECT MAX(salary) FROM Employee
WHERE salary <> (SELECT MAX(salary) FROM Employee);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Find employee name who taking second highest salary from Employee table</h2>

```sql
SELECT name FROM Employee
WHERE salary = (SELECT MAX(salary) FROM Employee WHERE salary <> (SELECT MAX(salary) FROM Employee));
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Display all the dept names along with number of Employee working in that</h2>

```sql
SELECT COUNT(*),dept FROM Employee GROUP BY dept;
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Display all the dept name where number of Employee are working in less then 2</h2>

```sql
SELECT COUNT(*), dept FROM Employee GROUP BY dept HAVING COUNT(*) < 2;
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Display nth highest salary from Empoyee table</h2>

```sql

SELECT MAX(salary ) FROM Employee e1
WHERE n-1 = (SELECT COUNT(DISTINCT(salary)) FROM Employee e2 WHERE e2.salary > e1.salary);
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>Difference between DBMS and RDBMS</h2>

| DBMS                                  | RDBMS                                            |
| ------------------------------------- | ------------------------------------------------ |
| DBMS Applications stores data as file | RDBMS Applications stores data in a tabular form |
| No relationships between data         | Supports relationships using foreign keys        |
| Normalisation is not present in DBMS  | Normalisation is present in RDBMS                |
| Ex-xml                                | Ex-MySQL,Oracle                                  |







