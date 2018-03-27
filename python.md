**Get All Files in a Folder:**

Use `os.walk()`. `os.walk()` generate tuples for each subdirectory. In each tuple, it is (dir name, [sub dir], [files]).

~~~python
import os
tuples = [x for x in os.walk(directory)]
files = []
for t in tuples:
	files += t[2]
~~~

**Handling Salted Hashed Passwords:**

~~~python
import hashlib, binascii, os
salt = binascii.hexlify(os.urandom(64)) #Return a string of n random bytes suitable for cryptographic use.
password = ''
keyHash = hashlib.pbkdf2_hmac('sha256', pwd, salt, 100000)
hashValue = binascii.hexlify(keyHash)
~~~

###Tornado

**Connect to MySQL:**

~~~python
import tornado.web
from tornado.options import define, options

define("mysql_host", default="127.0.0.1", help="database host")
define("mysql_port", default=11111, help="database port", type=int)
define("mysql_database", default="DATABASE", help="database name")
define("mysql_user", default="USER", help="database user")
define("mysql_password", default="PASSWORD", help="database password")

class Application(tornado.web.Application):
    def __init__(self):
	self.db = torndb.Connection(
            host=options.mysql_host, database=options.mysql_database,
            user=options.mysql_user, password=options.mysql_password)
~~~

**MySQL Prepared Statements:**

Execute Command:

~~~python
self.db.execute("INSERT INTO table VALUES (%s, %s, %s)", para1, para2, para3)
~~~

Query:

~~~python
data = self.db.query("SELECT col1, col2 \
                   FROM table \
                   WHERE para = %s", input)
~~~



