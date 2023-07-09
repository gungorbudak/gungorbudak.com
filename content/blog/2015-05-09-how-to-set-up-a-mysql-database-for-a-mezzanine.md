---
author: Güngör Budak
date: '2015-05-09T13:21:10+03:00'
slug: how-to-set-up-a-mysql-database-for-a-mezzanine
tags:
- python
- django
- mezzanine
- mysql
- database
title: How to Set Up a MySQL Database for a Mezzanine Project
year: '2015'
---

Install MySQL server and python-mysqldb package:

    sudo apt-get install mysql-server
    sudo apt-get install python-mysqldb

Run MySQL:

    mysql -u root -p

Create a database:

    mysql> create database mezzanine_project;

Confirm it:

    mysql> show databases;

Exit:

    mysql> exit

Configure `local_settings.py`:

    cd path/to/your/mezzanine/projectnano local_settings.py

Like following:

```python
DATABASES = {
    "default": {
        "ENGINE": "django.db.backends.mysql",
        "NAME": "mezzanine_project",
        "USER": "root",
        "PASSWORD": "123456",
        "HOST": "",
        "PORT": "",
        }
    }
```

Note: Replace your password
