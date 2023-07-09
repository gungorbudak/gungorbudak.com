---
author: Güngör Budak
date: '2015-05-06T22:58:18+03:00'
slug: how-to-get-path-to-or-directory-of-current-script
tags:
- r
- rscript
- path
- directory
- r programming
title: How to Get Path to or Directory of Current Script in R
year: '2015'
---

Use following code to get the path to or directory of current (running) script in R:

```r
scr_dir <- dirname(sys.frame(1)$ofile)
scr_path <- paste(scr_dir, "script.R", sep="/")
```

[Taken from SO](https://stackoverflow.com/questions/1815606/rscript-determine-path-of-the-executing-script/27090068#27090068)
