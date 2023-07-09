---
author: Güngör Budak
date: '2014-12-03T05:08:00.001+03:00'
slug: how-to-install-openpyxl-on-windows
tags:
- how to install openpyxl
- python excel
- python write excel
- windows
- python read excel
- python
- openpyxl
title: How to Install openpyxl on Windows
year: '2014'
---

openpyxl is a Python library to read/write Excel 2007 xlsx/xlsm files. To download and install on Windows:

<a href="https://pypi.python.org/pypi/openpyxl" target="_blank">Download it from Python Packages</a>

Then to install, extract the tar ball you downloaded, open up CMD, navigate to the folder that you extracted and run the following:

```
C:\Users\Gungor>cd Downloads\openpyxl-2.1.2.tar\dist\openpyxl-2.1.2\openpyxl-2.1.2
C:\Users\Gungor\Downloads\openpyxl-2.1.2.tar\dist\openpyxl-2.1.2\openpyxl-2.1.2>python setup.py install
```

It's going to install everything and will report any error. If there is nothing that seems like an error. You're good to go. Verify the installation by opening Python (command line) and running the following line in Python CMD:

```python
>>> from openpyxl import Workbook
>>>
```

<a href="https://openpyxl.readthedocs.org/en/latest/" target="_blank">openpyxl documentation</a> is a great place to start with it.
