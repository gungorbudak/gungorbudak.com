---
author: Güngör Budak
date: '2015-07-01T12:18:05+03:00'
slug: djangomezzanine-content-translation-for-mezzanine
tags:
- python
- django
- mezzanine
- translation
title: Django/Mezzanine Content Translation for Mezzanine Built-in Applications
year: '2015'
---

As Mezzanine comes with additional Django applications such as pages, galleries and to translate their content, Mezzanine supports django-modeltranslation integration.

Install django-modeltranslation:

    pip install django-modeltranslation

Add following to the `INSTALLED_APPS` in `settings.py`:

```python
"modeltranslation",
```

And following in `settings.py`:

```python
USE_MODELTRANSLATION = True
```

Also, move mezzanine.pages to the top of other Mezzanine apps in `INSTALLED_APPS` in `settings.py` like so:

```python
"mezzanine.pages",
"mezzanine.boot",
"mezzanine.conf",
"mezzanine.core",
"mezzanine.generic",
"mezzanine.blog",
"mezzanine.forms",
"mezzanine.galleries",
"mezzanine.twitter",
"mezzanine.accounts",
"mezzanine.mobile",
```

Run following to create fields in database tables for translations:

    python manage.py sync_translation_fieldspython manage.py update_translation_fields

Also, migrations might be needed:

    python manage.py makemigrationspython manage.py migrate

And done.
