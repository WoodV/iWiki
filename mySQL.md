**[Documentation](https://dev.mysql.com/doc/)**

**Web Tutorial about Syntax:**

	https://www.w3schools.com/sql/sql_syntax.asp


**Installation on Raspberry Pi:**
	
~~~bash
sudo apt-get install mysql-server python-mysqldb
~~~

**Check mySQL status:**

~~~bash
/etc/init.d/mysql status
~~~

**Reset root psw w/o knowing it:**

Stop the current mysql server:

(if want to start or restart, just change *stop* to *start*, *restart*)

~~~bash
sudo service mysqld stop
~~~

If /var/run/mysqld not exist:
	
~~~bash
sudo mkdir /var/run/mysqld; sudo chown mysql /var/run/mysqld
~~~
	
Login w/o asking password:

~~~bash
sudo mysqld_safe --skip-grant-tables&
~~~
	
Log in as root:

~~~bash
mysql -u root
~~~

Reset password:

~~~sql
UPDATE mysql.user SET authentication_string = PASSWORD('NEWPSW') WHERE User = 'root' AND Host = 'localhost';
~~~

Reload grant table:

~~~bash
mysqladmin flush-privileges
~~~
	
Restart the MySQL server normally:

~~~bash
sudo kill $(sudo cat /var/run/mysqld/mysqld.pid)
sudo systemctl start mysql
~~~
	
**Delete All data in a MySQL Table**

~~~sql
TRUNCATE TABLE tablename;
~~~

**Export Database from MySQL:**

~~~bash
mysqldump -u [username] -p [databasename] > [dumpfilename.sql]
~~~

**Import Database to MySQL:**

~~~bash
mysql -u username -p database_name < file.sql
~~~

**Adding User:**

[meaning]

~~~sql
CREATE USER "jianjian"@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON *[database].*[table] TO 'jianjian'@'localhost' WITH GRANT OPTION;

GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP
    ->     ON expenses.*
    ->     TO 'custom'@'localhost';
~~~

**Drop User:**

~~~sql
DROP USER 'jianjian'@'localhost';
~~~

**Change User Password:**

~~~sql
set password for 'webstore'@'localhost' = password('password');
~~~