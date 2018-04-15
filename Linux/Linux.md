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

**Show All process:**

~~~bash
ps aux
~~~

`ps` will only show process currently opened by this bash

**Back up system:**

~~~bash
sudo su
cd /
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
~~~

restoring:

~~~bash
tar xvpfz backup.tgz -C /
makdir proc
mkdir lost+found
mkdir mnt
mkdir sys
~~~

**HOWTO: Restore GRUB**

**Use ssh key to encrypt and decrypt:**

Recommend: 
Use ssh to encrypt a AES key, and use AES key to encrypt file (RSA has a size limit on its encryption file)

~~~bash
# generate AES key:
openssl rand 32 -out aes.key
# Encrypt file:
openssl aes-256-cbc -in secret-file.txt -out secretfile.txt.enc -pass file:secret.key
# Encrypt AES key with pub key:
openssl rsautl -encrypt -oaep -pubin -inkey <(ssh-keygen -e -f recipients-key.pub -m PKCS8) -in secret.key -out secret.key.enc
~~~

Decrypt:

~~~bash
openssl rsautl -decrypt -oaep -inkey ~/.ssh/id_rsa -in secret.key.enc -out secret.key
openssl aes-256-cbc -d -in secretfile.txt.enc -out secretfile.txt -pass file:secret.key
~~~

**GNU Screen:**

~~~bash
screen #open screen
<ctr+a> : #horizontal split
<ctr+a> | #vertical split
<ctr+a> X #delete current
<ctr+a> tab #switch among screen
<ctr+a> c #create a shell in the screen
<ctr+a> Q #delete all screen except current one
~~~

