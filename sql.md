# Commands(Statments) for mysql:-

* launching and setting up mysql - <mark>mysql -u root -p</mark>; then enter device password.
* to create database - <mark>CREATE DATABASE new_database_name;</mark>
* to show list of existing databases - <mark>SHOW DATABASES;</mark> [mysql, information_scheme, performance_scheme and sys are default databases of mysql to function].
* to select and interact with specific database - <mark>USE database_name;</mark>
* to remove database - <mark>DROP database_name;</mark>
* to create tables within an active(used) database-
  
      CREATE TABLE table_name (
      example_column1 data_type,
      example_column2 data_type,
      example_column3 data_type
      );
   **example application of command:-**
      
      CREATE TABLE book_inventory (
      book_id INT AUTO_INCREMENT PRIMARY KEY,
      book_name VARCHAR(255) NOT NULL,
      publication_date DATE
      );


  * <mark>SHOW TABLES;</mark> - to list the tables of currently active database (the database on which we used <mark>USE</mark> statment).
  * <mark>DESCRIBE or DESC book_inventory;</mark> - to know about coloumns and the data type of the table. Here is the example:
 <img width="869" height="355" alt="image" src="https://github.com/user-attachments/assets/d7d96dc6-7744-4411-96a8-17d62dae2255" />


  * <mark>ALTER</mark> + ADD statment:-
    -  to make change in dataset or alteration in table, like adding the coloums, , renaming column, changing and defining the data type in a coloumn, or removing a column.
    -  Syntatic order of statement-
<img width="865" height="135" alt="image" src="https://github.com/user-attachments/assets/54a48282-06a2-4998-b0d2-618d4dacefd5" />
 
 



  * <mark>DROP TABLE table_name;</mark> - to remove tables in a database.  

# CRUD Operations
* CRUD stands for Create, Read, Update, and Delete

## C - Create(Insert)
  
  * To create a new record in the table - "INSERT INTO"

    Example:-

  INSERT INTO books (id, name, published_date, description)
  VALUES (1, "Android Security Internals", "2014-10-14", "An In-Depth Guide to Android's Security Architecture");
  
  > In the example, we are inserting the record of a book in the table named 'books'.

## R - Read(Select)
  * To view contents of a table - "SELECT * FROM"

    example:-

    1. SELECT * FROM books;

    2. SELECT name,description FROM books;
   
       
    > In the example, the command will show all coloumns along with contents of a table. Here *(asterisk) symbol indicate to retrive all coloumns of the table. If we want to view only specific coloumns then we have to put name of coloumn in place of asterisk symbol, we can see this in example 2 above and ',' is used to retrive multiple coloumns.


    
