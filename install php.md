# mysql
pkg install mysql56-server
vim /etc/rc.conf
	mysql_enable="YES"
service mysql-server start
mysql_secure_installation
	[empty]
	Y
	enter passwd
	Y
	Y
	Y
	Y
mysql -u root -p
	exit

# php
pkg install php73-mysqli
pkg install php73-pdo_mysql
pkg install php73-gd
pkg install php73-session
pkg install mod_php73

vim /usr/local/etc/apache24/httpd.conf
	<FilesMatch "\.php$">
    		SetHandler application/x-httpd-php
	</FilesMatch>
	<FilesMatch "\.phps$">
    		SetHandler application/x-httpd-php-source
	</FilesMatch>

# phpMyAdmin
pkg install phpMyAdmin-php73
mkdir phpMyAdmin
cp -r /usr/local/www/phpMyAdmin /usr/local/www/apache24/data/phpMyAdmin
cd /usr/local/www/apache24/data/phpMyAdmin
chmod 644 config.inc.php

pkg install zh-wordpress-zh_TW
cp -r /usr/local/www/wordpress-zh_TW /usr/local/www/apache24/data/wordpress
cd /usr/local/www/apache24/data/wordpress/
cp wp-config-sample.php wp-config.php

# wordpress
go to phpMyAdmin
	create db : wordpress
	create user : wordpress
	passwd : [generate]
	click the two checkboxes(about db)

vim wp-config.php
	:19 "database_name_here" -> "wordpress"
	:22 "username_here" -> "wordpress"
	:25 "password_here" -> [generate]

[ip]/wordpress
	~
	~
	[new password]
	[email]
	install wordpress
	login
