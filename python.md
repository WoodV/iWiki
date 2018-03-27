**Get All Files in a Folder:**

Use `os.walk()`. `os.walk()` generate tuples for each subdirectory. In each tuple, it is (dir name, [sub dir], [files]).

~~~python
import os
tuples = [x for x in os.walk(directory)]
files = []
for t in tuples:
	files += t[2]
~~~

