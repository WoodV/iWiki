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

(?):
	
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
	
Restart the MySQL server normally:

~~~bash
sudo kill $(sudo cat /var/run/mysqld/mysqld.pid)
sudo systemctl start mysql
~~~
	

	
