---
author: Güngör Budak
date: '2015-08-06T14:52:10+03:00'
slug: importerror-reportlab-version-21-is-needed
tags:
- xhtml2pdf
- reportlab
- django easy pdf
- python
- django
- mezzanine
title: 'ImportError: Reportlab Version 2.1+ is needed'
year: '2015'
---

Little bug in xhtml2pdf version 0.0.5. To fix:

    $ sudo nano /usr/local/lib/python2.7/dist-packages/xhtml2pdf/util.py

Change the following lines:

```python
if not (reportlab.Version[0] == "2" and reportlab.Version[2] >= "1"):
    raise ImportError("Reportlab Version 2.1+ is needed!")

REPORTLAB22 = (reportlab.Version[0] == "2" and reportlab.Version[2] >= "2")
```

With these lines:

```python
if not (reportlab.Version[:3] >= "2.1"):
    raise ImportError("Reportlab Version 2.1+ is needed!")

REPORTLAB22 = (reportlab.Version[:3] >= "2.1")
```
