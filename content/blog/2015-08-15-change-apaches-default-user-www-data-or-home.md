---
author: Güngör Budak
date: '2015-08-15T14:41:41+03:00'
slug: change-apaches-default-user-www-data-or-home
tags:
- apache2
- default user
- default home directory
title: Change Apache’s Default User www-data or Home Directory /var/www/
year: '2015'
---

I was getting errors from StarCluster run due to not being able to find `.starcluster` directory in `/var/www/`.

This directory has config file and log directories for StarCluster so without it, it can’t run.

To solve the issue, I set up my own user in Apache envvars instead of www-data which also changes default home directory to mine.

Edit following file with super user permissions:

    sudo nano /etc/apache2/envvars

Enter your username to following lines and save:

    export APACHE_RUN_USER=user
    export APACHE_RUN_GROUP=user

Restart the server:

    sudo service apache2 restart
