**Create private-public key pair and use them as ssh authenticator:**

Generate rsa key pair

(will create a folder /home/a/.ssh)

	ssh-keygen -t rsa 

Create a ~/.ssh folder on the remote workstation

	ssh b@B mkdir -p .ssh

Append public key to remote workstation

	cat .ssh/id_rsa.pub | ssh name@server 'cat >> .ssh/authorized_keys'
	
Depends on ssh version, might still need to:

(Optional)

	.ssh/authorized_keys2
	.ssh to 700
	.ssh/authorized_keys2 to 640
	
**Unzip .tar or .tar.gz File:**

[to specific folder]

.tar

	tar [-C /myfolder] -xvf yourfile.tar 
.tar.gz

	tar [-C /myfolder] -zxvf yourfile.tar.gz 
	
