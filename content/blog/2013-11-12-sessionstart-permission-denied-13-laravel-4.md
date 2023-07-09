---
author: Güngör Budak
date: '2013-11-12T12:37:00+03:00'
slug: sessionstart-permission-denied-13-laravel-4
tags:
- php
- laravel
- session_start
- permission denied
title: session_start() Permission denied (13) Laravel 4
year: '2013'
---

Solve it by running following lines:

    chmod -R 755 /path/to/your/laravel/directory
    chmod -R o+w /path/to/your/laravel/directory

And/or maybe:

    sudo chown -R www-data:user /path/to/your/laravel/directory
