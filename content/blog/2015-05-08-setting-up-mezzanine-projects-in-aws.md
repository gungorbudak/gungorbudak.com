---
author: Güngör Budak
date: '2015-05-08T13:40:27+03:00'
slug: setting-up-mezzanine-projects-in-aws
tags:
- amazon
- aws
- mezzanine
- custom tcp
- ec2
title: Setting Up Mezzanine Projects in AWS
year: '2015'
---

Go to EC2 management console, Security groups and add a Custom TCP inbound rule with port 8000. Select "Anywhere" from the list.

Then follow [this to install Mezzanine]({% post_url 2015-05-01-how-to-install-mezzanine-on-ubuntulinux-mint %})

Above tutorial is also explains setting up a site record. Mezzanine default site record is `127.0.0.1:8000` which should be `0.0.0.0:8000` in our case. So, enter `0.0.0.0:8000` when you’re asked to enter a site record when you ru

    python manage.py createdb

Also, you might still need to provide this site record while running the development server:

    python manage.py runserver 0.0.0.0:8000

Next, visit following URL:

    http://http://ec2-XX-XX-XX-XX.us-west-2.compute.amazonaws.com:8000

You’ll see the server running in this URL.

Note: The URL is your public DNS given in the instance page.
