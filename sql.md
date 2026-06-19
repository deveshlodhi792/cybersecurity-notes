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
