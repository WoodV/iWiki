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

