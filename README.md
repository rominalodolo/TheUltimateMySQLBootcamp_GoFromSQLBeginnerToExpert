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


To list available databases:
``show databases;``
