---
author: Güngör Budak
date: '2015-06-27T03:16:00.000+03:00'
slug: convert-xlsxlsx-to-csv-in-bash
tags:
- csv
- libre office
- xls
- xls to csv
- excel
- xlsx to csv
- bash
- xlsx
title: Convert XLS/XLSX to CSV in Bash
year: '2015'
---

In most of the modern Linux distributions, Libre Office is available and it can be used to convert XLS or XLSX file(s) to CSV file(s) in bash.

For XLS file(s):

```bash
for i in *.xls; do libreoffice --headless --convert-to csv "$i"; done
```

For XLSX file(s):

```bash
for i in *.xlsx; do libreoffice --headless --convert-to csv "$i"; done
```

You may get following warning but it still works fine:

```bash
javaldx: Could not find a Java Runtime Environment!<br />Warning: failed to read path from javaldx
```

You'll see a standard output similar to following when the conversion is successful:

```bash
convert /home/gbudak/Downloads/cmap/cmap_instances_02.xls > /home/gbudak/Downloads/cmap/cmap_instances_02.csv using Text - txt - csv (StarCalc)
```

[Taken from an SO answer](http://stackoverflow.com/a/21651707/1597907).
