**Using pip**

~~~bash
easy_install pip
pip install --upgrade pip #upgrade pip or other package
~~~

**Install npm apps on Mac**

~~~bash
sudo npm install -g nyaovim --unsafe-perm=true --allow-root
~~~

**Uninstalled apps on Mac**

1. Binary and dock icons are located in `/Applications/`
2. Application support files are located in `~/Library/Application`
3. Support Caches can be found in `/Library/Caches/` and `~/Library/Caches`
4. Plugins are located in `~/Library/Address Book Plug-Ins/`
5. Library can be found in `~/Library/`
6. App preferences are located in `~/Library/Preferences/`
7. Crashes are found in `~/Library/Application Support/CrashReporter/`
8. App saved states are located in `~/Library/Saved Application State/`

**Calculate hash for a file**

~~~bash
md5 $PATHTOFILE
shasum -a 1 $PATHTOFILE
shasum -a 256 $PATHTOFILE
~~~