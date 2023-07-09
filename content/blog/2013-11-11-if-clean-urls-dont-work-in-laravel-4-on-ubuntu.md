---
author: Güngör Budak
date: '2013-11-11T23:03:29+03:00'
slug: if-clean-urls-dont-work-in-laravel-4-on-ubuntu
tags:
- php
- laravel
- clean urls
title: If clean URLs don't work in Laravel 4 on Ubuntu 12.04 LTS
year: '2013'
---

`.htaccess` directions are correct, `mod_rewrite` is enabled but still you are getting `404 Not Found` errors...

You need to change `AllowOverride None` to `AllowOverride All` in `/etc/apache2/sites-available/default`.

Modified section in the file:

```
<Directory /home/user/www/>
    Options Indexes FollowSymLinks MultiViews
    AllowOverride All
    Order allow,deny
    allow from all
</Directory>
```
