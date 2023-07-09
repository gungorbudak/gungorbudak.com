---
author: Güngör Budak
date: '2017-02-17T13:57:11+03:00'
slug: get-size-of-mysql-databases
tags:
- mysql
- database
title: Get Size of MySQL Databases
year: '2017'
---

Use below query in MySQL command prompt to get a table of databases and their sizes in MB.

    SELECT table_schema "DB Name", Round(Sum(data_length + index_length) / 1024 / 1024, 1) "DB Size in MB" FROM information_schema.tables GROUP BY table_schema;
