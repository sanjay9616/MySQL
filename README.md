<h2>What is Database?</h2>

- A database is an organized collection of data, so that it can be easily accessed and managed.
- You can organize data into tables, rows, columns, and index it to make it easier to find relevant information.

<h2>How to create SQL table</h2>

```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
    ...
    ...
    ...
)
```

<h2>3 Types of Category in Datatypes</h2>

1. String
2. Numeric
3. Date and Time

<h3>String data types in MySQL</h3>

1. CHAR(size) 0 to 255
2. VARCHAR(size) 0 to 65535
3. BINARY(size)
4. VARBINARY(size)
5. TINYTEXT 255 characters
6. TEXT(size) 65,535 bytes
7. MEDIUMTEXT 16,777,215 characters
8. LONGTEXT 4,294,967,295 charactes
9. TINYBLOB 255 bytes
10. BLOB(size) 65,535 bytes
11. MEDIUMBLOB 16,777,215 bytes
12. LONGBLOB 4,294,967,295 bytes
13. ENUM(val1, val2, val3, ...) list up to 65535 values
14. SET(val1, val2, val3, ...) list up to 64 values

<h3>Numeric data types in MySQL</h3>

1. BIT(size) 1 to 64
2. TINYINT(size) -128 to 127
3. INT(size) -2147483648 to 2147483647
4. INTEGER(size)
5. SMALLINT(size) -32768 to 32767
6. MEDIUMINT(size) -8388608 to 8388607
7. BIGINT(size) -9223372036854775808 to 9223372036854775807
8. BOOL
9. BOOLEAN 0/1
10. FLOAT(p)
11. DOUBLE(size, d) 255.568
12. DECIMAL(size, d) size = 60, d = 30
13. DEC(size, d)

<h3>Date and Time data types in MySQL</h3>

1. DATE '1000-01-01' to '9999-12-31'
2. DATETIME(fsp) YYYY-MM-DD hh:mm:ss
3. TIMESTAMP(fsp)
4. TIME(fsp) hh:mm:ss
5. YEAR four-digit-format: 1901

<h2>Create Database & Table</h2>

```sql
CREATE DATABASE student;
```
```sql
use student;
CREATE TABLE personal(
    roll_no INT,
    name VARCHAR(50),
    phone_no VARCHAR(12),
    gender VARCHAR(1),
    DOB DATE

);
```
```sql
CREATE TABLE Product(
    Pid INT,
    Pname VARCHAR(50),
    Pcompany VARCHAR(12),
    Price INT
);
```

<h2>How to Insert data in Tables with SQL</h2>

```sql
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...)
```

```sql
use student;
INSERT INTO personal(roll_no,name,DOB,gender,phone_no)
VALUES(4,"Ketan Mehta","2021-09-22","M","7855xxxxxx");

SELECT * FROM student.personal;
```
**Output**

| roll_no. | name        | DOB        | gender | phone_no   |
| -------- | ----------- | ---------- | ------ | ---------- |
| 4        | Ketan Mehta | 2021-09-22 | M      | 7855xxxxxx |

<h2>Insert Multiple Rows Into Table</h2>

```sql
INSERT INTO table_name(columns1, column2, ...)
VALUES
(value1, value2, ...),
(value1, value2, ...),
(value1, value2, ...);
```
```sql
USE student;
INSERT INTO personal(roll_no,name,gender,phone_no,DOB)
VALUES
(1,"Mohit Yadav","M","9000xxxxxx","2010-09-21"),
(2,"Ketan Mehta","M","9600xxxxxx","1998-09-11"),
(3,"Vanshika","F","8800xxxxxx","2000-09-07"),
(4,"Mohini","F","7800xxxxxx","2002-09-09");
```
**Output**

| roll_no. | name        | DOB        | gender | phone_no   |
| -------- | ----------- | ---------- | ------ | ---------- |
| 1        | Mohit Yadav | 2010-09-21 | M      | 9000xxxxxx |
| 2        | Ketan Mehta | 1998-09-11 | M      | 9600xxxxxx |
| 3        | Vanshika    | 2000-09-07 | F      | 8800xxxxxx |
| 4        | Mohini      | 2002-09-09 | F      | 7800xxxxxx |

<h2>Constrains in MySQL</h2>

Constrains in MySQL used to specify the rule that allows what values will be stored in the table

1. NOT NULL
2. UNIQUE
3. DEFAULT
4. CHECK
5. PRIMARY KEY
6. FOREIGN KEY

```sql
USE student;

CREATE TABLE student1(
    id INT NOT NULL UNIQUE,
    name VARCHAR(20) NOT NULL,
    age INT NOT NULL CHECK (age>=18),
    gender VARCHAR(10) NOT NULL,
    phone VARCHAR(12) NOT NULL UNIQUE,
    city VARCHAR(30) NOT NULL DEFAULT 'Agra'
);
```

<h2>SELECT with WHERE Clause</h2>

```sql
SELECT column1, column2, column3, ...
FROM table_name
WHERE condition
```

<h2>WHERE Comparision Operator</h2>

| Operator | Description                                      |
| -------- | ------------------------------------------------ |
| =        | Equal                                            |
| >        | Greater Than                                     |
| <>       | Less Than                                        |
| >=       | Greater Than or Equal                            |
| <=       | Les Than or EQUAL                                |
| <> OR != | Not Equal                                        |
| BETWEEN  | Between a certain range                          |
| LIKE     | Search for a pattern                             |
| IN       | To specify multiple possible values for a column |

**Examples**

```sql
USE student;
SELECT * FROM student.personal;
```
```sql
USE student;
SELECT * FROM personal;
```
```sql
USE student;
SELECT roll_no,name FROM personal;
```
```sql
USE student;
SELECT roll_no AS SN,name AS NAME FROM personal;
```
```sql
USE student;
SELECT roll_no AS SN,name AS "Student Name" FROM personal;
```
```sql
USE student;
SELECT * FROM personal
WHERE
roll_no=3;
```
```sql
USE student;
SELECT roll_no,name FROM personal
WHERE
roll_no=3;
```

<h2>SELECT with AND & OR Operator</h2>

```sql
SELECT column1, column2, column3, ....
FROM table_name
WHERE condition1 AND condition2 AND condition3....;
```
```sql
SELECT column1, column2, column3, ....
FROM table_name
WHERE condition1 OR condition2 OR condition3....;
```
**Example**

```sql
use student;
SELECT * FROM personal
WHERE age>=20 AND age<=25 AND (address="delhi" OR address="Agra");
```
```sql
use student;
SELECT * FROM personal
WHERE age>=20 AND age<=25 AND NOT (address="delhi" OR address="Agra");
```

<h2>SELECT with IN Operator</h2>

```sql
SELECT column1, column2, column3, ....
FROM table_name
WHERE column_name IN (value1, valu2, ...);
```
```sql
SELECT column1, column2, column3, ....
FROM table_name
WHERE column_name NOT IN (value1, valu2, ...);
```
**Example**

```sql
use student;
SELECT * FROM personal
WHERE age IN (20,21,22,23,24,25);
```
```sql
use student;
SELECT * FROM personal
WHERE age NOT IN (20,21,22,23,24,25);
```

<h2>SELECT with BETWEEN Operator</h2>

```sql
SELECT column1, column2, column3, ...
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```
```sql
SELECT column1, column2, column3, ...
FROM table_name
WHERE column_name NOT BETWEEN value1 AND value2;
```
**Example**

```sql
use student;
SELECT * FROM personal
WHERE age BETWEEN 20 AND 25;
```
```sql
use student;
SELECT * FROM personal
WHERE age NOT BETWEEN 20 AND 25;
```
```sql
use student;
SELECT * FROM personal
WHERE name BETWEEN "Ketan" AND "Umang";
-- Search only  between “K” and “U”
```
```sql
use student;
SELECT * FROM personal
WHERE name NOT BETWEEN "Ketan" AND "Umang";
```

<h2>LIKE Operator with Wildcard Patterns</h2>

| Pattern     | Description                                     |
| ----------- | ----------------------------------------------- |
| LIKE 'a%'   | Start with "a"                                  |
| LIKE '%a'   | End with "a"                                    |
| LIKE '%am%' | Have "am" in any position                       |
| LIKE 'a%m'  | Start with "a" and Ends with "m"                |
| LIKE '_a%'  | "a" in the second position                      |
| LIKE '__a%' | "a" in the third position                       |
| LIKE '_oy%' | "o" in the second and "y" in the third position |

**Examles**

```sql
-- patterns are Case sensitive
use student;
SELECT * FROM personal
WHERE name LIKE "s%";
```
```sql
use student;
SELECT * FROM personal
WHERE name LIKE "_h%";
-- Also we can use NOT LIKE
-- If you use BINARY after WHERE and before col_name then upper or lower does not matter
```

<h2>Regular Expressions Patterns with Descriptions</h2>

| Sign                     | Pattern                          | Description                                                  |
| ------------------------ | -------------------------------- | ------------------------------------------------------------ |
| ^                        | '^ra'                            | Beginning of string                                          |
| $                        | '^an$'                           | End of string                                                |
| [...]                    | '[rms]'                          | Any character listed between the square brackets             |
| ^[...]                   | '[^rms]'                         | Begins with any character listed between the square brackets |
| [a-z]                    | '[a-h]e'                         | Match with in the range                                      |
| p1&#124;p2&#124;p3&#124; | 'tom&#124;dick&#124;harry&#124;' | Match any of the patterns p1, p2 or p3                       |

```sql
SELECT column1, column2, column3, ...
FROM table_name
WHERE column_name REGEXP pattern;
```
```sql
-- Search name starting from ‘sh’
USE student;
SELECT * FROM personal WHERE name REGEXP '^sh';
```
```sql
-- Search name which contains ‘sh’
USE student;
SELECT * FROM personal WHERE name REGEXP 'sh';
```
```sql
-- Search name which contains ‘ar’ at the end
USE student;
SELECT * FROM personal WHERE name REGEXP 'ar$';
```
```sql
-- Seacrh name which matches any of ‘Kumar’,’Awasthi’,’Mehta’
USE student;
SELECT * FROM personal WHERE name REGEXP 'Kumar|Awasthi|Mehta';
```
```sql
-- Search name contains ‘Sanjay’ at starts OR ‘Awasthi’ at end OR contain ‘Mehta’
USE student;
SELECT * FROM personal WHERE name REGEXP '^Sanjay|Awasthi$|Mehta';
```
```sql
-- Search name which contains  ‘I’ character OR contains ‘s’ character OR contains ‘is’
USE student;
SELECT * FROM personal WHERE name REGEXP '[is]';
```
```sql
-- Search name which contains ‘iv’ OR ‘sv’
USE student;
SELECT * FROM personal WHERE name REGEXP '[is]v';
```
```sql
-- Search name which starts from ‘m’ OR starts ‘s’
USE student;
SELECT * FROM personal WHERE name REGEXP '^[ms]';
```
```sql
-- Search name which ends with ‘I’ OR ‘r’
USE student;
SELECT * FROM personal WHERE name REGEXP '[ir]$';
```
```sql
-- Search name which contains in range ‘a’ to ‘j’ and suffix ‘r’
USE student;
SELECT * FROM personal WHERE name REGEXP '[a-j]r';
```

<h2>SELECT with ORDER BY</h2>

```sql
SELECT column1, column2, column3, ...
FROM table_name
ORDER BY column1, column2, ... ASC | DESC
```
**Example**

```sql
USE student;
SELECT * FROM personal ORDER BY name ASC;
```
```sql
USE student;
SELECT * FROM personal ORDER BY name DESC;
```
```sql
USE student;
SELECT * FROM personal WHERE gender="M" ORDER BY name DESC;
```
```sql
-- Sort name in ascending order
USE student;
SELECT * FROM personal ORDER BY name;
```
```sql
-- Sort by name if name same then it compare to age and sorts by age
USE student;
SELECT * FROM personal ORDER BY name, age;
```

<h2>SELECT Data with DISTINCT</h2>

```sql
SELECT DISTINCT column1, column2, ...
FROM table_name;
```
**Example**

```sql
USE student;
SELECT DISTINCT age FROM personal;
```
```sql
USE student;
SELECT DISTINCT name,age FROM personal;
```
```sql
USE student;
SELECT DISTINCT age FROM personal ORDER BY age;
```

<h2>SELECT Data with IS NULL</h2>

```sql
SELECT column1, column2, column3, ...
FROM table_name
WHERE column IS NULL;
```
```sql
SELECT column1, column2, column3, ...
FROM table_name
WHERE column IS NOT NULL;
```
**Example**

```sql
USE student;
SELECT * FROM personal WHERE gender IS NULL;
```
```sql
USE student;
SELECT * FROM personal WHERE gender IS NOT NULL;
```

<h2>SELECT Data with LIMIT</h2>

```sql
SELECT column1, column2, column3, ...
FROM table table_name
WHERE condition
LIMIT number;
```
**Example**

```sql
USE student;
SELECT * FROM personal LIMIT 3;
```
```sql
USE student;
SELECT * FROM personal
WHERE gender="M" ORDER BY name LIMIT 3;
```

<h2>SELECT Data with LIMIT & OFFSET</h2>

```sql
SELECT column1, column2, column3, ...
FROM table_name
WHERE condition
LIMIT offset, number;
```
**Example**

```sql
-- Starts from 3rd Row and return 4th 5th 6th
USE student;
SELECT * FROM personal LIMIT 3, 3;
```

<h2>Aggregate Functions</h2>

Perform calculations on multiple values and return the result in a single value like the average of all values.

```sql
COUNT(column_name)
MAX(column_name)
MIN(column_name)
SUM(column_name)
AVG(column_name)
```
```sql
SELECT COUNT(column_name)
FROM table_name
WHERE condition;
```
```sql
SELECT SUM(column_name)
FROM table_name
WHERE condition;
```
```sql
USE student;

CREATE TABLE Employee(
    id INT NOT NULL UNIQUE,
    name VARCHAR(30),
    age INT,
    gender VARCHAR(1),
    salary INT
);

INSERT INTO Employee(id,name,gender,age,salary)
VALUES
(1,"Sanjay Kumar","M",23,110000),
(2,"Shivani Awasthi","F",20,100000),
(3,"Shivank Varshney","M",22,90000),
(4,"Mohit Yadav","M",21,95000),
(5,"Ketan Mehta","M",24,95000),
(6,"Priya Yadav","F",20,97000),
(7,"Rekha Mehta","F",20,50000),
(8,"Aliya Gupta","F",21,80000);
```
```sql
USE student;

SELECT COUNT(id) FROM Employee; --Output: 8 (Total nimber of record)

SELECT COUNT(*) FROM Employee; --Output: 8 (Total nimber of record)

SELECT COUNT(salary) FROM Employee; --Output: 8

SELECT COUNT(DISTINCT salary) FROM Employee; --Output: 7

SELECT SUM(salary) FROM Employee; --Output: 717000

SELECT SUM(DISTINCT salary) FROM Employee; --Output: 622000

SELECT MAX(salary) FROM Employee; --Output: 110000

SELECT MIN(salary) FROM Employee; --Output: 50000

SELECT AVG(salary) FROM Employee; --Output: 89625.0

SELECT AVG(DISTINCT salary) FROM Employee; --Output: 88857.1429

SELECT COUNT(id) AS TotalRecords FROM Employee;
```

<h2>How to Update data in Tables</h2>

```sql
UPDATE table_name
SET column_name1 = value1, column_name2 = value2, ...
WHERE condition
```
**Example**

```sql
USE student;
UPDATE Employee
SET name="Anu Chaudhary" WHERE id=7;
```
```sql
USE student;
UPDATE Employee
SET age=20,salary=45000 WHERE id=7;
```
```sql
USE student;
UPDATE Employee
SET age=18 WHERE id IN (2,3);
```

<h2>How to DELETE data in Tables</h2>

```sql
DELETE FROM table_name
WHERE condition;
```
**Example**

```sql
USE student;
DELETE FROM Employee WHERE id=8;
```

<h2>How to Rollback your work in MySQL</h2>

**ROLLBACK**:- Cancels all modifications, which modified after COMMIT operation, it only modifies `Insert`, `Update` and `Delete` operation (which modifies after COMMIT).

**COMMIT**:- Save previous transection permanently

```sql
use student;
UPDATE Employee SET name="Shivani" WHERE id=2; -- -- It will not be ROLLBACK
COMMIT;
UPDATE Employee SET name="Sonal" WHERE id=2; -- It will be ROLLBACK
ROLLBACK;
SELECT * FROM Employee;
```

<h2>What is PRIMARY KEY Constrains</h2>

`Primary key is key which is uniquely identify each records in a table, and it cannot have null value`

- Primary Key always has unique data.
- A Primary Key cannot have null value.
- A Table contain only one Primary Key constrains.

<h2>Create table with PRIMARY KEY Syntax</h2>

```sql
CREATE TABLE table_name (
    id INT NOT NULL AUTO_INCREMENT,
    name VARCHAR(50) NOT NULL,
    age INT NOT NULL,
    city VARCHAR(10) NOT NULL,
    PRIMARY KEY(id),
    FOREIGN KEY(city) REFERENCES City (cid)
);
```

<h2>ALTER Table with FOREIGN KEY Syntax</h2>

```sql
ALTER TABLE table_name
ADD FOREIGN KEY (city) REFERENCES City (cid);
```

**Examples**

```sql
USE student;
CREATE TABLE City(
    cid INT NOT NULL AUTO_INCREMENT,
    cname VARCHAR(20) NOT NULL,
    PRIMARY KEY (cid)
);
```
```sql
USE student;
INSERT INTO City(cname)
VALUES
('Agra'),
('Bhopal'),
('Noida'),
('Delhi'),
('Jaipur');
```

```sql
USE student;
CREATE TABLE Personal(
    id INT NOT NULL,
    name VARCHAR(50) NOT NULL,
    percentage INT NOT NULL,
    age INT NOT NULL,
    gender VARCHAR(1) NOT NULL,
    city INT NOT NULL,
    PRIMARY KEY (id),
    FOREIGN KEY (city) REFERENCES City (cid)
);
```
```sql
USE student;
INSERT INTO Personal(id,name,percentage,age,gender,city)
VALUES
(1,"Ram Kumar",45,19,"M",1),
(2,"Sarita Kumari",55,22,"F",2),
(3,"Salman Khan",62,20,"M",1),
(4,"Juhi Chawla",47,18,"F",3),
(5,"Anil Kapoor",74,22,"M",1),
(6,"John Abraham",64,21,"M",2),
(7,"Shahid Kapoor",52,20,"M",1);
```

<h2>Types of Joins in MySQL</h2>

1. INNER JOIN
2. LEFT JOIN
3. RIGHT JOIN
4. CROSS JOIN

<h2>What is INNER JOIN</h2>

- The INNER JOIN selects records that have matching values in both tables.
- **Note**: We can simply write JOIN

```sql
SELECT columns
FROM Table1
INNER JOIN table2
ON table1.column_name(foreign_key) = table2.column_name(primary_key)
```
```sql
USE student;
SELECT * FROM Personal INNER JOIN city
ON personal.city=city.cid;

-- OR

USE student;
SELECT * FROM Personal p INNER JOIN city c
ON p.city=c.cid;

USE student;
SELECT p.id,p.name,p.percentage,p.age,p.gender,c.cname FROM Personal p INNER JOIN city c
ON p.city=c.cid;
```

<h2>What is LEFT JOIN</h2>

- The LEFT JOIN returns all records from the left table (table1), and the matched records from the right table (table2)

![1](https://github.com/sanjay9616/MySQL/assets/87460579/b3efd5da-25d2-46a6-afd3-bfea1251aad9)

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column_name(foreign_key) = table2.column_name2(primary_key)
```
```sql
SELECT * FROM personal
LEFT JOIN city
ON personal.city=city.cid;
```

<h2>What is RIGHT JOIN</h2>

![2](https://github.com/sanjay9616/MySQL/assets/87460579/787d2e62-34ec-4310-866b-d8c1dfc5a061)

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column_name(foreign_key) = table2.column_name2(primary_key)
```
```sql
SELECT * FROM personal RIGHT JOIN city ON
personal.city=city.cid;
```

<h2>What is CROSS JOIN</h2>

![3](https://github.com/sanjay9616/MySQL/assets/87460579/7807432b-24fa-4ea1-bf30-207adb352f68)
![4](https://github.com/sanjay9616/MySQL/assets/87460579/64caeec3-5a0d-4768-ae66-dc5696cbaa17)

```sql
SELECT columns
FROM table1
CROSS JOIN table2
```
```sql
USE student;
SELECT * FROM Employee CROSS JOIN City;
```

**Example**

```sql
CREATE DATABASE Schema1;

USE Schema1;
CREATE TABLE City(
    cid INT NOT NULL AUTO_INCREMENT,
    city VARCHAR(20),
    PRIMARY KEY (cid)
);
INSERT INTO City(city)
VALUES
("Agra"),
("Bhopal"),
("Delhi"),
("Noida");

USE Schema1;
CREATE TABLE Courses(
    crid INT NOT NULL AUTO_INCREMENT,
    course VARCHAR(20),
    PRIMARY KEY (crid)
);
INSERT INTO Courses(course)
VALUES
("Btech"),
("BCA"),
("BBA");

USE Schema1;
CREATE TABLE Student(
    id INT NOT NULL AUTO_INCREMENT,
    name VARCHAR(20),
    age INT,
    course INT,
    city INT,
    PRIMARY KEY (id),
    FOREIGN KEY (course) REFERENCES Courses (crid),
    FOREIGN KEY (city) REFERENCES City(cid)
);
INSERT INTO Student(name,age,course,city)
VALUES
("Ram Kumar",19,1,1),
("Salman Khan",18,3,2),
("Meera Khan",19,1,1),
("Sarita kumari",21,2,3);
```

<h2>JOIN Three Tables</h2>

```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column_name = table2.column_name
INNER JOIN table3
ON table1.column_name = table_name3.column_name
```
```sql
USE Schema1;
SELECT * FROM Student
INNER JOIN City
ON Student.city=City.cid
INNER JOIN Courses
ON Student.course=Courses.crid;

-- OR

Or

USE Schema1;
SELECT * FROM Student s
INNER JOIN City c
ON s.city=c.cid
INNER JOIN Courses cr
ON s.course=cr.crid;
```

```sql
USE Schema1;
SELECT s.id,s.name,s.age,c.city,cr.course FROM Student s
INNER JOIN City c
ON s.course=c.cid
INNER JOIN Courses cr
on s.city=cr.crid;
```

<h2>GROUP BY Clause</h2>

The GROUP BY Clause is used in conjunction with the SELECT Statment and Aggregate functions to group rows togather common column values.

```sql
SELECT columns
FROM table_name
WHERE condition
GROUP BY column_name(s)
```
```sql
SELECT columnc
FROM table1 INNER JOIN table2
ON table1.column_name = table2.column_name
WHERE condition
GROUP BY column_name(s);
```
**Examples**

`Student Table`

| id  | name          | age | course | city |
| --- | ------------- | --- | ------ | ---- |
| 1   | Ram Kumar     | 19  | 1      | 1    |
| 2   | Salman Khan   | 18  | 3      | 2    |
| 3   | Meera Khan    | 19  | 1      | 1    |
| 4   | Sarita Kumari | 21  | 2      | 3    |

```sql
USE Schema1;
SELECT city, COUNT(city)
FROM Student
GROUP BY city;
```
`Output`

| city | COUNT(city) |
| ---- | ----------- |
| 1    | 2           |
| 2    | 1           |
| 3    | 1           |

`city Table`

| cid | city   |
| --- | ------ |
| 1   | Agra   |
| 2   | Bhopal |
| 3   | Delhi  |

```sql
USE Schema1;
SELECT c.city, COUNT(s.city) FROM Student s
INNER JOIN City c
ON s.city=c.cid
GROUP BY city;
```
`Output`

| city   | COUNT(s.city) |
| ------ | ------------- |
| Agra   | 2             |
| Bhopal | 1             |
| Delhi  | 1             |

<h2>GROUP BY with HAVING Clause</h2>

```sql
SELECT columns
FROM table_name
GROUP BY column_name(s)
HAVING condition;
```

If we use WHERE then use it before GROUP BY else if use HAVING then use it after GROUP BY

<h2>What is SubQuery or Nested Query</h2>

```sql
SELECT columns
FROM table1
WHERE
column = (SELECT columns FROM table2 WHERE condition);
```

```sql
USE Schema1;
SELECT name FROM Student s
WHERE s.course = (SELECT cr.crid FROM Courses cr WHERE cr.course = "Btech");
```
```sql
USE Schema1;
SELECT s.name FROM Student s
WHERE s.course IN (SELECT cr.crid FROM Courses cr WHERE cr.course IN ("Btech","BBA"));
```

<h2>SELECT with EXISTS / NOT EXISTS Sytax</h2>

If any single records exists then Parent commond show result.

```sql
SELECT columns
FROM table1
WHERE
EXISTS (SELECT columns FROM table2 WHERE Condition);
```
```sql
SELECT columns
FROM table1
WHERE
NOT EXISTS (SELECT columns FROM table2 WHERE Condition);
```

<h2>What is UNION & UNION ALL</h2>

```sql
SELECT column1, column2 FROM table1
UNION / UNION ALL
SELECT coumn1, column2 FROM table2
```

- **UNION** - Removes duplicate rows from the combined result set, but **UNION ALL** does not removes duplicate rows from the combined result set
- Each SELECT Statement within UNION must have the same number of columns
- The columns must also have similar data types
- The columns in each SELECT statetment must also be in same order

```sql
USE schema1;
CREATE TABLE Lecturers(
    id INT NOT NULL AUTO_INCREMENT,
    name VARCHAR(20),
    age INT,
    city INT,
    course INT,
    PRIMARY KEY (id),
    FOREIGN KEY (course) REFERENCES Courses (crid),
    FOREIGN KEY (city) REFERENCES City(cid)
);
INSERT INTO Lecturers(name,age,city,course)
VALUES("Raj Kapoor",37,1,2),
("Raj Kapoor",39,2,3),
("Sadhna",38,4,1),
("Ram Kumar",45,3,2),
("Nagma",42,2,1);
SELECT * FROM Lecturers;
```
| id  | name       | age | city | course |
| --- | ---------- | --- | ---- | ------ |
| 1   | Raj Kapoor | 37  | 1    | 2      |
| 2   | Raj Kapoor | 39  | 2    | 3      |
| 3   | Sadhna     | 38  | 4    | 1      |
| 4   | Ram Kumar  | 45  | 3    | 2      |
| 5   | Nagma      | 45  | 2    | 1      |

```sql
USE Schema1;
SELECT * FROM Student
UNION
SELECT * FROM Lecturers;
```
```sql
USE Schema1;
SELECT name FROM Student
UNION
SELECT name FROM Lecturers;
```
| name          |
| ------------- |
| Ram Kumar     |
| Salman Khan   |
| Meera Khan    |
| Sarita Kumari |
| Raj Kapoor    |
| Sadhna        |
| Nagma         |

```sql
USE Schema1;
SELECT name FROM Student
UNION ALL
SELECT name FROM Lecturers;
```
| name          |
| ------------- |
| Ram Kumar     |
| Salman Khan   |
| Meera Khan    |
| Sarita Kumari |
| Raj Kapoor    |
| Raj Kapoor    |
| Sadhna        |
| Ram Kumar     |
| Nagma         |

In the above example Ram Kumar & Raj Kapoor have duplicacy(UNION ALL)

<h2>What is If Clause</h2>

```sql
USE Schema1;
SELECT *, IF(percentage >=33,"PASS","FAIL") AS Res
FROM result;
```
| id  | name         | percentage | Res  |
| --- | ------------ | ---------- | ---- |
| 1   | Sanjay Kumar | 98         | PASS |
| 2   | Mohit Yadav  | 80         | PASS |
| 3   | Somil        | 23         | FAIL |
| 4   | Vinay        | 33         | PASS |

<h2>What is Case Clause</h2>

```sql
USE Schema1;
SELECT *,
CASE
    WHEN percentage <=100 AND percentage >80 THEN "1st"
    WHEN percentage <=80 AND percentage >60 THEN "2nd"
    WHEN percentage <=60 AND percentage >40 THEN "3rd"
    WHEN percentage <=40 THEN "FAIL"
    ELSE "Not Correct Data"
END
AS Grade
FROM Result;
```
| id  | name         | percentage | Grade |
| --- | ------------ | ---------- | ----- |
| 1   | Sanjay Kumar | 98         | 1st   |
| 2   | Mohit Yadav  | 80         | 2nd   |
| 3   | Somil        | 23         | FAIL  |
| 4   | Vinay        | 33         | PASS  |

```sql
UPDATE Result SET percentage= 
CASE id 
    WHEN 4 THEN 45 
    WHEN 3 THEN 60 
END WHERE id IN(3,4);
```
![1](https://github.com/user-attachments/assets/47f43dd5-b605-4065-a2aa-fb549e1bc722)
![2](https://github.com/user-attachments/assets/602fb081-5594-4070-8d02-1ed5ff123bb2)

```sql
SELECT 4+3; -- 7
SELECT 4+3 AS Total; -- 7

USE Schema1;
SELECT name,percentage,(5+percentage) FROM Result;

SELECT PI(); -- 3.141593

SELECT ROUND(9.48),ROUND(9.5),ROUND(9.6); -- 9, 10, 10

SELECT ROUND(-9.48),ROUND(-9.5),ROUND(-9.6); -- -9, -10, -10

SELECT CEIL(9.48),CEIL(9.5),CEIL(9.6),CEIL(-9.6),CEIL(-9.6),CEIL(-9.6); -- 10, 10, 10, -9, -9, -9

SELECT FLOOR(9.48),FLOOR(9.5),FLOOR(9.6),FLOOR(-9.6),FLOOR(-9.6),FLOOR(-9.6); --9, 9, 9, -10, -10, -10

SELECT POW(2,3),SQRT(17),SQRT(16); -- 8, 4.12310565617661, 4

SELECT RAND(),RAND()*100,CEIL(7+RAND()*6); --0.34415738316640015, 8.720505711362236, 10

SELECT SIGN(-2),SIGN(0),SIGN(2); -- -1, 0, 1
```
![3](https://github.com/user-attachments/assets/811467ab-0a2e-4a0f-9b17-22612e40701f)

```sql
USE Schema1;
SELECT id, UPPER(name) AS Name, percentage FROM Result;
```
```sql
USE Schema1;
SELECT id, name, LENGTH(name) AS ByteLength, CHAR_LENGTH(name) AS Length FROM Result;

SELECT id,CONCAT(name," - ",percentage,"%") AS Name FROM Result;

SELECT CONCAT_WS(" - ","ABES","ENGINEERING","COLLEGE");

SELECT LTRIM("   Sanjay Kumar          ") AS Name1,RTRIM("        Sanjay Kumar     ") AS Name2,TRIM("     Sanjay Kumar      ") as Name3;
```
- LTRIM:-Remove all left spaces
- RTRIM:-Remove all Right spaces
- TRIM:-Remove left and right spaces

```sql
SELECT POSITION("Kumar" IN "Sanjay Kumar") as Pos1,POSITION("a" IN "Sanjay Kumar") as Pos2;

SELECT INSTR("Sanjay Kumar","KUmar") as Pos1,INSTR("Sanjay Kumar","a") as Pos2;

SELECT LOCATE("Kumar","Sanjay Kumar") as Pos1,LOCATE("a","Sanjay Kumar",3) as Pos2;

SELECT SUBSTRING("Sanjay Kumar",3) AS Name1,SUBSTRING("Sanjay Kumar",3,6) AS Name2,SUBSTRING("Sanjay Kumar",-5,5) AS Nmae3;

-- SUBSTRING(String,Start,Length)  ---SUBSTRING is same as SUBSTR and MID

SELECT SUBSTRING_INDEX("www.yahoobaba.net",".",2);

SELECT LEFT("Sanjay Kumar",5) AS First5,RIGHT("Sanjay Kumar",5) AS Last5;

SELECT RPAD("Sanjay Kumar",20,"*"),LPAD("Sanjay Kumar",20,"-");

SELECT REVERSE("Sanjay Kumar"),REPLACE("Sanjay Kumar","a"," ");

SELECT STRCMP("Sanjay Kumar","sanjay kumar"),STRCMP("Sanjay Kumar","sanjay"),STRCMP("Sanjay","sanjay kumar");

-- right>left then 1
-- right<left then -1
-- right==left then 0

SELECT FIELD("ram","Sanjay","Ram","Shivank") AS Find1,FIND_IN_SET("ram","Sanjay,Ram,Shivank") AS Find2;

SELECT FORMAT(123.4567,2) AS Value1,FORMAT(123.4567,3) AS Value2;

SELECT HEX("Sanjay Kumar"),HEX(10),HEX(15);
```

![4](https://github.com/user-attachments/assets/abf09503-a3dd-4f3d-80b1-0026c630e740)

```sql
SELECT CURRENT_DATE(),CURDATE(),SYSDATE(),NOW();

SELECT DATE("2019-07-26 09:54:36"),YEAR("2019-07-26 09:54:36"),MONTH("2019-07-26 09:54:36"),MONTHNAME("2019-07-26 09:54:36");

SELECT QUARTER("2019-07-26 09:54:36"),QUARTER("2019-03-26 09:54:36"),DAY("2019-07-26 09:54:36"),DAYOFMONTH("2019-07-26 09:54:36"),DAYNAME("2019-07-26 09:54:36");

-- January - March, QUARTER = 1
-- Aprail - June, QUARTER = 2
-- July - September, QUARTER = 3
-- October - December, QUARTER = 4

SELECT DAYNAME("2019-07-26 09:54:36"),DAYOFWEEK("2019-07-26 09:54:36");

SELECT DAYNAME("2020-09-27 11:34:45"),DAYOFWEEK("2020-09-27 11:34:45"),DAYOFYEAR("2020-09-27 11:34:45"),WEEK("2020-09-27 11:34:45"),WEEKDAY("2020-09-27 11:34:45");

SELECT YEARWEEK("2019-08-21"),LAST_DAY("2019-08-21") AS LastDateOfMonth8;

SELECT EXTRACT(YEAR FROM "2018-09-22"),EXTRACT(MONTH FROM "2018-09-22"),EXTRACT(WEEK FROM "2018-09-22");
```
![5](https://github.com/user-attachments/assets/5e80c96b-3757-4832-9c52-03ac01a5dfa7)

```sql
-- We can add DATE,MONTH,DAY,WEEK,HOURS

SELECT ADDDATE("2019-09-12", INTERVAL 10 DAY),ADDDATE("2019-09-12", INTERVAL 2 MONTH);
```
![6](https://github.com/user-attachments/assets/766bc31b-49b7-4dd0-ae57-b4a3058fe3b4)

```sql
SELECT MAKEDATE(2019,7);

SELECT SUBDATE("2019-09-12",INTERVAL 10 DAY); -- Same like ADDDATE but it subtracts

SELECT DATEDIFF("2019-10-01","2020-10-01"),TO_DAYS("2000-01-01"),FROM_DAYS("730485"); -- Base Yar = 0

SELECT DATE_FORMAT("2010-09-01","%d-%b-%y"); -- 01-Sep-10
```

<h2>Features of MySQL ALTER Command</h2>

The ALTER command in MySQL is used to modify the structure of an existing database table. It allows you to perform various operations such as adding, modifying, or deleting columns, as well as adding or removing constraints.

1. **Add Column**

```sql
ALTER TABLE table_name
ADD column_name datatype;
```
1. **Modify Column**

- Changing Data Type of a column

```sql
ALTER TABLE table_name
MODIFY column_name datatype;
```
- Adding Constrains to a columns

```sql
ALTER TABLE table_name
MODIFY column_name datatype NOT NULL;
```

3. **Delete Column / Drop Column**

```sql
ALTER TABLE table_name
DROP COLUMN column_name datatype;
```

4. **Rename / Change Column Name**

```sql
ALTER TABLE table_name
CHANGE column_name new_name datatype;
```

5. **Rename Table**

```sql
ALTER TABLE table_name
RENAME new_table_name;
```

6. **Changing Column Position**

```sql
ALTER TABLE table_name
MODIFY column_name column_type
[AFTER other_column | FIRST];
```

```sql
ALTER TABLE employees
MODIFY email VARCHAR(255) FIRST;
```
```sql
ALTER TABLE employees
MODIFY email VARCHAR(255) AFTER last_name;
```


