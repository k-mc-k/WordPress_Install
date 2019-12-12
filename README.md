# WordPress Install on Ubuntu 16.04
WordPress install with Ubuntu 16.04

## Getting Started
These instructions will help you install and deploy WordPress using the command line in a few easy steps, provided you have all the prerequisites.

### Prerequisites
Please ensure you have installed and configured Ubuntu 16.04 Server, ssh open and an internet connection prior to starting

### Installing
```
sudo apt-get update
```

Test test test
```
sudo apt-get install lamp-server^
```

Purple MySQL screen, create secure password
### Step 2: Create a MySQL Database and User for WordPress

To get started, log into the MySQL root (administrative) account by using this command:

```
sudo mysql -u root -p
```
You will be prompted for the password you set for the MySQL root account when you installed the LAMP stack.

Next, you will create a database that WordPress can control. We will be using wordpress in this guide, however you can call this whatever you would like:

```
mysql> CREATE DATABASE wordpress;
```
The next step is to create a separate MySQL user account that you will use to operate on the new database created in the previous step. For this guide, we will be using the the user name wordpressuser. Ensure you choose a strong password:

```
mysql> CREATE USER wordpressuser@localhost IDENTIFIED BY 'password';
```
After creating the user account, you must give that account accessnto the database:

```
mysql> GRANT ALL PRIVILEGES ON wordpress.* TO wordpressuser@localhost;
```
Now that you have a database and user account, you need to flush the privileges so the current instance of MySQL knows about the changes you just made:

```
mysql> FLUSH PRIVILEGES;
```
Exit out of MySQL by typing:

```
mysql> exit
```

```
cd /tmp
```

```
sudo wget http://wordpress.org/latest.zip
```

```
sudo apt install unzip
```

```
sudo unzip -q latest.zip -d /var/www/html/
```

```
sudo chown -R www-data:www-data /var/www/html/wordpress
```

```
sudo chmod -R 755 /var/www/html/wordpress
```

```
sudo mkdir -p /var/www/html/wordpress/wp-content/uploads
```

```
sudo chown -R www-data:www-data /var/www/html/wordpress/wp-content/uploads
```

```
service apache2 restart
```

To verify your IP address
```
ifconfig
```

### Open your browser
http://youripaddress/wordpress

You will see the Wordpress install screen!
