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


- Check which terminal you are using with this command:
    
    echo $SHELL
  
    
- If you get `/bin/zsh` then execute this line to configure MySQL:
    
    echo "export PATH=\${PATH}:/usr/local/mysql/bin" >> ~/.zshrc

    <img width="982" height="406" alt="image" src="https://github.com/user-attachments/assets/87411a85-f1be-46a4-92a2-5392681be005" />

    mysql -u root -p

