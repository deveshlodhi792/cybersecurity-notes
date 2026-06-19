# Commands for mysql:-

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


  * 
