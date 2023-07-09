---
author: Güngör Budak
date: '2015-06-12T15:07:34+03:00'
slug: django-rosetta-installation
tags:
- python
- django
- localization
- translation
- rosetta
title: Django Rosetta Installation
year: '2015'
---

Install SciPy:

    sudo apt-get install python-numpy python-scipy python-matplotlib ipython ipython-notebook python-pandas python-sympy python-nose

Install pymongo and nltk:

    sudo pip install pymongo
    sudo pip install nltk

Install Python MySQLdb:

    sudo apt-get install python-mysqldb

Install Rosetta:

    sudo pip install django-rosetta

Add following into `INSTALLED_APPS` in `settings.py`:

```python
"rosetta",
```

Add following into `urls.py`:

    url(r’^translations/’, include(‘rosetta.urls’)),

To also allow [language prefixes](https://docs.djangoproject.com/en/1.8/topics/i18n/translation/#language-prefix-in-url-patterns), change patters to `i18n_patterns` in `urls.py`:

```python
urlpatterns += i18n_patterns(
    ...
)
```
