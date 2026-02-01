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
