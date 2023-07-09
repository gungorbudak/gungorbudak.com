---
author: Güngör Budak
date: '2013-11-19T21:12:00+03:00'
slug: install-apache2-php5-mysql-phpmyadmin-on
tags:
- ubuntu
- php
- apache2
- mysql
- phpmyadmin
title: Install Apache2, PHP5, MySQL & phpMyAdmin on Ubuntu 12.04
year: '2013'
---

First, install apache2:

    sudo apt-get install apache2

Then, for it to work:
    sudo service apache2 restart

For custom `www` folder:

    sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/www
    gksudo gedit /etc/apache2/sites-available/www

Change `DocumentRoot` and `Directory` directive to point to new location. For example, `/home/user/www/`

Save and see (link here clean URLs not working Laravel 4)

Make `www` default and disable `default`:

    sudo a2dissite default && sudo a2ensite www
    sudo service apache2 restart

Create new file in `www`

    echo "<b>Hello! It is working!</b>" > /home/user/www/index.html

Go to `http://localhost/`

If you get `403 Forbidden` error:

    chmod -R 755 /home/user/www/

Next, install php5:

    sudo apt-get install libapache2-mod-php5

Enable:

    sudo a2enmod php5

Restart apache2:

    sudo service apache2 restart

Check if it works:

    mkdir ~/www/test
    gedit /home/gungor/www/test/index.php

Enter:

```php
<?php echo "It's working"; ?>
```

Save

Go to `http://localhost/test/`

Next, install mysql:

    sudo apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql

Set a password 

Finally, install phpmyadmin:

    sudo apt-get install phpmyadmin

Select apache2 and then "Yes", enter your password

Open following and add the line `Include /etc/phpmyadmin/apache.conf`:

    gksudo gedit /etc/apache2/apache2.conf

Restart apache2:

    sudo service apache2 restart

Navigate to `http://localhost/phpmyadmin/`

After all these steps, you should be able to run PHP files on your Apache server and also use MySQL with phpMyAdmin

[More on Ubuntu Help](https://help.ubuntu.com/community/ApacheMySQLPHP)
