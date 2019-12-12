# WordPress Install on Ubuntu 16.04
Install WordPress on Ubuntu 16.04

## Getting Started
These instructions will help you install and deploy WordPress using the command line in a few easy steps, provided you have all the prerequisites.

### Prerequisites
* Installed and configured Ubuntu 16.04 Server
* SSH open 

### Step 1: Connect to your server

With your credentials, connect to your Ubuntu server:

```
ssh user@ipaddress -p portnumber
```

### Step 2: Install the LAMP stack (Linux, Apache, MySQL, PHP)

First ensure you are getting the newest versions of packages and their dependencies:

```
sudo apt-get update
```

In this guide, we are installing the above software (Apache, MySQL, PHP) through one command, however they can also be installed individually:

```
sudo apt-get install lamp-server^
```

You will be prompted by a purple MySQL screen to create a password for "root" user. Create secure password, confirm and ensure you remember it.

### Step 3: Create a MySQL Database and User for WordPress

To get started, log into the MySQL root (administrative) account by using this command:

```
sudo mysql -u root -p
```
You will be prompted for the password you set for the MySQL root account when you installed the LAMP stack.

Next, you will create a database that WordPress can control. We will be using *wordpress* in this guide, however you can call this whatever you would like:

```
mysql> CREATE DATABASE wordpress;
```
The next step is to create a separate MySQL user account that you will use to operate on the new database created in the previous step. For this guide, we will be using the the user name *wordpressuser*. Ensure you choose a strong *password*:

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

### Step 4: Install WordPress

Change into a writable directory:

```
cd /tmp
```

Then download the lastest version of WordPress by typing:

```
sudo wget http://wordpress.org/latest.zip
```

In order to unzip the WordPress file, you will need to install "unzip" if you haven't done so previously:

```
sudo apt install unzip
```

Unzip the file into your servers root directory, which is /var/www/html by default:

```
sudo unzip -q latest.zip -d /var/www/html/
```

### Step 5: Configure the WordPress Directory 

Set permissions for WordPress by entering the following commands:

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

### Step 6: Restart Apache 

Restart Apache to implement the changes:

```
service apache2 restart
```

### Step 7: Complete Installation through Web Interface

Now that you have completed configuring the server, you can complete the installation through your browser. In your web browser, navigate to your IP address:

```
http://youripaddress/wordpress
```

If you are unsure of your IP address, type:

```
ifconfig
```

You will see the Wordpress install screen! Next, you will be promted to seleced your language, select a name for your site and choose a user name. 
