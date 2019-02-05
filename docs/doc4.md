---
id: doc4
title: MYSQL COMMAND
---

#### If you don't have MySQL installed on your droplet, you can quickly download it.

                                   sudo apt-get install mysql-server

#### Once you have MySQL installed on your droplet, you can access the MySQL shell by typing the following command into terminal:

                                   mysql -u root -p

#### You can quickly check what databases are available by typing:

                                   mysql> SHOW DATABASES;
                                   
#### DESCRIBE shows information on all columns of a table:

                                   mysql> DESCRIBE table_name;

#### Creating a database is very easy:

                                   mysql> CREATE DATABASE database_name;
                                   
#### In this case, for example, we will call our database "events."

                                   mysql> SHOW DATABASES;

#### Creating a table inside a database.Let’s open up the database we want to use:

                                   mysql> USE database_name ;

#### In the same way that you could check the available databases, you can also see an overview of the tables that the database contains.

                                   mysql> SHOW tables; 

#### Let’s create a new MySQL table:

                                   mysql> CREATE TABLE potluck (id INT NOT NULL PRIMARY KEY AUTO_INCREMENT, name VARCHAR(20),food VARCHAR(30),confirmed CHAR(1), signup_date DATE);

#### To select specific columns and rows by a certain condition using the WHERE clause:

                                   mysql> SELECT name FROM cats WHERE owner = 'Casey';

#### If needed, you can also delete rows from the table with the following command:

                                   mysql> DELETE from [table name] where [column name]=[field text];

#### Adding or deleting a column from a table.  Use an ALTER TABLE...ADD statement to add a column. You can use, for example, an AFTER clause to specify the location of the new column:

                                  mysql> ALTER TABLE cats ADD gender CHAR(1) AFTER name;
                       
#### Use ALTER TABLE...DROP to delete a column:

                                  mysql> ALTER TABLE cats DROP gender;

