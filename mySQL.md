**Installation on Raspberry Pi:**
	
	sudo apt-get install mysql-server python-mysqldb

**Check mySQL status:**
	
	/etc/init.d/mysql status
	
**Reset root psw w/o knowing it:**

Stop the current mysql server:

(if want to start or restart, just change *stop* to *start*, *restart*)
	
	sudo service mysqld stop
(?):
	
	sudo mkdir /var/run/mysqld; sudo chown mysql /var/run/mysqld
	
Login w/o asking password:
	
	sudo mysqld_safe --skip-grant-tables&
	
Log in as root:
	
	mysql -u root

Reset password:

	UPDATE mysql.user SET authentication_string = PASSWORD('NEWPSW') WHERE User = 'root' AND Host = 'localhost';
	
