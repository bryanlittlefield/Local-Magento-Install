Local Magento Install (Mac)
=====================

### **Step 1** Install MAMP
------------------------------------------
1. [Install MAMP](http://www.mamp.info/downloads/releases/MAMP_PRO.zip)
2. Once Installation is Completed Open Up Mamp and click Preferences
3. Navigate to "Ports" and click "Reset MAMP ports" and hit "Ok"
4. Click "Open Start Page" & Click "phpMyAdmin"
5. Once the page loads click "Database" at the top
6. Enter a Database name and click "Create"

#####You now have a Database setup with the Username: root and Password: root *(Note: by default MAMP will use "root" for the Username and Password you can change this is phpMyAdmin)*

### **Step 2** Setup localhost
------------------------------------------
1. Open Finder and hit " Command + Shift + G"
2. Enter "/etc"
3. Open up "hosts" file in your favorite editor
4. Copy & Paste line "127.0.0.1  localhost"
5. Change localhost to your desired domain name ex. magento.dev *(Note in order to install magento your domain name MUST have at least one ".")* 

##### It should Look Like This:
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
*Save and enter admin password* 

### **Step 3** Setup Virtual Host
------------------------------------------
1. Open Finder and hit " Command + Shift + G"
2. Enter "/Applications/MAMP/conf/apache"
3. Open up the "httpd.conf" file in your favorite text editor
4. Navigate to the very bottom and add the following and change "your-folder" and "yourdomain.dev" to match your setup

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

### **Step 4**  Download Magento
------------------------------------------
1. Navigate to your root directory setup in Virtual Host (/Applications/MAMP/htdocs/your-folder)
2. Download Magento from thier website or use the following script in Terminal:

```bash
curl -O http://www.magentocommerce.com/downloads/assets/1.7.0.2/magento-1.7.0.2.tar.gz
tar -zxvf magento-1.7.0.2.tar.gz 
mv magento/* magento/.htaccess . 
chmod -R o+w media var 
chmod o+w app/etc
rm -rf magento/ magento-1.7.0.2.tar.gz
find . -type f -exec chmod 644 {} \;
find . -type d -exec chmod 755 {} \;
```

### **Step 5**  Install Magento
------------------------------------------
*At this Point you have sucessfully Installed, Created a Database, Setup your localhost to point to a domain of your choice, Setup Virtual Host to tell that domian where to point, and Downloaded Magento into the directory that your Virtual Host is pointing to.*
##### Now it is time to Install Magento, 
If you did everything correctly you will be able to put the domain you created in the hosts file in your browsers URL bar and see the Magento Installlation Wizard! 
*(Note: If it is not showing up and you are sure you followed all the steps clear your browser cache and your DNS cache, refresh and you should be good to go)*


