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
| 12    | [What are the categories of SQL Commonds](#What-are-the-categories-of-SQL-Commonds)                                                                             |
| 13    | [What is candidate key](#What-is-candidate-key)                                                                                                                 |
| 14    | [What is primary key](#What-is-primary-key)                                                                                                                     |
| 15    | [What is foreign key](#What-is-foreign-key)                                                                                                                     |
| 16    | [What is super key](#What-is-super-key)                                                                                                                         |
| 17    | [What is combination key](#What-is-combination-key)                                                                                                             |
| 18    | [what is SQL trigger](#what-is-SQL-trigger)                                                                                                                     |
| 19    | [what is Normalisation](#what-is-Normalisation)                                                                                                                 |
| 20    | [what is ACID properties](#what-is-ACID-properties)                                                                                                             |


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

**[⬆ Back to Top](#table-of-contents)**

### <h2>What are the categories of SQL Commonds</h2>

In SQL, commands are divided into various categories based on their functionality. These categories include DDL, DML, DCL, and TCL. Here's an overview of each category along with examples of the commands within them:

| DDL (Data Definition Language)     | Used to create database schema and and to define the type & structure of that data that will store in a database, ex - CREATE, ALTER, DROP, TRUNCATE, RENAME |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| DML (Data Manipulation Language)   | Used for inserting,updating and deleting data in a database, ex - SELECT, INSERT, UPDATE, DELETE.                                                            |
| DCL (Data Control Language)        | Used to control the database transection, ex - GRANT, REVOKE.                                                                                                |
| TCL (Transection Control Language) | Used to manage transection in database, ex - COMMIT, ROLLBACK, SAVEPOINT, SET TRANSACTION.                                                                   |

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is candidate key</h2>

Uniquily Identify each record in a table.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is primary key</h2>

- Primary key is uniquily identify each record in a table and it cannot be null.
- One table contains only one primary key.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is foreign key</h2>

- It is used to link two tables together and maintained the referencial integrity.
- It is key that references the primary key of referenced table.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is super key</h2>

It is combination of all possible attributes that can uniquily identify each record in a table.

**[⬆ Back to Top](#table-of-contents)**

### <h2>What is combination key</h2>

Combination of two or more columns that can uniquily identify each record in a table.

**[⬆ Back to Top](#table-of-contents)**

### <h2>what is SQL trigger</h2>

A SQL trigger is a special kind of stored procedure that automatically executes or fires when certain events occur in a database table, such as insertions, updates, or deletions.

**Key Points:**

- `Automatic Execution:` Triggers are invoked automatically in response to certain events.
- `Associated with Tables:` Typically linked to a specific table.
- `Event-Driven:` Can be set to trigger before or after an INSERT, UPDATE, or DELETE operation.

```sql
CREATE TRIGGER LogInsert
AFTER INSERT ON Students
FOR EACH ROW
BEGIN
    INSERT INTO Students_Log (StudentID, Action)
    VALUES (NEW.StudentID, 'INSERT');
END;
```

**[⬆ Back to Top](#table-of-contents)**

### <h2>what is Normalisation</h2>

Normalization is the process of organizing data in a database to reduce redundancy and improve data integrity by dividing large tables into smaller, related tables.

**Key Objectives of Normalization:**

1. `Eliminate Redundant Data`: Reduce duplicate data by ensuring each piece of data is stored only once.
2. `Ensure Data Dependencies`: Store related data in separate tables to ensure data dependencies are logical and clear.
3. `Improve Data Integrity`: Maintain accuracy and consistency of data through proper structuring.

**Normal Forms**

| 1 NF | Table should not contained any multivalued attribute in the table                                                                                                                                                         |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2 NF | There should be no partial dependency in the table. <br> All non prime attribute should be fully functional dependent on the ck. <br> Condition for partial dependency <br> LHS = Proper subset of CK AND RHS = be a NPA. |
| 3 NF | There should be no transitive dependency in the table. <br> LHS = CK or SK OR RHS = PA.                                                                                                                                   |
| BCNF | LHS of each FD should be CK or SK.                                                                                                                                                                                        |

### <h2>what is ACID properties</h2>

1. **Atomicity**: Either all transections execute or None.
2. **Consistency**: Before transection starts and after transection completed the sum of money should be same.
3. **Isolation**: A transection must not effect other transections that are running parallel to it.
4. **Durability**: After transection completed changes should be change permanently.







