---
author: Güngör Budak
date: '2015-05-08T11:12:06+03:00'
slug: getting-started-with-your-aws-instance-and
tags:
- amazon
- aws
- apache2
title: Getting Started with Your AWS Instance and Installing and Setting Up an Apache
  Server
year: '2015'
---

Update and upgrade packages:

    sudo apt-get update
    sudo apt-get upgrade

Install Apache server:

    sudo apt-get install apache2

Set up a root folder in home folder and create an index file for testing:

    mkdir ~/www
    echo ‘Hello, World!’ > ~/www/index.html

Set up your virtual host:

    sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/000-www.conf
    sudo nano /etc/apache2/sites-available/000-www.conf

Modify `DocumentRoot` to point your "www" folder in home folder (e.g. /home/ubuntu/www)

And add following lines after `DocumentRoot` line:

```
<Directory "/home/ubuntu/www">
    Order allow,deny
    Allow from all
    Require all granted
</Directory>
```

Enable "www" site and restart Apache:

    sudo a2ensite 000-www
    sudo service apache2 restart

Finally, go to your public DNS, something like:

    http://ec2-XX-XX-XXX-XX.us-west-2.compute.amazonaws.com/

Sources: [SO](https://stackoverflow.com/questions/6959189/apache-virtualhost-403-forbidden/13923435#13923435), [DO Community](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts)
