? Which folders will preserve after app vm is closed?

/home, /usr/local, /rw

? What's the difference between gpk & yum?



? Can Qubes machine install dual boot os?

Yes, though there may be security vulnerabilities introduce by the other os. (Modifying BIOS)

? Which appvm has usb access?

? What are the qubes config files?


* GUI and audio config: /etc/qubes/guid.conf

* /rw/config/rc.local - script runs at VM setup

* /etc/profile.d

? Add another disk to qubes?

? What is RPM?

? How to install a package to a different directory?

FAILED ATTEMPT:
    * Download .rpm file
    * Use 'rpm -qpi file.rpm' to find out whether the package is relocatable or not.
    * Use 'rpm -i --prefix=preferpath file.rm' to install 

    Won't work, can't automatically install dependency.

? Install chrome?

    * Edit/etc/yum.repos.d/google-chrome.repo
    * Set enable=1
    * sudo dnf install google-chrome

? Copy files between vms?

    qvm-copy file [file]+

