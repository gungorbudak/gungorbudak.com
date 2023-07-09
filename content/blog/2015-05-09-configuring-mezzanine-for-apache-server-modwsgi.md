---
author: Güngör Budak
date: '2015-05-09T13:21:59+03:00'
slug: configuring-mezzanine-for-apache-server-modwsgi
tags:
- python
- django
- mezzanine
- mysql
- apache
- wsgi
- aws
- amazon
title: Configuring Mezzanine for Apache server & mod_wsgi in AWS
year: '2015'
---

Install [Mezzanine]({% post_url 2015-05-01-how-to-install-mezzanine-on-ubuntulinux-mint %}), [Apache server]({% post_url 2015-05-08-getting-started-with-your-aws-instance-and %}) and mod_wsgi:

    sudo apt-get install libapache2-mod-wsgi
    sudo a2enmod wsgi

Set up a MySQL database for your Mezzanine project

Read [my post on how to set up a MySQL database for a Mezzanine project]({% post_url 2015-05-09-how-to-set-up-a-mysql-database-for-a-mezzanine %})

Collect static files:

    python manage.py collectstatic

Configure your Apache server configuration for the project like following:

```
WSGIPythonPath /home/ubuntu/www/mezzanine-project

<VirtualHost *:80>
    #ServerName example.com
    ServerAdmin admin@example.com
    DocumentRoot /home/ubuntu/www/mezzanine-project
    WSGIScriptAlias / /home/ubuntu/www/mezzanine-project/wsgi.py
    Alias /static /home/ubuntu/www/mezzanine-project/static/

    <Directory /home/ubuntu/www/mezzanine-project>
        Order allow,deny
        Allow from all
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

Note: Replace `mezzanine-project` with the name of your project

Configure `wsgi.py` (I don’t know why but it needs this fix - complete script):

```python
from __future__ import unicode_literals
import os
import sys

PROJECT_ROOT = os.path.dirname(os.path.abspath(__file__))
sys.path.append(os.path.join(PROJECT_ROOT, ".."))
settings_module = "%s.settings" % PROJECT_ROOT.split(os.sep)[-1]
os.environ["DJANGO_SETTINGS_MODULE"] = settings_module

from django.core.wsgi import get_wsgi_application
application = get_wsgi_application()
```

Enable the site and restart the server:

    sudo a2ensite mezzanine-project.conf
    sudo service apache2 restart

Now, when you navigate to your AWS public DNS, your Mezzanine project should be running.

Source: [Vimmaniac](https://vimmaniac.com/blog/bangal/mezzanine-configuration-with-apache-mod-wsgi-on-ubuntu/)
