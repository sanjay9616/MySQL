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


