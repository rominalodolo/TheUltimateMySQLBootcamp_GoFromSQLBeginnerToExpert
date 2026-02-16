# The Ultimate My SQL Bootcamp: Go from SQL Beginner to Expert

The Ultimate MySQL Bootcamp: Go from SQL Beginner to Expert, the Udemy course for SQL. 

UPDATED version 2025 

View it [HERE](https://www.udemy.com/course/the-ultimate-mysql-bootcamp-go-from-sql-beginner-to-expert/?couponCode=UPGRADE02223)

Currently running through this course, 2 December 2025. 
Lectures: 384
Video: 22 total hours
By Colt Steele


> Slides and course material available on the course
> 
> W3 schools [SQL Sand Box](https://www.w3schools.com/sql/trysql.asp?filename=trysql_op_or)


What is a database: 
1. Collection of data
2. A method for accessing and manipulating that data


Database vs. Database Management System
![Database vs. Database Management System image](https://github.com/user-attachments/assets/816f5bff-e4f6-4e49-b271-9b0e296ae4ee)
These are all management systems that work with your data base. 

SQL = structured query language 

MySQL, SQLite, Postgress, Oracle, etc. = relational databases 

Installing MySQL workbench: 
> [Video tutorial](https://www.youtube.com/watch?v=wpGnJHb2R58)
> to insall from 11 months ago


## Terminal configuration for MySQL
> [Download](https://dev.mysql.com/downloads/mysql/) SQL
> My current local set up is MAC os 13, and M1 chip.
> Downloading the 8.4.0 version ARM type
> <img width="2658" height="1424" alt="image" src="https://github.com/user-attachments/assets/b844d478-cf4a-4583-8bcf-8c75e4641935" />
> <img width="635" height="415" alt="image" src="https://github.com/user-attachments/assets/a3e2fa7f-f903-4a9d-91bb-4e3690bf70a2" />

- Check which terminal you are using with this command:
    
    ``echo $SHELL``
  
    
- If you get `/bin/zsh` then execute this line to configure MySQL:
    
    echo "export PATH=\${PATH}:/usr/local/mysql/bin" >> ~/.zshrc

    mysql -u root -p


I ran into a few issues so I restarted my terminal and ran these: 
> > sudo /usr/local/mysql/support-files/mysql.server start
> > 
> > /usr/local/mysql/bin/mysql -u root -p
```
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 11
Server version: 8.4.0 MySQL Community Server - GPL

Copyright (c) 2000, 2024, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
```
Then I killed the terminal to check by running `mysql --version`
<img width="505" height="110" alt="image" src="https://github.com/user-attachments/assets/8ec4022f-a817-481c-93d7-bf32e06e64c6" />
<img width="202" height="143" alt="image" src="https://github.com/user-attachments/assets/906856ea-1865-41ec-948f-15ba628846ce" />

### Issues on a new laptop with setting up permissions for mysql and solutions
> 
> <img width="2022" height="1100" alt="Snip20260201_30" src="https://github.com/user-attachments/assets/9f92911a-d989-4608-ac91-e9eb099362d4" />
> 
>  Run this command to check ` ls -ld /usr/local/mysql/data `
> 
>  If you see something like: ` drwx------  root  wheel`
> or owned by your user instead of mysql, then that would be this permissions issue.
> 
>  I got this result:
```
	ls -ld /usr/local/mysql/data
 drwxr-x---@ 33 rominalodolo  _mysql  1056 Feb  2 09:06 /usr/local/mysql/data
 rominalodolo@Rominas-MacBook-Pro-2 ~ % sudo chown -R _mysql:_mysql /usr/local/mysql/data
```
rominalodolo → owner user
_mysql → group
Permissions: drwxr-x--- →
Owner (rominalodolo) → read/write/execute ✅
Group (_mysql) → read/execute ✅ (no write ❌)

 ### The fix
Change the ownership so the MySQL server user _mysql owns the folder
` sudo chown -R _mysql:_mysql /usr/local/mysql/data `

Then make sure permissions are okay:
` sudo chmod -R 750 /usr/local/mysql/data`

> 7 → owner _mysql can read/write/execute
> 5 → group can read/execute
> 0 → others nothing

Checking permissions : ` ls -la /usr/local/mysql/data `
 <img width="1105" height="693" alt="Screenshot 2026-02-02 at 11 58 58" src="https://github.com/user-attachments/assets/54210bc6-00a9-4c1e-b9d9-c43a519e1e2e" />


Still did not work so I removed Mysql and workbench from my laptop, restared the laptop and downloaded the workbench and server files for sql. 

---

Get more [Docs](https://dev.mysql.com/doc/) 

Quick Qs
To list available databases:
``show databases;``

The general command for creating a database:
``CREATE DATABASE <database_name>;``

A specific example:
``CREATE DATABASE soap_store;``

To drop a database:
``DROP DATABASE <database-name>;``

To use a database:
``USE <database-name>;``


<img width="1771" height="950" alt="image" src="https://github.com/user-attachments/assets/8cd49bfc-9ac3-4e64-bda1-e4f4541bd42f" />
> MySQL and Workbench are working and tested. 

```
Creating Tables:

CREATE TABLE cats (
    name VARCHAR(50),
    age INT
);
 
CREATE TABLE dogs (
    name VARCHAR(50),
    breed VARCHAR(50),
    age INT
);


```

DESC = Describe and can use this to see the table cols and data in your specified table

See your work and if the data updated by: 

> ``SHOW tables;``
> 
> ``SHOW COLUMNS FROM cats;``
> 
> ``DESC cats;``
> 


Drop table will delete the specified table (use with caution)

Making Database to add new tables to 
> ``CREATE DATABASE testing;``
> 
> ``CREATE TABLE people (first_name VARCHAR(20), last_name VARCHAR(20), age INT);``
> 
> ``DESC people;``
> 
> ``SELECT * FROM people;``
> 
> <img width="911" height="851" alt="image" src="https://github.com/user-attachments/assets/073dc4c4-21ba-446e-9d68-44b11c976a6f" />

### INSERT INTO 
> ``INSERT INTO people (first_name, last_name, age)``
> ``VALUES (’Vector’, ‘James’, 30), (‘Sally’, ‘Beth’, 82), (‘John’, ‘Doe’, 54);``
> ``SELECT * FROM people; ``
> ``DROP TABLE people; ``
> ``SHOW TABLES; ``

### NULL values
No value / Unknown value 
`` CREATE TABLE cats2 ( name VARCHAR(100) NOT NULL, age INT NOT NULL);``

Not NULL 
`CREATE TABLE cats2 (
    name VARCHAR(100) NOT NULL,
    age INT NOT NULL
);`

### DEFAULT values 
> is setting the values to have a value even when none is being added to the col in the table. It will show that value instead
> 
> ``NOT NULL DEFAUT 'unnamed'``

EG: 
``CREATE TABLE cats3  (    
    name VARCHAR(20) DEFAULT 'no name provided',    
    age INT DEFAULT 99  
); ``

OR 

``CREATE TABLE cats4  (    
    name VARCHAR(20) NOT NULL DEFAULT 'unnamed',    
    age INT NOT NULL DEFAULT 99 
);``


### Primary Keys 
Adding unique identifiers to tables so that each record has an ID that uniquely distinguishes it from others.

``Specifing Primary Keys example: 
CREATE TABLE unique_cats (
	cat_id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    age INT NOT NULL
);``

OR 

``CREATE TABLE unique_cats2 (
	cat_id INT,
    name VARCHAR(100) NOT NULL,
    age INT NOT NULL,
    PRIMARY KEY (cat_id)
);``


Primary Keys can never be NULL. They always have a value and values are always unique. Using AUTO_INCREMEANT will help you have ids that automatically increment as you add values. 

Example:
`` CREATE TABLE unique_cats3 (
    cat_id INT AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    age INT NOT NULL,
    PRIMARY KEY (cat_id)
); ``

Exercise to wrap up the section
<img width="902" height="260" alt="image" src="https://github.com/user-attachments/assets/88a1b9c8-97a0-4c11-bd7e-947bc1a5a430" />

-- Defining employees table

```
CREATE TABLE employees (
    id INT AUTO_INCREMENT,
    first_name VARCHAR(255) NOT NULL,
    last_name VARCHAR(255) NOT NULL,
    middle_name VARCHAR(255),
    age INT NOT NULL,
    current_status VARCHAR(255) NOT NULL DEFAULT 'employed',
    PRIMARY KEY(id)
);

```

-- Another way of defining the primary key:


```
CREATE TABLE employees (
    id INT AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(255) NOT NULL,
    last_name VARCHAR(255) NOT NULL,
    middle_name VARCHAR(255),
    age INT NOT NULL,
    current_status VARCHAR(255) NOT NULL DEFAULT 'employed'
);
```


-- A test INSERT:
```
INSERT INTO employees(first_name, last_name, age) VALUES
('Dora', 'Smith', 58);
```



### Basics of mySQL with CRUD 
>
> CREATE, READ, UPDATE, DELETE
>
``
DROP TABLE cats;
``


-- Create the new cats table:
```
CREATE TABLE cats (
    cat_id INT AUTO_INCREMENT,
    name VARCHAR(100),
    breed VARCHAR(100),
    age INT,
    PRIMARY KEY (cat_id)
);
```

-- Insert some cats:
```
INSERT INTO cats(name, breed, age) 
VALUES ('Ringo', 'Tabby', 4),
       ('Cindy', 'Maine Coon', 10),
       ('Dumbledore', 'Maine Coon', 11),
       ('Egg', 'Persian', 4),
       ('Misty', 'Tabby', 13),
       ('George Michael', 'Ragdoll', 9),
       ('Jackson', 'Sphynx', 7);
```


-- To get all the columns:

`SELECT * FROM cats;`



-- To only get the age column:

`SELECT age FROM cats;`



-- To select multiple specific columns:

`SELECT name, breed FROM cats;`


-- Use where to specify a condition:

`SELECT * FROM cats WHERE age = 4; `

`SELECT * FROM cats WHERE name ='Egg';`


Select Challenges Solution
`SELECT cat_id FROM cats;`

`SELECT name, breed FROM cats;`

`SELECT name, age FROM cats WHERE breed='Tabby';`

`SELECT cat_id, age FROM cats WHERE cat_id=age;`

`SELECT * FROM cats WHERE cat_id=age;`


-- Use 'AS' to alias a column in your results (it doesn't actually change the name of the column in the table)

`SELECT cat_id AS id, name FROM cats;`

*Updating Data*
Change tabby cats to shorthair:

`UPDATE cats SET breed='Shorthair' WHERE breed='Tabby';`

Another update:

`UPDATE cats SET age=14 WHERE name='Misty';`


## NOTE
Always SELECT _before_ UPDATEing so you can ensure you are updating the correct item. 


**Update** Challenges Solution
`SELECT * FROM cats WHERE name='Jackson'; `
 
`UPDATE cats SET name='Jack' WHERE name='Jackson'; `
 
`SELECT * FROM cats WHERE name='Jackson'; `
 
`SELECT * FROM cats WHERE name='Jack'; `
 
`SELECT * FROM cats WHERE name='Ringo'; `
 
`UPDATE cats SET breed='British Shorthair' WHERE name='Ringo'; `
 
`SELECT * FROM cats WHERE name='Ringo'; `
 
`SELECT * FROM cats; `
 
`SELECT * FROM cats WHERE breed='Maine Coon'; `
 
`UPDATE cats SET age=12 WHERE breed='Maine Coon'; `
 
`SELECT * FROM cats WHERE breed='Maine Coon';`


-- Delete all cats with name of 'Egg':

`DELETE FROM cats WHERE name='Egg';`


-- Delete all rows in the cats table:

`DELETE FROM cats;`

-- Delete all 4 year old cats:

DELETE FROM cats WHERE age=4;


-- Delete cats where cat_id is the same as their age:

`DELETE FROM cats WHERE cat_id=age;`


-- Delete all cats:

`DELETE FROM cats;`


Exercise 

```
CREATE DATABASE shirts_db;
 
USE shirts_db;
 
CREATE TABLE shirts (
    shirt_id INT AUTO_INCREMENT PRIMARY KEY,
    article VARCHAR(50),
    color VARCHAR(50),
    shirt_size VARCHAR(5),
    last_worn INT
);
 
DESC shirts;
 
INSERT INTO shirts (article, color, shirt_size, last_worn)  
VALUES 
	('t-shirt', 'white', 'S', 10),
	('t-shirt', 'green', 'S', 200),
	('polo shirt', 'black', 'M', 10),
	('tank top', 'blue', 'S', 50),
	('t-shirt', 'pink', 'S', 0),
	('polo shirt', 'red', 'M', 5),
	('tank top', 'white', 'S', 200),
	('tank top', 'blue', 'M', 15);
 
INSERT INTO shirts (article, color, shirt_size, last_worn)
VALUES ('polo shirt','purple', 'M', 50);
```


Using Select in the exercise
```
SELECT article, color FROM shirts;
 
SELECT * FROM shirts WHERE shirt_size='M';
 
SELECT article, color, shirt_size, last_worn FROM shirts WHERE shirt_size='M';
```


Exercise solution 

```
UPDATE shirts 
SET 
    shirt_size = 'L'
WHERE
    article = 'polo shirt';
    
    
UPDATE shirts 
SET 
    last_worn = 0
WHERE
    last_worn = 15;
    
    
UPDATE shirts 
SET 
    color = 'off white',
    shirt_size = 'XS'
WHERE
    color = 'white';
```

DELETE FROM Exercise
```
SELECT * FROM shirts WHERE last_worn=200;
 
DELETE FROM shirts WHERE last_worn=200;
 
 
SELECT * FROM shirts WHERE article='tank top';
 
DELETE FROM shirts WHERE article='tank top';
 
 
 
SELECT * FROM shirts;
 
DELETE FROM shirts;
 
 
 
 
DROP TABLE shirts;
 
 
show tables;
 
DESC shirts;
```


### String Functions
> [Docs](https://dev.mysql.com/doc/refman/8.0/en/string-functions.html)
> 

#### Books Table Data 
> Inserting data to use in exercises.
> 
> Create table then Insert the data.
> 
```

CREATE TABLE books 
	(
		book_id INT AUTO_INCREMENT,
		title VARCHAR(100),
		author_fname VARCHAR(100),
		author_lname VARCHAR(100),
		released_year INT,
		stock_quantity INT,
		pages INT,
		PRIMARY KEY(book_id)
	);
 
INSERT INTO books (title, author_fname, author_lname, released_year, stock_quantity, pages)
VALUES
('The Namesake', 'Jhumpa', 'Lahiri', 2003, 32, 291),
('Norse Mythology', 'Neil', 'Gaiman',2016, 43, 304),
('American Gods', 'Neil', 'Gaiman', 2001, 12, 465),
('Interpreter of Maladies', 'Jhumpa', 'Lahiri', 1996, 97, 198),
('A Hologram for the King: A Novel', 'Dave', 'Eggers', 2012, 154, 352),
('The Circle', 'Dave', 'Eggers', 2013, 26, 504),
('The Amazing Adventures of Kavalier & Clay', 'Michael', 'Chabon', 2000, 68, 634),
('Just Kids', 'Patti', 'Smith', 2010, 55, 304),
('A Heartbreaking Work of Staggering Genius', 'Dave', 'Eggers', 2001, 104, 437),
('Coraline', 'Neil', 'Gaiman', 2003, 100, 208),
('What We Talk About When We Talk About Love: Stories', 'Raymond', 'Carver', 1981, 23, 176),
("Where I'm Calling From: Selected Stories", 'Raymond', 'Carver', 1989, 12, 526),
('White Noise', 'Don', 'DeLillo', 1985, 49, 320),
('Cannery Row', 'John', 'Steinbeck', 1945, 95, 181),
('Oblivion: Stories', 'David', 'Foster Wallace', 2004, 172, 329),
('Consider the Lobster', 'David', 'Foster Wallace', 2005, 92, 343);

```

### CONCAT 

> Concatenate which means combining 2 strings. 
>
> We can use this to combine titles of columns and other data
>


### CONCAT_WS

> It means Concatenate with seperator
>
> It'll concat but with a seperator which would be the first item in the srting of things you want to join.
>
> So if you join it like " " and then your titles "firstname" "lastname"  you should get `firstname lastname"
> but just adding an extra white space is bad practice so rather use "-" dashes or unerscores like this "_"
>
> If you are just SELECTing data the you can add the white spaces for readability and using it for reporting
>

 Exapmle 

 ```
SELECT CONCAT('pi', 'ckle');
 
SELECT CONCAT(author_fname,' ', author_lname) AS author_name FROM books;
 
SELECT CONCAT_WS('-',title, author_fname, author_lname) FROM books;
```

### SUBSTRING() & SUBSTR()

<img width="1538" height="170" alt="image" src="https://github.com/user-attachments/assets/c8463525-8de3-410f-985c-89a04772318e" />

<img width="2166" height="1312" alt="image" src="https://github.com/user-attachments/assets/4129bb83-e244-470f-b15e-af56b9b63c80" />

> The first string is the one you want to sample from
>
> This you can make into a title name
>
> The first number you provide is the starting point
>
> The second numkber provided is the length of the sting you are calling.


Example 
`` SELECT SUBSTRING('Hello World', 1, 4); ``
> Answer is ``Hell``
>
> <img width="630" height="256" alt="image" src="https://github.com/user-attachments/assets/d47f2c3d-58c5-433f-a0c7-46a085a36c60" />

Another test to see starting point 
`` SELECT SUBSTRING('Hello World', 2, 4); ``
> Answer is ``ello``
>
> <img width="692" height="228" alt="image" src="https://github.com/user-attachments/assets/db3f2391-5de4-4718-a154-b895fa8b3705" />

Last test to see how to go grab the last few letters of the string
`` SELECT SUBSTRING('Hello World', 5); ``
> Answer is  ``o World``
>
> <img width="616" height="272" alt="image" src="https://github.com/user-attachments/assets/d3505ecf-3d56-4f9f-8b3e-920f8cc03e09" />

**You can also use a negative straing point like -3**
> This makes it count backwards from the end of the sring
>
> <img width="600" height="198" alt="image" src="https://github.com/user-attachments/assets/03f21b57-9336-4ace-bd00-7067db233b63" />

Example using the Books data 
```
SELECT SUBSTRING('Hello World', 1, 4);
 
SELECT SUBSTRING('Hello World', 7);
 
SELECT SUBSTRING('Hello World', -3);
 
SELECT SUBSTRING(title, 1, 10) AS 'short title' FROM books;
 
SELECT SUBSTR(title, 1, 10) AS 'short title' FROM books;
```

Example using the Books data by using concat then nesting the substring function 
```
SELECT CONCAT
    (
        SUBSTRING(title, 1, 10),
        '...'
    ) AS 'short title'
FROM books;
```

### Formatting SQL 

> You can use this site to do that
>
> [Code Editor ](https://codebeautify.org/sqlformatter)
> 
> OR
>
> If the mySQL workbench you can use the paint brush tool found in the tool bar
>
> <img width="1838" height="1006" alt="image" src="https://github.com/user-attachments/assets/dc9228bb-4a8b-4ece-8092-5fa2b53c0f1a" />
>
> OR
>
> You can use a formatter in your code editor, this one is VScode
> 
> <img width="2256" height="1204" alt="image" src="https://github.com/user-attachments/assets/d728899a-77b2-417f-8ff2-0f0b8d760976" />

### REPLACE 

<img width="2080" height="484" alt="image" src="https://github.com/user-attachments/assets/620a8fc4-8d00-4f5d-b747-1d39ba9a5679" />

Example
> Replacing text that you are calling with something else
>
> `` SELECT REPLACE('Hello World', 'Hell', '^&%$'); ``
>
> Answer: ``^&%$o World`` 
> 
> <img width="806" height="278" alt="image" src="https://github.com/user-attachments/assets/ea312612-dc44-4a9f-ace4-ae2667bd6899" />

> **NB: case sensitive.**
> 
> <img width="792" height="212" alt="image" src="https://github.com/user-attachments/assets/0ac652e6-2583-460e-93d7-1517be5aa60c" />

Example 
 ```
SELECT REPLACE('Hello World', 'Hell', '%$#@');
 
SELECT REPLACE('Hello World', 'l', '7');
 
SELECT REPLACE('Hello World', 'o', '0');
 
SELECT REPLACE('HellO World', 'o', '*');
 
SELECT
  REPLACE('cheese bread coffee milk', ' ', ' and ');
 
SELECT REPLACE(title, 'e ', '3') FROM books;
 
SELECT REPLACE(title, ' ', '-') FROM books;
```


### REVERSE

<img width="1240" height="412" alt="image" src="https://github.com/user-attachments/assets/95f25974-fe61-4cf0-99a5-9a415dd5761e" />
<img width="424" height="220" alt="image" src="https://github.com/user-attachments/assets/45296326-40db-4025-85e3-bf435ade54fe" />

Example
```
SELECT REVERSE('Hello World');
 
SELECT REVERSE('meow meow');
 
SELECT REVERSE(author_fname) FROM books;
 
SELECT CONCAT('woof', REVERSE('woof'));
 
SELECT CONCAT(author_fname, REVERSE(author_fname)) FROM books;

```


### CHARLENGTH

<img width="2128" height="964" alt="image" src="https://github.com/user-attachments/assets/454aac9c-7926-4da2-bc11-8e709d5a6eba" />

> Charlength vs length are not the same, LENGTH does the byte length NOT the charater length, so how mych is being stored
> 
<img width="2102" height="650" alt="image" src="https://github.com/user-attachments/assets/1e12fd09-1dae-4660-a37d-3cde65f06cd1" />

EXAMPLE OF HOW THIS WORKS: 

<img width="600" height="448" alt="image" src="https://github.com/user-attachments/assets/4e61ddb0-bb7e-4687-83af-84879c7243e0" />

Example code to play with:

```
SELECT CHAR_LENGTH('Hello World');
 
SELECT CHAR_LENGTH(title) as length, title FROM books;
 
SELECT author_lname, CHAR_LENGTH(author_lname) AS 'length' FROM books;
 
SELECT CONCAT(author_lname, ' is ', CHAR_LENGTH(author_lname), ' characters long') FROM books;

```

### LOWWER and UPPER 

> Returns your query in upper or lower case
>
> Example: 
```
SELECT UPPER('Hello World');
 
SELECT LOWER('Hello World');
 
SELECT UPPER(title) FROM books;
 
SELECT CONCAT('MY FAVORITE BOOK IS ', UPPER(title)) FROM books;
 
SELECT CONCAT('MY FAVORITE BOOK IS ', LOWER(title)) FROM books;

```

### RIGHT or LEFT  or REPEAT  or TRIM

<img width="1354" height="420" alt="image" src="https://github.com/user-attachments/assets/e7e60d1f-c632-46ea-b290-c11b3173905d" />

<img width="1354" height="430" alt="image" src="https://github.com/user-attachments/assets/9c6a5993-a73f-4126-8315-0e42e8ea04bb" />

<img width="2130" height="354" alt="image" src="https://github.com/user-attachments/assets/921e26f9-e630-4dde-8bac-f5d2cdee356a" />

<img width="2090" height="718" alt="image" src="https://github.com/user-attachments/assets/93d671f3-16a5-4354-abb4-5dee4315ad63" />
>>
>> Removes trailing spaces not all the spaces in the words unless you specify
>>

Example
```
SELECT INSERT('Hello Bobby', 6, 0, 'There'); 
 
SELECT LEFT('omghahalol!', 3);
 
SELECT RIGHT('omghahalol!', 4);
 
SELECT REPEAT('ha', 4);
 
SELECT TRIM('  pickle  ');
```

Challenge:
```
SELECT REVERSE(UPPER('Why does my cat look at me with such hatred?'));
 
SELECT REPLACE(title, ' ', '->') AS title FROM books;
 
SELECT 
    author_lname AS forwards, REVERSE(author_lname) AS backwards
FROM
    books;
    
 
SELECT UPPER(CONCAT(author_fname, ' ', author_lname)) AS 'full name in caps' FROM books;
 
 
SELECT CONCAT(title, ' was released in ', released_year) AS blurb FROM books;
 
SELECT title, CHAR_LENGTH(title) AS character_count FROM books;
 
SELECT 
    CONCAT(SUBSTR(title, 1, 10), '...') AS short_title,
    CONCAT(author_lname, ',', author_fname) AS author,
    CONCAT(stock_quantity, ' in stock') AS quantity
FROM
    books;
``` 


## Refining Selections

Adding more data to the books table: 
```
INSERT INTO books
    (title, author_fname, author_lname, released_year, stock_quantity, pages)
    VALUES ('10% Happier', 'Dan', 'Harris', 2014, 29, 256), 
           ('fake_book', 'Freida', 'Harris', 2001, 287, 428),
           ('Lincoln In The Bardo', 'George', 'Saunders', 2017, 1000, 367);

```

### DISTINCT

You'll only get results that don't include duplictaes

<img width="2140" height="1248" alt="image" src="https://github.com/user-attachments/assets/4e15ff8b-813f-4388-94e9-ef886d2b5d1f" />

Example

```
SELECT author_lname FROM books;
 
SELECT DISTINCT author_lname FROM books;
 
SELECT author_fname, author_lname FROM books;
 
SELECT DISTINCT CONCAT(author_fname,' ', author_lname) FROM books;
 
SELECT DISTINCT author_fname, author_lname FROM books;

```


## ORDERBY

> Ascends by default.
>
> <img width="2132" height="724" alt="image" src="https://github.com/user-attachments/assets/10d76d46-7377-453b-b0b0-f1631bc43935" />
>
> Example
```
SELECT * FROM books
ORDER BY author_lname;
 
SELECT * FROM books
ORDER BY author_lname DESC;
 
SELECT * FROM books
ORDER BY released_year;
```
> Another example by using DESC abd multible columns 
>
```
SELECT book_id, author_fname, author_lname, pages
FROM books ORDER BY 2 desc;
 
SELECT book_id, author_fname, author_lname, pages
FROM books ORDER BY author_lname, author_fname;
```

## LIMIT 

It will limit the amount you get back, the number added after with say the limit you want from you results.  

Example
 ```
SELECT title FROM books LIMIT 3;
 
SELECT title FROM books LIMIT 1;
 
SELECT title FROM books LIMIT 10;
 
SELECT * FROM books LIMIT 1;
 
SELECT title, released_year FROM books 
ORDER BY released_year DESC LIMIT 5;
 
SELECT title, released_year FROM books 
ORDER BY released_year DESC LIMIT 1;
 
SELECT title, released_year FROM books 
ORDER BY released_year DESC LIMIT 14;
 
SELECT title, released_year FROM books 
ORDER BY released_year DESC LIMIT 0,5;
 
SELECT title, released_year FROM books 
ORDER BY released_year DESC LIMIT 0,3;
 
SELECT title, released_year FROM books 
ORDER BY released_year DESC LIMIT 1,3;
 
SELECT title, released_year FROM books 
ORDER BY released_year DESC LIMIT 10,1;
 
SELECT * FROM books LIMIT 95,18446744073709551615;
 
SELECT title FROM books LIMIT 5;
 
SELECT title FROM books LIMIT 5, 123219476457;
 
SELECT title FROM books LIMIT 5, 50;
```

## LIKE 

Perform basic searching
Has to be the exact match string OR you can use % before and after the string you want to search to help you find the item you are looking for. 
Using '_' helps you find that many characters.
Using '%' helps you find everything.

EXAMPLE
```
SELECT title, author_fname, author_lname, pages 
FROM books
WHERE author_fname LIKE '%da%';
 
SELECT title, author_fname, author_lname, pages 
FROM books
WHERE title LIKE '%:%';
 
SELECT * FROM books
WHERE author_fname LIKE '____';
 
SELECT * FROM books
WHERE author_fname LIKE '_a_';

```

If there are sentences with % or _ the you can use an escape '/' character
you use this before the character you want to use. 

Example 
-- To select books with '%' in their title:
``SELECT * FROM books 
WHERE title LIKE '%\%%';``
 
-- To select books with an underscore '_' in title:
``SELECT * FROM books 
WHERE title LIKE '%\_%';``


Excersise:
```
SELECT title FROM books WHERE title LIKE '%stories%';
 
SELECT title, pages FROM books ORDER BY pages DESC LIMIT 1;
 
SELECT 
    CONCAT(title, ' - ', released_year) AS summary 
FROM books ORDER BY released_year DESC LIMIT 3;
 
SELECT title, author_lname FROM books WHERE author_lname LIKE '% %';
 
SELECT title, released_year, stock_quantity 
FROM books ORDER BY stock_quantity LIMIT 3;
 
SELECT title, author_lname 
FROM books ORDER BY author_lname, title;
 
SELECT title, author_lname 
FROM books ORDER BY 2,1;
 
SELECT
    CONCAT(
        'MY FAVORITE AUTHOR IS ',
        UPPER(author_fname),
        ' ',
        UPPER(author_lname),
        '!'
    ) AS yell
FROM books ORDER BY author_lname;

```

## Aggregate Functions

#### COUNT 

`SELECT COUNT (*) FROM books;` this gets back the rows - select the number of rows from books 

doesn't play nice to do multiple with functions. Just run it without other functions. 

`SELECT COUNT(*) FROM books;`
 
`SELECT COUNT(author_lname) FROM books;`
 
`SELECT COUNT(DISTINCT author_lname) FROM books;`
 
`SELECT COUNT(*) FROM books WHERE title LIKE '%the%';`

#### GROUP BY

"GROUP BY summarises or aggregates identical data into single rows"

```
SELECT author_lname, COUNT(*) 
FROM books
GROUP BY author_lname;
 
SELECT 
    author_lname, COUNT(*) AS books_written
FROM
    books
GROUP BY author_lname
ORDER BY books_written DESC;
```

What this looks like in Workbench:

<img width="1313" height="909" alt="Screenshot 2026-02-06 at 13 59 26" src="https://github.com/user-attachments/assets/c4a4a30f-3dd2-4ec3-a995-27990d2371b8" />

#### MIN & MAX 

`SELECT MAX(pages) FROM books;`
 
`SELECT MIN(author_lname) FROM books;`


#### Subqueries 

``` SELECT title, pages FROM books
WHERE pages = (SELECT MAX(pages) FROM books);
 
SELECT MIN(released_year) FROM books;
 
SELECT title, released_year FROM books 
WHERE released_year = (SELECT MIN(released_year) FROM books);
```

<img width="1313" height="909" alt="Screenshot 2026-02-06 at 14 14 40" src="https://github.com/user-attachments/assets/109ca11e-b90d-429f-9a29-b626903a7882" />



#### GROUP BY multiple columns

```
SELECT author_fname, author_lname, COUNT(*) 
FROM books 
GROUP BY author_lname, author_fname;
 
 
SELECT CONCAT(author_fname, ' ', author_lname) AS author,  COUNT(*)
FROM books
GROUP BY author;
```
<img width="1313" height="909" alt="Screenshot 2026-02-06 at 14 25 36" src="https://github.com/user-attachments/assets/5fc94d94-6952-47af-8a38-b1bea8a3f293" />


#### MIN and MAX with GROUP BY 

The question is "Find the year each author published their first book. 


`SELECT author_lname, MIN(released_year) FROM books GROUP BY author_lname;`
 
`SELECT author_lname, MAX(released_year), MIN(released_year) FROM books GROUP BY author_lname;`


 ```
SELECT 
	author_lname, 
	COUNT(*) as books_written, 
	MAX(released_year) AS latest_release,
	MIN(released_year)  AS earliest_release,
      MAX(pages) AS longest_page_count
FROM books GROUP BY author_lname;
 ```


 ```
SELECT 
	author_lname, 
        author_fname,
	COUNT(*) as books_written, 
	MAX(released_year) AS latest_release,
	MIN(released_year)  AS earliest_release
FROM books GROUP BY author_lname, author_fname;
```

<img width="1313" height="909" alt="Screenshot 2026-02-06 at 14 48 23" src="https://github.com/user-attachments/assets/578b3aa6-20db-4579-9b96-4f200e4d9d80" />


#### SUM 

Example: 
` SELECT SUM(pages) FROM books;`
 
 ```
SELECT author_lname, COUNT(*), SUM(pages)
FROM books
GROUP BY author_lname;
```


#### AVG 

`SELECT AVG(pages) FROM books;`

`SELECT AVG(released_year) FROM books;`


```
SELECT 
    released_year, 
    AVG(stock_quantity), 
    COUNT(*) FROM books
GROUP BY released_year;
```





`SELECT COUNT(*) FROM books;`
 
``SELECT released_year, COUNT(*) 
FROM books GROUP BY released_year;``
 
`SELECT SUM(stock_quantity) FROM books;`
 
``SELECT AVG(released_year) 
FROM books GROUP BY author_lname, author_fname;``
 
 
``SELECT CONCAT(author_fname, ' ', author_lname) AS author, pages FROM books
WHERE pages = (SELECT MAX(pages) FROM books);``
 
``SELECT CONCAT(author_fname, ' ', author_lname) AS author, pages FROM books
ORDER BY pages DESC LIMIT 1;``
 

```
SELECT 
    released_year AS year,
    COUNT(*) AS '# books',
    AVG(pages) AS 'avg pages'
FROM books
GROUP BY released_year
ORDER BY released_year;
```


### Data Types 

#### CHAR vs VARCHAR 

Docs: https://dev.mysql.com/doc/refman/8.0/en/string-types.html 
- "The CHAR and VARCHAR types are similar, but differ in the way they are stored and retrieved. They also differ in maximum length and in whether trailing spaces are retained."

CHAR (0 to 255) Always specify how many characters you want to retrieve. Use for all fixed amount of items you want like cell number etc. 
VARCHAR (0 to 65,535)

<img width="659" height="162" alt="Screenshot 2026-02-09 at 22 46 04" src="https://github.com/user-attachments/assets/76fe9019-a5be-4e79-8ecf-4bdf6d02c691" />



#### NUMERIC: INT TINYINT BIGINT ...
<img width="1155" height="222" alt="Screenshot 2026-02-09 at 22 52 42" src="https://github.com/user-attachments/assets/e5fb8d14-13fb-4379-8a27-6081621e6897" />


#### DECIMAL

- "Standard SQL requires that DECIMAL(5,2) be able to store any value with five digits and two decimals, so values that can be stored in the salary column range from -999.99 to 999.99."


#### FLOAT and DOUBLE 

- "The FLOAT and DOUBLE types represent approximate numeric data values. "

#### DATE and TIME 

Docs: https://dev.mysql.com/doc/refman/8.0/en/datetime.html 

<img width="1155" height="363" alt="Screenshot 2026-02-09 at 23 16 15" src="https://github.com/user-attachments/assets/c725489d-197d-4273-8d1b-11c19da47380" />

<img width="1508" height="817" alt="Screenshot 2026-02-09 at 23 17 07" src="https://github.com/user-attachments/assets/359936a8-5c6e-46c3-923f-5384ed81b3b2" />

Example:

``` CREATE TABLE people (
	name VARCHAR(100),
    birthdate DATE,
    birthtime TIME,
    birthdt DATETIME
);
 
INSERT INTO people (name, birthdate, birthtime, birthdt)
VALUES ('Elton', '2000-12-25', '11:00:00', '2000-12-25 11:00:00');
 
INSERT INTO people (name, birthdate, birthtime, birthdt)
VALUES ('Lulu', '1985-04-11', '9:45:10', '1985-04-11 9:45:10');
 
INSERT INTO people (name, birthdate, birthtime, birthdt)
VALUES ('Juan', '2020-08-15', '23:59:00', '2020-08-15 23:59:00');
```

#### CURDATE CURTIME & NOW 

`SELECT CURTIME();`
 
`SELECT CURDATE();`
 
`SELECT NOW();`
 
``INSERT INTO people (name, birthdate, birthtime, birthdt)
VALUES ('Hazel', CURDATE(), CURTIME(), NOW());``

<img width="463" height="197" alt="Screenshot 2026-02-09 at 23 32 50" src="https://github.com/user-attachments/assets/e7420c52-6a59-44d6-872e-fcd8660c54da" />



#### Date functions

```
SELECT 
    birthdate,
    DAY(birthdate),
    DAYOFWEEK(birthdate),
    DAYOFYEAR(birthdate)
FROM people;
 
SELECT 
    birthdate,
    MONTHNAME(birthdate),
    YEAR(birthdate)
FROM people;
```

#### Time functions

```
SELECT 
    birthtime,
    HOUR(birthtime),
    MINUTE(birthtime)
FROM people;
 
SELECT 
    birthdt,
    MONTH(birthdt),
    DAY(birthdt),
    HOUR(birthdt),
    MINUTE(birthdt)
FROM people;
```

#### Formatting dates

Docs: https://dev.mysql.com/doc/refman/8.0/en/date-and-time-functions.html

<img width="447" height="498" alt="Screenshot 2026-02-09 at 23 48 05" src="https://github.com/user-attachments/assets/b9b991ef-97c8-458b-bde9-7c677235a171" />


`SELECT birthdate, DATE_FORMAT(birthdate, '%a %b %D') FROM people;`
 
`SELECT birthdt, DATE_FORMAT(birthdt, '%H:%i') FROM people;`
 
`SELECT birthdt, DATE_FORMAT(birthdt, 'BORN ON: %r') FROM people;`

#### Date math, TIMESTAMPS, DEFAULT and ON UPDATE TIMESTAMPS

```
CREATE TABLE captions (
  text VARCHAR(150),
  created_at TIMESTAMP default CURRENT_TIMESTAMP
);
 
CREATE TABLE captions2 (
  text VARCHAR(150),
  created_at TIMESTAMP default CURRENT_TIMESTAMP,
  updated_at TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```


```
-- What's a good use case for CHAR?
 
-- Used for text that we know has a fixed length, e.g., State abbreviations, 
-- abbreviated company names, etc.
 
CREATE TABLE inventory (
    item_name VARCHAR(100),
    price DECIMAL(8,2),
    quantity INT
);
 
-- What's the difference between DATETIME and TIMESTAMP?
 
-- They both store datetime information, but there's a difference in the range, 
-- TIMESTAMP has a smaller range. TIMESTAMP also takes up less space. 
-- TIMESTAMP is used for things like meta-data about when something is created
-- or updated.
 
 
SELECT CURTIME();
 
SELECT CURDATE();
 
SELECT DAYOFWEEK(CURDATE());
SELECT DAYOFWEEK(NOW());
SELECT DATE_FORMAT(NOW(), '%w') + 1;
 
SELECT DAYNAME(NOW());
SELECT DATE_FORMAT(NOW(), '%W');
 
SELECT DATE_FORMAT(CURDATE(), '%m/%d/%Y');
 
SELECT DATE_FORMAT(NOW(), '%M %D at %k:%i');
 
CREATE TABLE tweets(
    content VARCHAR(140),
    username VARCHAR(20),
    created_at TIMESTAMP DEFAULT NOW()
);
 
INSERT INTO tweets (content, username) VALUES('this is my first tweet', 'coltscat');
SELECT * FROM tweets;
 
INSERT INTO tweets (content, username) VALUES('this is my second tweet', 'coltscat');
SELECT * FROM tweets;
```


## Comparison & Logical Operators

NOT EQUAL operator !=

``SELECT * FROM books
WHERE released_year != 2017;``

NOT LIKE
``SELECT * FROM books
WHERE title NOT LIKE '%e%';
``

Less than Or Equal To
``
SELECT * FROM books
WHERE pages < 200;
``

 ``
SELECT * FROM books
WHERE released_year < 2000;
``

 ``
SELECT * FROM books
WHERE released_year <= 1985;
``

Logigal AND
``
SELECT title, author_lname, released_year FROM books
WHERE released_year > 2010
AND author_lname = 'Eggers';
``

`` 
SELECT title, author_lname, released_year FROM books
WHERE released_year > 2010
AND author_lname = 'Eggers'
AND title LIKE '%novel%';
``

Both conditions must be true to show results

Logical OR
``
SELECT title, pages FROM books 
WHERE CHAR_LENGTH(title) > 30
AND pages > 500;
``

`` 
SELECT title, author_lname FROM books
WHERE author_lname='Eggers' AND
released_year > 2010;
``

``
SELECT title, author_lname, released_year FROM books
WHERE author_lname='Eggers' OR
released_year > 2010;
`` 

`` 
SELECT title, pages FROM books
WHERE pages < 200 
OR title LIKE '%stories%';
``

both conditions can be true to produce results


Between
``
SELECT title, released_year FROM books
WHERE released_year <= 2015
AND released_year >= 2004;
``

 ``
SELECT title, released_year FROM books
WHERE released_year BETWEEN 2004 AND 2014;
``

Comparing Data

``
SELECT * FROM people WHERE birthtime 
BETWEEN CAST('12:00:00' AS TIME) 
AND CAST('16:00:00' AS TIME);
`` 

 ``
SELECT * FROM people WHERE HOUR(birthtime)
BETWEEN 12 AND 16;
``

CAST
<img width="1144" height="433" alt="image" src="https://github.com/user-attachments/assets/0f5d5bbb-19c4-43d3-adcf-0615296f00df" />


IN operator 

``
SELECT title, author_lname FROM books
WHERE author_lname = 'Carver' 
OR author_lname = 'Lahiri'
OR author_lname = 'Smith';
``

`` 
SELECT title, author_lname FROM books
WHERE author_lname IN ('Carver', 'Lahiri', 'Smith');
``

 ``
SELECT title, author_lname FROM books
WHERE author_lname NOT IN ('Carver', 'Lahiri', 'Smith');
`` 

`` 
SELECT title, released_year FROM books
WHERE released_year >= 2000 
AND released_year % 2 = 1;
``

CASE

``
SELECT title, released_year,
CASE
	WHEN released_year >= 2000 THEN 'modern lit'
    ELSE '20th century lit' 
END AS genre
FROM books;
``
 
`` 
SELECT 
    title,
    stock_quantity,
    CASE
        WHEN stock_quantity BETWEEN 0 AND 40 THEN '*'
        WHEN stock_quantity BETWEEN 41 AND 70 THEN '**'
        WHEN stock_quantity BETWEEN 71 AND 100 THEN '***'
        WHEN stock_quantity BETWEEN 101 AND 140 THEN '****'
        ELSE '*****'
    END AS stock
FROM
    books;
 ``

`` 
SELECT 
    title,
    stock_quantity,
    CASE
        WHEN stock_quantity <= 40 THEN '*'
        WHEN stock_quantity <= 70 THEN '**'
        WHEN stock_quantity <= 100 THEN '***'
        WHEN stock_quantity <= 140 THEN '****'
        ELSE '*****'
    END AS stock
FROM
    books;
``    




Exercise

`SELECT * FROM books WHERE released_year < 1980;`
<img width="517" height="400" alt="Screenshot 2026-02-15 at 20 54 38" src="https://github.com/user-attachments/assets/c044fad4-9cdc-4cc1-88b5-02ccc189b5cf" />

 
``SELECT * FROM books 
WHERE author_lname = 'Eggers'
OR author_lname = 'Chabon';``
<img width="514" height="344" alt="Screenshot 2026-02-15 at 20 56 30" src="https://github.com/user-attachments/assets/7b94bdf7-1839-4e0e-bf17-d4474a357aed" />

 
``SELECT * FROM books
WHERE author_lname = 'Lahiri'
AND released_year > 2000;``

 
``SELECT * FROM books
WHERE pages >= 100 
AND pages <= 200;``

 
``SELECT * FROM books
WHERE pages BETWEEN 100 and 200;``

 
``SELECT title, author_lname FROM books
WHERE author_lname LIKE 'C%'
OR author_lname LIKE 'S%';``

 
``SELECT title, author_lname
FROM books WHERE SUBSTR(author_lname, 1, 1) in ('C', 'S');``


 ```
SELECT title, author_lname,
CASE
    WHEN title LIKE '%stories%' THEN 'Short Stories'
    WHEN title = 'Just Kids' THEN 'Memoir' 
    WHEN title = 'A Heartbreaking Work of Staggering Genius' THEN 'Memior'
    ELSE 'Novel'
END AS type
FROM books;
 ```
<img width="675" height="620" alt="image" src="https://github.com/user-attachments/assets/0474b159-5af5-4480-ae62-f041c980868c" />

 ```
SELECT author_fname, author_lname,
	CASE
        WHEN COUNT(*) = 1 THEN '1 book'
        ELSE CONCAT(COUNT(*), ' books')
	END AS count
FROM books
WHERE author_lname IS NOT NULL
GROUP BY author_fname, author_lname;

```
<img width="381" height="479" alt="image" src="https://github.com/user-attachments/assets/37634661-b1b1-46e2-ace5-4e12f7f4c026" />


### Constraints and ALTER TABLE 

#### UNIQUE Constraint

```
CREATE TABLE contacts (
	name VARCHAR(100) NOT NULL,
    phone VARCHAR(15) NOT NULL UNIQUE
);
 
INSERT INTO contacts (name, phone)
VALUES ('billybob', '8781213455');
 
-- This insert would result in an error:
INSERT INTO contacts (name, phone)
VALUES ('billybob', '8781213455');

```
<img width="675" height="365" alt="image" src="https://github.com/user-attachments/assets/536a41d5-1c5d-4e7a-a2ef-4df67d39e290" />

I ran these inividually otherwise the last line throws the error and nothing adds.

#### CHECK constraints

```
CREATE TABLE users (
	username VARCHAR(20) NOT NULL,
    age INT CHECK (age > 0)
);
```

<img width="935" height="538" alt="image" src="https://github.com/user-attachments/assets/a94ef6be-4d24-4f4b-8093-08a9369fca81" />


`` 
CREATE TABLE palindromes (
  word VARCHAR(100) CHECK(REVERSE(word) = word)
)
``

<img width="935" height="538" alt="image" src="https://github.com/user-attachments/assets/8ece2310-4d4e-4103-b2c3-141f436621f6" />


#### Named constraints 

``
CREATE TABLE users2 (
    username VARCHAR(20) NOT NULL,
    age INT,
    CONSTRAINT age_not_negative CHECK (age >= 0)
);
``
<img width="935" height="538" alt="image" src="https://github.com/user-attachments/assets/a3898c41-2295-4686-830d-ad6b44c6e8ee" />


 ``
CREATE TABLE palindromes2 (
  word VARCHAR(100),
  CONSTRAINT word_is_palindrome CHECK(REVERSE(word) = word)
);
``
<img width="935" height="538" alt="image" src="https://github.com/user-attachments/assets/67132f07-8b35-4bf7-b66c-5556ec4b1898" />


#### Multiple Column Constraints

``
CREATE TABLE companies (
    name VARCHAR(255) NOT NULL,
    address VARCHAR(255) NOT NULL,
    CONSTRAINT name_address UNIQUE (name , address)
);
``
<img width="951" height="557" alt="image" src="https://github.com/user-attachments/assets/ab0cdf46-065e-4a3d-9a7f-b5b8527ef507" />


`` 
CREATE TABLE houses (
  purchase_price INT NOT NULL,
  sale_price INT NOT NULL,
  CONSTRAINT sprice_gt_pprice CHECK(sale_price >= purchase_price)
);
``
<img width="951" height="577" alt="image" src="https://github.com/user-attachments/assets/26c989c0-50c5-4279-84a4-b4d7d1636c93" />


#### ALTER TABLE: Adding columns

We can add colunns by altering the table.

``
ALTER TABLE companies 
ADD COLUMN phone VARCHAR(15);
``
<img width="1902" height="1186" alt="image" src="https://github.com/user-attachments/assets/8b35cf01-aebf-4b7d-b9ef-3b3e743c7775" />


`` 
ALTER TABLE companies
ADD COLUMN employee_count INT NOT NULL DEFAULT 1;
``
<img width="951" height="593" alt="image" src="https://github.com/user-attachments/assets/76b3f71e-f952-45bf-89f4-fc4fcda8fdc3" />



#### ALTER TABLE: Removing columns

The same as Adding you are just removing a col 

`ALTER TABLE companies DROP COLUMN phone;`

<img width="951" height="593" alt="image" src="https://github.com/user-attachments/assets/73942286-e328-4ea9-99d3-4f57ed97e0cd" />



#### ALTER TABLE: Renaming

A list of seeing our tables: 

<img width="1902" height="1186" alt="image" src="https://github.com/user-attachments/assets/5579c888-727f-4ace-9dc3-a759faf10ea0" />

`RENAME TABLE companies to suppliers;`

<img width="951" height="593" alt="image" src="https://github.com/user-attachments/assets/aaca56b5-a430-4a9d-bdde-399c091ff87f" />


`ALTER TABLE suppliers RENAME TO companies;`


``
ALTER TABLE companies
RENAME COLUMN name TO company_name;
``

<img width="1902" height="1186" alt="image" src="https://github.com/user-attachments/assets/08d5a17f-2dbd-43ed-ba8b-70b4055afa6f" />


#### ALTER TABLE: Modifying Columns 

``ALTER TABLE companies
MODIFY company_name VARCHAR(100) DEFAULT 'unknown';``

<img width="951" height="593" alt="image" src="https://github.com/user-attachments/assets/4dc1b0f8-76c2-4eba-b11b-88893a072bb7" />


``ALTER TABLE suppliers
CHANGE business biz_name VARCHAR(50);``


#### ALTER TABLE: Constraints

``
ALTER TABLE houses 
ADD CONSTRAINT positive_pprice CHECK (purchase_price >= 0);
``


`ALTER TABLE houses DROP CONSTRAINT positive_pprice;`


### One to Many and Joins

<img width="1084" height="828" alt="Screenshot 2026-02-16 at 00 32 40" src="https://github.com/user-attachments/assets/8f632622-d7ab-48b4-bb4c-fe80d64c0801" />


```
CREATE TABLE customers (
    id INT PRIMARY KEY AUTO_INCREMENT,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    email VARCHAR(50)
);
 
CREATE TABLE orders (
    id INT PRIMARY KEY AUTO_INCREMENT,
    order_date DATE,
    amount DECIMAL(8,2),
    customer_id INT,
    FOREIGN KEY (customer_id) REFERENCES customers(id)
);
 
INSERT INTO customers (first_name, last_name, email) 
VALUES ('Boy', 'George', 'george@gmail.com'),
       ('George', 'Michael', 'gm@gmail.com'),
       ('David', 'Bowie', 'david@gmail.com'),
       ('Blue', 'Steele', 'blue@gmail.com'),
       ('Bette', 'Davis', 'bette@aol.com');
       
       
INSERT INTO orders (order_date, amount, customer_id)
VALUES ('2016-02-10', 99.99, 1),
       ('2017-11-11', 35.50, 1),
       ('2014-12-12', 800.67, 2),
       ('2015-01-03', 12.50, 2),
       ('1999-04-11', 450.25, 5);
```

<img width="951" height="593" alt="image" src="https://github.com/user-attachments/assets/1c020579-7690-4665-9c0c-f4fa3eae207a" />


#### Cross Joins

```
SELECT id FROM customers WHERE last_name = 'George';
SELECT * FROM orders WHERE customer_id = 1;
 
 
SELECT * FROM orders 
WHERE customer_id = (SELECT id FROM customers WHERE last_name = 'George');
 
-- To perform a (kind of useless) cross join:
SELECT * FROM customers, orders;
```

#### Inner Joins

```
-- Our first inner join!
SELECT * FROM customers
JOIN orders ON orders.customer_id = customers.id;
 
SELECT first_name, last_name, order_date, amount FROM customers
JOIN orders ON orders.customer_id = customers.id;
 
-- The order doesn't matter here:
SELECT * FROM orders
JOIN customers ON customers.id = orders.customer_id;
```

```
SELECT 
    first_name, last_name, SUM(amount) AS total
FROM
    customers
        JOIN
    orders ON orders.customer_id = customers.id
GROUP BY first_name , last_name
ORDER BY total;
```

#### Left Join

Taking everything from the left side and any overlaps from the other table - customers is the left side, orders table would be the other data added seen aswell.
Good way to find if there's users who haven't placed orders. You'd have to see it with the overlap. 

```
SELECT 
    first_name, last_name, order_date, amount
FROM
    customers
        LEFT JOIN
    orders ON orders.customer_id = customers.id;
 
 
SELECT 
    order_date, amount, first_name, last_name
FROM
    orders
        LEFT JOIN
    customers ON orders.customer_id = customers.id;
```

Replacing null values by using IFNULL to make null values a 0 

```
SELECT 
    first_name, 
    last_name, 
    IFNULL(SUM(amount), 0) AS money_spent
FROM
    customers
        LEFT JOIN
    orders ON customers.id = orders.customer_id
GROUP BY first_name , last_name;
```


#### Right Join

Same as Left join but ir's the right table 

```
SELECT 
    first_name, last_name, order_date, amount
FROM
    customers
        RIGHT JOIN
    orders ON customers.id = orders.customer_id;
```

#### On delete Cascade

We can't delete foriegn ids you will get an error but you can add ON DELETE CASCADE to delete all instances of the data associated with that id so that you can remove a users data from a database. 

**NB! Very useful to have this part of your initial table creation.**

```
CREATE TABLE customers (
    id INT PRIMARY KEY AUTO_INCREMENT,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    email VARCHAR(50)
);
 
CREATE TABLE orders (
    id INT PRIMARY KEY AUTO_INCREMENT,
    order_date DATE,
    amount DECIMAL(8 , 2 ),
    customer_id INT,
    FOREIGN KEY (customer_id)
        REFERENCES customers (id)
        ON DELETE CASCADE
);
```

#### Exercise 

Students and papers tables. 
Students: id, first_name
Papers: title, grade, student_id
Null values for grades or titles should be missing and undefined. 

Then, add a use case where you can make an average for passing or failed and the pass mark is 75%.

Starter data: 

```
INSERT INTO students (first_name) VALUES 
('Caleb'), ('Samantha'), ('Raj'), ('Carlos'), ('Lisa');
 
INSERT INTO papers (student_id, title, grade ) VALUES
(1, 'My First Book Report', 60),
(1, 'My Second Book Report', 75),
(2, 'Russian Lit Through The Ages', 94),
(2, 'De Montaigne and The Art of The Essay', 98),
(4, 'Borges and Magical Realism', 89);
```

Code 
```
CREATE TABLE students (
    id INT PRIMARY KEY AUTO_INCREMENT,
    first_name VARCHAR(50)
);
 
 
CREATE TABLE papers (
    title VARCHAR(50),
    grade INT,
    student_id INT,
    FOREIGN KEY (student_id)
        REFERENCES students (id)
);
 
 
SELECT 
    first_name, title, grade
FROM
    students
        JOIN
    papers ON papers.student_id = students.id
ORDER BY grade DESC;
 
 
 
SELECT 
    first_name, title, grade
FROM
    students
        LEFT JOIN
    papers ON papers.student_id = students.id;
 
 
 
SELECT 
    first_name, IFNULL(title, 'MISSING'), IFNULL(grade, 0)
FROM
    students
        LEFT JOIN
    papers ON papers.student_id = students.id;
 
 
 
SELECT 
    first_name, IFNULL(AVG(grade), 0) AS average
FROM
    students
        LEFT JOIN
    papers ON students.id = papers.student_id
GROUP BY first_name
ORDER BY average DESC;
 
 
 
SELECT 
    first_name,
    IFNULL(AVG(grade), 0) AS average,
    CASE
        WHEN IFNULL(AVG(grade), 0) >= 75 THEN 'passing'
        ELSE 'failing'
    END AS passing_status
FROM
    students
        LEFT JOIN
    papers ON students.id = papers.student_id
GROUP BY first_name
ORDER BY average DESC;
```


### Many to Many 

> Examples
>
> Authers and books - many authers for scientific works for many diffent papers
>
> Posts and their tags - like blog posts
>
> Students and classes - many studnets take lots of classes and some of them can overlap


The example we work with for this section are tv shows and the reviewers like of like Rotton Tomato 

We use Union table 

Series data and reviewer data : they are connected with a reviews tables 

<img width="924" height="650" alt="image" src="https://github.com/user-attachments/assets/e62ce07c-0994-49fe-80e3-b5407c54c09f" />

<img width="924" height="650" alt="image" src="https://github.com/user-attachments/assets/81e3fa24-68e8-4f2d-a121-930520f488ef" />

```
CREATE TABLE reviewers (
    id INT PRIMARY KEY AUTO_INCREMENT,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL
);
 
CREATE TABLE series (
    id INT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(100),
    released_year YEAR,
    genre VARCHAR(100)
);
 
CREATE TABLE reviews (
    id INT PRIMARY KEY AUTO_INCREMENT,
    rating DECIMAL(2 , 1 ),
    series_id INT,
    reviewer_id INT,
    FOREIGN KEY (series_id)
        REFERENCES series (id),
    FOREIGN KEY (reviewer_id)
        REFERENCES reviewers (id)
);
 
INSERT INTO series (title, released_year, genre) VALUES
    ('Archer', 2009, 'Animation'),
    ('Arrested Development', 2003, 'Comedy'),
    ("Bob's Burgers", 2011, 'Animation'),
    ('Bojack Horseman', 2014, 'Animation'),
    ("Breaking Bad", 2008, 'Drama'),
    ('Curb Your Enthusiasm', 2000, 'Comedy'),
    ("Fargo", 2014, 'Drama'),
    ('Freaks and Geeks', 1999, 'Comedy'),
    ('General Hospital', 1963, 'Drama'),
    ('Halt and Catch Fire', 2014, 'Drama'),
    ('Malcolm In The Middle', 2000, 'Comedy'),
    ('Pushing Daisies', 2007, 'Comedy'),
    ('Seinfeld', 1989, 'Comedy'),
    ('Stranger Things', 2016, 'Drama');
 
 
INSERT INTO reviewers (first_name, last_name) VALUES
    ('Thomas', 'Stoneman'),
    ('Wyatt', 'Skaggs'),
    ('Kimbra', 'Masters'),
    ('Domingo', 'Cortes'),
    ('Colt', 'Steele'),
    ('Pinkie', 'Petit'),
    ('Marlon', 'Crafford');
    
 
INSERT INTO reviews(series_id, reviewer_id, rating) VALUES
    (1,1,8.0),(1,2,7.5),(1,3,8.5),(1,4,7.7),(1,5,8.9),
    (2,1,8.1),(2,4,6.0),(2,3,8.0),(2,6,8.4),(2,5,9.9),
    (3,1,7.0),(3,6,7.5),(3,4,8.0),(3,3,7.1),(3,5,8.0),
    (4,1,7.5),(4,3,7.8),(4,4,8.3),(4,2,7.6),(4,5,8.5),
    (5,1,9.5),(5,3,9.0),(5,4,9.1),(5,2,9.3),(5,5,9.9),
    (6,2,6.5),(6,3,7.8),(6,4,8.8),(6,2,8.4),(6,5,9.1),
    (7,2,9.1),(7,5,9.7),
    (8,4,8.5),(8,2,7.8),(8,6,8.8),(8,5,9.3),
    (9,2,5.5),(9,3,6.8),(9,4,5.8),(9,6,4.3),(9,5,4.5),
    (10,5,9.9),
    (13,3,8.0),(13,4,7.2),
    (14,2,8.5),(14,3,8.9),(14,4,8.9);
```


<img width="922" height="812" alt="image" src="https://github.com/user-attachments/assets/cb0d132a-ada6-4500-b347-1037d679d224" />

TV series challenge 1

```
SELECT 
    title, rating
FROM
    series
        JOIN
    reviews ON series.id = reviews.series_id;
```

<img width="922" height="812" alt="image" src="https://github.com/user-attachments/assets/20234a8b-8450-4d48-805e-a32b069990a7" />

TV series challenge 2

```
SELECT 
    title, ROUND(AVG(rating), 2) AS avg_rating
FROM
    series
        JOIN
    reviews ON series.id = reviews.series_id
GROUP BY title
ORDER BY avg_rating;
```

<img width="687" height="438" alt="image" src="https://github.com/user-attachments/assets/fb8c9476-224e-46a7-bacd-d3b12e6900e3" />


TV series challenge 3

```
SELECT 
    first_name, last_name, rating
FROM
    reviewers
        JOIN
    reviews ON reviews.reviewer_id = reviewers.id;
```

<img width="758" height="809" alt="image" src="https://github.com/user-attachments/assets/3ee314d1-75c8-4b9f-ba3b-1b40af86a545" />


TV series challenge 4

Using inner join - using Left & right joins 

```
SELECT 
    title AS unreviewed_series
FROM
    series
        LEFT JOIN
    reviews ON series.id = reviews.series_id
WHERE
    rating IS NULL;
 
 
SELECT 
    title AS unreviewed_series
FROM
    reviews
        RIGHT JOIN
    series ON series.id = reviews.series_id
WHERE
    rating IS NULL;
```
<img width="758" height="809" alt="image" src="https://github.com/user-attachments/assets/705e0b9f-119d-416b-9388-8dd78ea8060c" />


TV series challenge 5

Finding ave rathing for genres

```
SELECT 
    genre, ROUND(AVG(rating), 2) AS avg_rating
FROM
    series
        JOIN
    reviews ON series.id = reviews.series_id
GROUP BY genre;
```

<img width="554" height="332" alt="image" src="https://github.com/user-attachments/assets/57aa8c74-90cd-4288-90e9-bb78913784a7" />


TV series challenge 6

```
-- USING CASE 
SELECT 
    first_name,
    last_name,
    COUNT(rating) AS count,
    IFNULL(MIN(rating), 0) AS min,
    IFNULL(MAX(rating), 0) AS max,
    ROUND(IFNULL(AVG(rating), 0), 2) AS average,
    CASE
        WHEN COUNT(rating) >= 10 THEN 'POWERUSER'
        WHEN COUNT(rating) > 0 THEN 'ACTIVE'
        ELSE 'INACTIVE'
    END AS status
FROM
    reviewers
        LEFT JOIN
    reviews ON reviewers.id = reviews.reviewer_id
GROUP BY first_name , last_name;
 
-- USING IF 
SELECT 
    first_name,
    last_name,
    COUNT(rating) AS count,
    IFNULL(MIN(rating), 0) AS min,
    IFNULL(MAX(rating), 0) AS max,
    ROUND(IFNULL(AVG(rating), 0), 2) AS average,
    IF(COUNT(rating) > 0,
        'ACTIVE',
        'INACTIVE') AS status
FROM
    reviewers
        LEFT JOIN
    reviews ON reviewers.id = reviews.reviewer_id
GROUP BY first_name , last_name;
```

<img width="527" height="551" alt="image" src="https://github.com/user-attachments/assets/f899b5a7-3a53-4f2c-b93b-fc0134491e6a" />



TV series challenge 7

```
SELECT 
    title,
    rating,
    CONCAT(first_name, ' ', last_name) AS reviewer
FROM
    reviews
        INNER JOIN
    series ON reviews.series_id = series.id
        INNER JOIN
    reviewers ON reviews.reviewer_id = reviewers.id;
 
 
 
SELECT 
    title,
    rating,
    CONCAT(first_name, ' ', last_name) AS reviewer
FROM
    series
        INNER JOIN
    reviews ON reviews.series_id = series.id
        INNER JOIN
    reviewers ON reviews.reviewer_id = reviewers.id;
 
 
 
SELECT 
    title,
    rating,
    CONCAT(first_name, ' ', last_name) AS reviewer
FROM
    reviewers
        INNER JOIN
    reviews ON reviews.reviewer_id = reviewers.id
        INNER JOIN
    series ON reviews.series_id = series.id;
```

<img width="528" height="764" alt="image" src="https://github.com/user-attachments/assets/28d05de0-1895-441d-81e8-4270046bdcbe" />


### View, Models and more 

> Views
>
> a stored query so you don't have to rewite it over snd over.
> A virtial type table 


```
-- INSTEAD OF TYPING THIS QUERY ALL THE TIME...
SELECT 
    title, released_year, genre, rating, first_name, last_name
FROM
    reviews
        JOIN
    series ON series.id = reviews.series_id
        JOIN
    reviewers ON reviewers.id = reviews.reviewer_id;
 
-- WE CAN CREATE A VIEW:
CREATE VIEW full_reviews AS
SELECT title, released_year, genre, rating, first_name, last_name FROM reviews
JOIN series ON series.id = reviews.series_id
JOIN reviewers ON reviewers.id = reviews.reviewer_id;
 
-- NOW WE CAN TREAT THAT VIEW AS A VIRTUAL TABLE 
-- (AT LEAST WHEN IT COMES TO SELECTING)
SELECT * FROM full_reviews;
```

<img width="668" height="764" alt="image" src="https://github.com/user-attachments/assets/ad368000-b2a6-43ad-8017-6be241ab2e8e" />

Viewiing just let's you see the data and play with what you get not dlete or alter anything. 

```
CREATE VIEW ordered_series AS
SELECT * FROM series ORDER BY released_year;
 
CREATE OR REPLACE VIEW ordered_series AS
SELECT * FROM series ORDER BY released_year DESC;
 
ALTER VIEW ordered_series AS
SELECT * FROM series ORDER BY released_year;
 
DROP VIEW ordered_series;
```


> HAVING clauce 
>
> HAVING is used to filter groups that we get from GROUP BY
> 

```
SELECT 
    title, 
    AVG(rating),
    COUNT(rating) AS review_count
FROM full_reviews 
GROUP BY title HAVING COUNT(rating) > 1;
```


> WITH ROLLUP
>
> Only works with GROUP BY
>
> 

```
SELECT 
    title, AVG(rating)
FROM
    full_reviews
GROUP BY title WITH ROLLUP;
 
 
SELECT 
    title, COUNT(rating)
FROM
    full_reviews
GROUP BY title WITH ROLLUP;
 
 
SELECT 
    first_name, released_year, genre, AVG(rating)
FROM
    full_reviews
GROUP BY released_year , genre , first_name WITH ROLLUP;
```


#### SQL Modes Basics

If you want to change the basic conditions of the baground functions 

```
-- To View Modes:
SELECT @@GLOBAL.sql_mode;
SELECT @@SESSION.sql_mode;
 
-- To Set Them:
SET GLOBAL sql_mode = 'modes';
SET SESSION sql_mode = 'modes';
```

#### STRICT_TRANS_TABLES

Stands for strictly tranactional tables 
Strict mode controles missing values and how to manage the chars or out of range etc. 
Helpful from a baseline level when you want to change what throws errors. 

#### More Modes

Default enabled modes like full or only group by 

See the docs [here](https://dev.mysql.com/doc/refman/8.0/en/sql-mode.html) 👈

<img width="1174" height="743" alt="image" src="https://github.com/user-attachments/assets/f2fd2863-125c-445a-8c6a-888f9a453415" />

<img width="1174" height="931" alt="image" src="https://github.com/user-attachments/assets/e8d6b0e8-d7ae-4caf-8fb0-75d49205ad3f" />



### Window Functions

> "Before you begin this section about Window Functions, please be aware that you will not be able to run the code from this section in your Goorm environment.
> Goorm uses MySQL 5.7 by default, which does not support Window Functions.
> MySQL 8.0 and newer will support Window Functions but upgrading to 8.x on Goorm is not an easy task.
> If you would like to use Window Functions, then we recommend installing MySQL 8.x on your local machine (see Section 2 for installation instructions)."
>
> [Docs](https://dev.mysql.com/doc/refman/8.0/en/window-function-descriptions.html)

<img width="1209" height="779" alt="image" src="https://github.com/user-attachments/assets/93be36e8-ef76-4fc5-a00f-7b31724ccc13" />

I am currenlty running v8

<img width="1209" height="645" alt="image" src="https://github.com/user-attachments/assets/fbd42c5e-c280-4c79-9757-08bba16bf685" />

```
CREATE DATABASE windowfunctions;

CREATE TABLE employees (
    emp_no INT PRIMARY KEY AUTO_INCREMENT,
    department VARCHAR(20),
    salary INT
);
 
INSERT INTO employees (department, salary) VALUES
('engineering', 80000),
('engineering', 69000),
('engineering', 70000),
('engineering', 103000),
('engineering', 67000),
('engineering', 89000),
('engineering', 91000),
('sales', 59000),
('sales', 70000),
('sales', 159000),
('sales', 72000),
('sales', 60000),
('sales', 61000),
('sales', 61000),
('customer service', 38000),
('customer service', 45000),
('customer service', 61000),
('customer service', 40000),
('customer service', 31000),
('customer service', 56000),
('customer service', 55000);
 
 
SELECT emp_no, department, salary, AVG(salary) OVER() FROM employees;
 
SELECT 
    emp_no, 
    department, 
    salary, 
    MIN(salary) OVER(),
    MAX(salary) OVER()
FROM employees;
    
    
SELECT 
    emp_no, department, salary, MIN(salary), MAX(salary)
FROM
    employees;
```
<img width="899" height="777" alt="image" src="https://github.com/user-attachments/assets/d1d8c99a-2eb1-4b51-96c2-b92ae83cb249" />


#### PARTITION BY 

<img width="916" height="484" alt="image" src="https://github.com/user-attachments/assets/aae96ca6-3fbd-4b2f-98b2-b0a16d90b66b" />

```
SELECT 
    emp_no, 
    department, 
    salary, 
    AVG(salary) OVER(PARTITION BY department) AS dept_avg,
    AVG(salary) OVER() AS company_avg
FROM employees;
 
SELECT 
    emp_no, 
    department, 
    salary, 
    COUNT(*) OVER(PARTITION BY department) as dept_count
FROM employees;
 
SELECT 
    emp_no, 
    department, 
    salary, 
    SUM(salary) OVER(PARTITION BY department) AS dept_payroll,
    SUM(salary) OVER() AS total_payroll
FROM employees;
```

<img width="910" height="695" alt="image" src="https://github.com/user-attachments/assets/1bda1543-c9a8-44f5-b1df-2809ca825064" />


#### ORDER BY

<img width="916" height="484" alt="image" src="https://github.com/user-attachments/assets/e717b803-3993-40eb-803d-851ffe1179af" />


