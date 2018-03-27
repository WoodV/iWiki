**Create private-public key pair and use them as ssh authenticator:**

Generate rsa key pair

(will create a folder /home/a/.ssh)

~~~bash
ssh-keygen -t rsa 
~~~

Create a ~/.ssh folder on the remote workstation

~~~bash
ssh b@B mkdir -p .ssh
~~~

Append public key to remote workstation

~~~bash
cat .ssh/id_rsa.pub | ssh name@server 'cat >> .ssh/authorized_keys'
~~~

Depends on ssh version, might still need to:

(Optional)

	.ssh/authorized_keys2
	.ssh to 700
	.ssh/authorized_keys2 to 640
	
**Unzip .tar or .tar.gz File:**

[to specific folder]

.tar

~~~bash
tar [-C /myfolder] -xvf yourfile.tar 
~~~

.tar.gz

~~~bash
tar [-C /myfolder] -zxvf yourfile.tar.gz 
~~~

**How to automatically choose defaults when running commands:**

*yes* command will repeatedly output a line with string input, therefore in these case it is like hitting enter for all choices.

~~~bash
yes "" | YOUR COMMAND
~~~

**Run sudo jobs in crontab:**

Use the root crontab instead of individual crontab:

~~~bash
sudo crontab
~~~