## How to set up a wordpress server on EC2 

### Create AWS account
See details on [AWS website](http://aws.amazon.com/)

### Create an instance
See details on [AWS website](http://aws.amazon.com/)

### SSH into your instance

### Install the Apache Web Server
- To install the Apache Web Server, type:
```
yum install httpd
```
- Start the Apache Web Server:
```
service httpd start
```

### Install php
- To install PHP, type:
```
yum install php php-mysql
```
- Restart the Apache Web Server:
```
service httpd restart
```
- Create a page to test your PHP installation:
```
cd /var/www/html
vi test.php
```

### Install MySQL
- To install MySQL, type:
```
yum install mysql-server
```
- Start MySQL:
```
service mysqld start
```
- Create your “blog” database:
```
mysqladmin -uroot create blog
```
- Secure your database:
```
mysql_secure_Installation
```
- Answer the wizard questions as follows:
    - Enter current password for root: Press return for none
    - Change Root Password: Y
    - New Password: Enter your new password
    - Remove anonymous user: Y
    - Disallow root login remotely: Y
    - Remove test database and access to it: Y
    - Reload privilege tables now: Y 

### Install WordPress

- To install WordPress, type:
```
cd /var/www/html
wget http://wordpress.org/latest.tar.gz
tar -xzvf latest.tar.gz
```
- This will uncompress WordPress in its own “wordpress” directory. I like having WordPress in a separate directory, but would rather rename it to “blog”:
```
mv wordpress blog
```
- Create the WordPress wp-config.php file: 
```
cd blog
mv wp-config-sample.php wp-config.php
vi wp-config.php
```
- In `wp-config.php`, change:
```
define(‘DB_NAME’, ‘blog’);
define(‘DB_USER’, ‘root’);
define(‘DB_PASSWORD’, ‘YOUR_PASSWORD’);
define(‘DB_HOST’, ‘localhost’);
```

### Map IP Address and Domain Name