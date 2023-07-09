---
author: Güngör Budak
date: '2015-04-13T11:38:41+03:00'
slug: how-to-clear-or-drop-db-table-of-a-django-app
tags:
- django
- clear
- tables
- django app
- sqlite3
- mysql
title: How to Clear (or Drop) DB Table of A Django App
year: '2015'
---

Let’s say you created a Django app and ran `python manage.py syncdb` and created its table. Everytime you make a change in the table, you’ll need to drop that table and run `python manage.py syncdb` again to update. And how you drop a table of a Django app:

    $ python manage.py sqlclear app_name | python manage.py dbshell

Drop tables of an app with migrations (Django >= 1.8):

    $ python manage.py migrate appname zero

Recreate all the tables:

    $ python manage.py syncdb

Easy!

[Taken from SO](https://stackoverflow.com/questions/2286276/how-do-i-drop-a-table-from-sqlite3-in-django/15444900#15444900)
