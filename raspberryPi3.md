**Raspberry Pi 3 Installation:**

Download image from here:
	
	https://www.raspberrypi.org/downloads/raspbian/
	
Use Etcher to burn image into microSD card.

Enable ssh

~~~bash
touch /boot/ssh
~~~

Check IP by log into router:

	http://routerlogin.net

ssh in raspberry pi; username: pi; password:raspberry

**Set-up WiFi for Pi:**

Check current network status:

~~~bash
sudo iwlist wlan0 scan
~~~

Modify the wireless conf. file:

~~~bash
sudo vi name /etc/wpa_supplicant/wpa_supplicant.conf
~~~
	
Append the wanted wifi connection to the end of file:

	network={
	    ssid="network"
	    psk="password"
	}

To not store password in plain text:

command line:

~~~bash
wpa_passphrase "network" "password"
~~~
	
Then append:

	network={
	    ssid="network"
		psk="sfskdlfajsdklfasjdklf;adkflsa
	}
Or use a more elegant way:

~~~bash
wpa_passphrase "testing" "testingPassword" | sudo tee -a /etc/wpa_supplicant/wpa_supplicant.conf > /dev/null
~~~

Reconfigure the network interface:

~~~bash
wpa_cli -i wlan0 reconfigure
~~~