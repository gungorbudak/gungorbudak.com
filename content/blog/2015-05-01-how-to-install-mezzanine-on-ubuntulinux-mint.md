---
author: Güngör Budak
date: '2015-05-01T16:08:33+03:00'
slug: how-to-install-mezzanine-on-ubuntulinux-mint
tags:
- python
- django
- mezzanine
- virtualenv
- ubuntu
title: How to Install Mezzanine on Ubuntu/Linux Mint [Complete Guide]
year: '2015'
---

[Mezzanine](http://mezzanine.jupo.org/) is a CMS application built on Django web framework. The installation steps are easy but your environment may not just suitable enough for it work without a problem. So, here I'm going to describe complete installation from scratch on a virtual environment.

First of all, install virtualenv:

    $ sudo apt-get install python-virtualenv

Then, create a virtual environment:

    $ virtualenv testenv

And, activate it:
    $ cd testenv
    $ source bin/activate

Now, we have our environment set and it only has python and pip installed. Next, we are going to install some necessary packages:

    (testenv)$ sudo apt-get install python-pip python-dev python-setuptools python-imaging build-essential

Finally, we can install Mezzanine:

    (testenv)$ pip install mezzanine

To start your first Mezzanine project:
    (testenv)$ mezzanine-project mytest

And create DB and run:
    
    (testenv)$ cd mytest
    (testenv)$ python manage.py createdb
    (testenv)$ python manage.py runserver

Note that you'll be asked to create a super user when you're creating DB, do that.

After you ran your project, go to: `http://127.0.0.1:8000/`. You'll visit your first Mezzanine project on your favorite browser.
