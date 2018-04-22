# mysql4pi
## Install MySQL and PHPMYADMIN on Rasbian OS
__1.__ If your packet manager is not up to date first of all update it
 
        sudo apt-get update
        
__2.__ If you haven't installed apache server, install it.
 
        sudo apt-get install -t stretch apache2
 
__3.__ Install php
 
        sudo apt-get install -t stretch php7.0
        sudo apt-get install -t stretch php7.0-mysql
        
 __4.__ Restart your Raspberry Pi
 
        sudo reboot
        
 __5.__ Install mysql server and mysql client
 
        sudo apt-get install -t stretch mysql-server mysql-client
        
 __6.__ Restart again
 
        sudo reboot
        
 __7.__ Install phpmyadmin
 
        sudo apt-get phpmyadmin
        
 When it ask you to select a server Select `apache2`. When it ask you to use dbconfig-common settings, say `Yes`
 Whet it ask you, select `your root pasword`
 
 __8.__ Configure Apache to work with PhpMyAdmin
 Open apache configuration file
 
        sudo nano /etc/apache2/apache2.conf
        
  Add that line at the bottom of the file
  
          Include /etc/phpmyadmin/apache.conf
          
  Reload apache
  
          sudo service apache2 reload
          
  __9.__ Increase Mysql security
  
          sudo mysql_secure_installation
         
  Enter `your root pasword` that you have set while installing PhpMyAdmin
  
  Change the root password Y/N (N) --Because you have set it already--
  
  Reload privilege tables now Y/N (Y)
  
   __10.__ Set all the privileges for the user `rooot`
   
          sudo mysql -u root -p
          Enter Password: 'your root password'
          GRANT ALL PRIVILEGES on *.* to 'root'@'localhost' IDENTIFIED BY 'your root password';
          FLUSH PRIVILEGES;
          
   __11.__ Pres Ctrl+c to quit from mariadb or type `\q`
   
   Then restart mysql server
          
          sudo service mysql restart
          
Then go to `http://yourip/phpmyadmin`
