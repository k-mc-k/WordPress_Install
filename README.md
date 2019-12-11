# WordPress-Install
WordPress install with Ubuntu 16.04

## Prerequisites
Please ensure you have installed and configured Ubuntu 16.04 Server with a static ip address, ssh open and an internet connection prior to starting this WordPress Install tutorial

```
sudo apt-get update
```

Test test test
```
sudo apt-get install lamp-server^
```

Purple MySQL screen, create secure password

```
sudo mysql -u root -p
```

```
mysql> CREATE DATABASE wordpress;
```

```
mysql> CREATE USER wordpressuser@localhost IDENTIFIED BY 'password';
```

```
mysql> GRANT ALL PRIVILEGES ON wordpress.* TO wordpressuser@localhost;
```

```
mysql> FLUSH PRIVILEGES;
```

```
mysql> exit
```

BYE.

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

Open browser
http://yourip/wordpress
