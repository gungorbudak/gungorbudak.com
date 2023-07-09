---
author: Güngör Budak
date: '2015-06-13T09:45:56+03:00'
slug: setting-up-templates-and-python-scripts-for
tags:
- python
- django
- translation
- templates
- python scripts
- rosetta
title: Setting Up Templates and Python Scripts for Translation
year: '2015'
---

Templates need following template tag:

```python
{% raw %}{% load i18n %}{% endraw %}
```

Then, wrapping any text with

```python
{% raw %}{% trans "TEXT" %}{% endraw %}
```

will make it translatable via Rosetta Django application

In Python scripts, you need to import following library:

    from django.utils.translation import ugettext_lazy as _

Then wrapping any text with

```python
_('TEXT')
```

will make it translatable.
