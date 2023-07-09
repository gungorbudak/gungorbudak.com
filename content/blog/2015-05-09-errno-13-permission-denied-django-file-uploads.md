---
author: Güngör Budak
date: '2015-05-09T15:16:00+03:00'
slug: errno-13-permission-denied-django-file-uploads
tags:
- python
- django
- permission denied
title: Errno 13 Permission denied Django File Uploads
year: '2015'
---

Run following command to give www-data permissions to static folder and all its content:

    cd path/to/your/django/project
    sudo chown -R www-data:www-data static/

Do this in your production server
