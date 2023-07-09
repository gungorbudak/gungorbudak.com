---
author: Güngör Budak
date: '2013-11-11T16:30:39+03:00'
slug: permission-issues-develop-laravel-4-on-ubuntu
tags:
- php
- laravel
- 403 forbidden
- permission denied
title: Permission Issues develop Laravel 4 on Ubuntu 12.04 LTS
year: '2013'
---

If your CSS or JS files don’t seem to load or you get `403 Forbidden` or `Permissions denied`, all you need to do is to run following on terminal:

    sudo chmod -R 755 /path/to/your/laravel/directory
