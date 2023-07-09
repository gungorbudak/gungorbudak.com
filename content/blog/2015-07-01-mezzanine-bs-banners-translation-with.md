---
author: Güngör Budak
date: '2015-07-01T14:30:29+03:00'
slug: mezzanine-bs-banners-translation-with
tags:
- python
- django
- mezzanine
- bsbanners
- bootstrap
- banners
- sliders
title: Mezzanine BS Banners Translation with django-modeltranslation
year: '2015'
---

Mezzanine BS Banners is a nice app for implementing Bootstrap 3 banners/sliders to your Mezzanine projects. The Banners model in BS Banners app has a title and its stacked inline Slides model has title and content for translation.

After [installing and setting up Django/Mezzanine translations]({% post_url 2015-07-01-djangomezzanine-content-translation-for-mezzanine %}):

Create a translation.py inside your Mezzanine project or your custom theme/skin application and copy/paste following lines:

```python
from modeltranslation.translator import translator
from mezzanine.core.translation import TranslatedSlugged, TranslatedRichText
from mezzanine_bsbanners.models import Banners, Slides


class TranslatedBanners(TranslatedSlugged):
   fields = ('title', )

class TranslatedSlides(TranslatedRichText):
   fields = ('title', 'content', )

translator.register(Banners, TranslatedBanners)
translator.register(Slides, TranslatedSlides)
```

For admin integration, create or use your existing admin.py in your Mezzanine project or your custom theme/skin application and copy/paste following lines:

```python
from django.contrib import admin
from mezzanine_bsbanners.admin import SlidesInline, BannersAdmin
from mezzanine_bsbanners.models import Banners, Slides
from modeltranslation.admin import TranslationAdmin, TranslationStackedInline


class TranslatedSlidesInline(SlidesInline, TranslationStackedInline):
   model = Slides

class TranslatedBannersAdmin(BannersAdmin, TranslationAdmin):
   inlines = [TranslatedSlidesInline, ]

   def formfield_for_dbfield(self, db_field, **kwargs):
       field = super(TranslatedBannersAdmin, self).formfield_for_dbfield(db_field, **kwargs)
       self.patch_translation_field(db_field, field, **kwargs)
       return field
       
admin.site.unregister(Banners)
admin.site.register(Banners, TranslatedBannersAdmin)
```

Run following to create fields in database tables for translations:

    python manage.py sync_translation_fields
    python manage.py update_translation_fields

This completes it.
