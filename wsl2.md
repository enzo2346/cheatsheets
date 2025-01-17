## Summary

**-> [Back to Index](./README.md)**

* [Wsl2 setup with Cntlm](#wsl2-setup-with-cntlm)

## Wsl2 setup with cntlm

1. Enable virtualization in your BIOS

2. In windows search, type turn windows features on or off and check the following boxes:

* Virtual Machine Platform
* Windows Subsystem for Linux

  Then restart your computer

3. Type the following in an administrator powershell to install wsl:

```
wsl --install
```

If, you already have a deprecated version of wsl, you can type the following:

```
wsl --update
```

6. Set wsl default to version 2:

```
wsl --set-default-version 2
```

7. Install your distribution (here Ubuntu) by executing the following:

```
wsl --install -d Ubuntu
```

Then download CNTLM on your windows machine from https://sourceforge.net/projects/cntlm/files/

8. Start wsl and install cntlm:

```
wsl
```
```
cd /mnt/to-download-dir
```
```
sudo dpkg -i cntlm_0.92.3-1ubuntu2_amd64.deb
```

9. Next, generate your authentication hashes (replace <your user> by your NT user name):

```
cntlm -H -u <your user> -d EMEA
```

10. Copy hash passntlmv2 and paste it in the following file:

```
sudo nano /etc/cntlm.conf
```

11. Fill the rest of the data of /etc/cntlm.conf with the data of your windows my_cntlm.ini file:

```
C:\Users\<user>\AppData\Local\Programs\<cntlm_folder>\my_cntlm.ini
```

12. Add at the end of .bashrc the following to start cntlm on startup (here we use the default port 3128)

```
sudo service cntlm start
export http_proxy=http://localhost:3128
export https_proxy=http://localhost:3128
```

13. Exit and restart

```
exit
```
```
wsl --shutdown
```
```
wsl
```

14. Update DNS resolution config file with nameservers IP adresses: 

```
sudo  nano  /etc/resolv.conf
```

15. Change the access rights of the file to

```
sudo chmod 444 /etc/resolv.conf
```

16. Next, restart Ubuntu as before.

17. Now the configuration can be tested with:

```
wget www.google.com && rm index.html && echo "SUCCESS"
```

If the result ends with "SUCCESS" then everything is set up corretcly.

[Back to top](#summary)