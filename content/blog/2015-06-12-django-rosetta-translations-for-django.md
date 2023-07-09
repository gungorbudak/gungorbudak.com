---
author: Güngör Budak
date: '2015-06-12T15:20:33+03:00'
slug: django-rosetta-translations-for-django
tags:
- python
- django
- rosetta
- django-rosetta
- django translation
title: Django Rosetta Translations for Django Applications
year: '2015'
---

Make a directory called `locale/` under the application directory:

    cd app_name
    mkdir locale

Add the folder in `LOCAL_PATHS` dictionary in `settings.py`:

```python
LOCALE_PATHS = (
    os.path.join(PROJECT_ROOT, 'app_name', 'locale/'),
)
```

Run the following command to create PO translation file for the application:

    python ../manage.py makemessages -l tr -e html,py,txt
    python ../manage.py compilemessages

Option -l is for language, it should match your definition in `settings.py`:

```python
LANGUAGES = (
    ('en' _('English')),
    ('tr' _('Turkish')),
    ('it' _('Italian')),
)
```

Repeat the last step for all languages and the go to Rosetta URL to translate.
