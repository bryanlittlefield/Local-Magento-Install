Local Magento Install
=====================

####Setup localhost
------------------------------------------

1. Install MAMP
2. Open Finder and hit " Command + Shift + G"
3. Enter "/etc"
4. Open up "hosts" file in your favorite editor
5. Copy line "127.0.0.1  localhost"
6. Change localhost to your desired domain name ex. magento.dev ( Note in order to install magento your domain name MUST have at least one ".")
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
