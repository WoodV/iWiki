**Get All Files in a Folder:**

Use `os.walk()`. `os.walk()` generate tuples for each subdirectory. In each tuple, it is (dir name, [sub dir], [files]).

~~~python
import os
tuples = [x for x in os.walk(directory)]
files = []
for t in tuples:
	files += t[2]
~~~

**url encode and decode**

~~~python
import urllib
import urlparse
d = {'a':'b', 'c':'d'}
s = urllib.urlencode(d) #s = 'a=b&c=d'
d1 = urlparse.parse_qs(s) #d1 = d
~~~

**Retrieve an element from a set without removing it**

~~~python
e = next(iter(s))
~~~

**Generate a random string**

~~~python
import string
import random
randomS = ''.join([random.choice(string.ascii_letters + string.digits) for n in xrange(8)]) #string.ascii_uppercase
~~~

**Handling Salted Hashed Passwords:**

~~~python
import hashlib, binascii, os
salt = binascii.hexlify(os.urandom(64)) #Return a string of n random bytes suitable for cryptographic use.
password = ''
keyHash = hashlib.pbkdf2_hmac('sha256', pwd, salt, 100000)
hashValue = binascii.hexlify(keyHash)
~~~

### [Tornado](http://www.tornadoweb.org/en/stable/guide/security.html?highlight=login)

**Using Secret Token to anti-XSRF:**

Within `settings` under `class Application(tornado.web.Application)`, set `xsrf_cookies=True`.

Then, within each form need to submit:

~~~
<form action="/new_message" method="post">
  {% module xsrf_form_html() %}
  <input type="text" name="message"/>
  <input type="submit" value="Post"/>
</form>
~~~

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

**Form Filds Validation:**

Use python [wtform](http://wtforms.readthedocs.io/en/stable/) and [wtforms-tornado](https://github.com/puentesarrin/wtforms-tornado) packages.

~~~bash
pip install wtform wtforms-tornado
~~~

~~~python
from wtforms import TextField
from wtforms.validators import Required, Email
from wtforms_tornado import Form

class SignUpForm(Form):
    email = TextField('Email', validators=[Required(), Email()])

class SignupHandler(BaseHandler):
    def get(self):
    	form = SignUpForm()
        self.render("signup.html", email=form.email)
	
    def post(self):
        form = SignUpForm(self.request.arguments)
        if form.validate():
            email = form.data['email']
	else:
            self.set_status(400)
            self.write(form.errors)
            return
~~~





