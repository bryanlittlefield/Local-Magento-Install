Local Magento Install on Mac
=====================

####Install MAMP
------------------------------------------
1. [Install MAMP](http://www.mamp.info/downloads/releases/MAMP_PRO.zip)
2. Once Installation is Completed Open Up Mamp and click Preferences
3. Navigate to "Ports" and click "Reset MAMP ports"


####Setup localhost
------------------------------------------
1. Open Finder and hit " Command + Shift + G"
2. Enter "/etc"
3. Open up "hosts" file in your favorite editor
4. Copy & Paste line "127.0.0.1  localhost"
5. Change localhost to your desired domain name ex. magento.dev ( Note in order to install magento your domain name MUST have at least one ".") It should Look Like This:

```bash
##
# Host Database
#
# localhost is used to configure the loopback interface
# when the system is booting.  Do not change this entry.
##
127.0.0.1  localhost
127.0.0.1	magento.dev
255.255.255.255	broadcasthost
::1             localhost 
fe80::1%lo0	localhost
```

7. Save and enter admin password

####Setup Virtual Host
------------------------------------------
1. Open Finder and hit " Command + Shift + G"
2. Enter "/Applications/MAMP/conf/apache"
3. Open up the "httpd.conf" file in your favorite text editor
4. Navigate to the very bottom and add the following:

```bash
NameVirtualHost *

<VirtualHost *>
DocumentRoot "/Applications/MAMP/htdocs"
ServerName localhost
</VirtualHost>

<VirtualHost *>
DocumentRoot "/Applications/MAMP/htdocs/your-folder"
ServerName yourdomain.dev
</VirtualHost>
```
