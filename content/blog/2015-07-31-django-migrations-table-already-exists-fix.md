---
author: Güngör Budak
date: '2015-07-31T14:12:11+03:00'
slug: django-migrations-table-already-exists-fix
tags:
- python
- django
- migrations
- table already exists
title: Django Migrations Table Already Exists Fix
year: '2015'
---

Fix this issue by faking the migrations:

    python manage.py migrate –fake <appname>

Taken from [this SO answer](https://stackoverflow.com/a/25925368/1597907)
