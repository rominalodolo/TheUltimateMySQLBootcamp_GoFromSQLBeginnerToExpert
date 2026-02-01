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
>> Removes trailing spaces not all the spaces in the words unless you specify

Example
```
SELECT INSERT('Hello Bobby', 6, 0, 'There'); 
 
SELECT LEFT('omghahalol!', 3);
 
SELECT RIGHT('omghahalol!', 4);
 
SELECT REPEAT('ha', 4);
 
SELECT TRIM('  pickle  ');
```

