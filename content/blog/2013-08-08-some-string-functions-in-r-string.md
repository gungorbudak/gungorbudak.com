---
author: Güngör Budak
date: '2013-08-08T10:43:00.000+03:00'
slug: some-string-functions-in-r-string
tags:
- regex
- perl
- python
- replace
- concatenate
- extract
- string functions
- r functions
- split
- r
- r programming
- php
- check
title: Some String Functions in R, String Manipulation in R
year: '2013'
---

I have programmed with Perl, Python, and PHP before, and string manipulation was more direct and easier in them than in R. But still there are useful functions for string manipulation in R. I'm not an expert in R but I've been dealing with it for a while and I've learned some good functions for this purpose.

**Concatenate strings**

Concatenation is done with *paste* function. It gets concatenated strings as arguments separated bu comma and also separator character(s). Default for separator character is one white space. It directly returns output as string and starting strings remain the same.

```R
str1 <- "Gungor"
str2 <- "Budak"
paste(str1, str2, sep="_") # Output: [1] "Gungor_Budak"
```

<a href="http://stat.ethz.ch/R-manual/R-devel/library/base/html/paste.html" target="_blank">More on the documentation for *paste*</a>

**Extract character(s) from strings**

This can be done with *substr* function. It gets string, start and stop indices for the extraction. It directly returns output as string and starting string remains the same.

```R
str1 <- "Gungor"
substr(str1, 1, 3) # Output: [1] "Gun"
```

<a href="http://stat.ethz.ch/R-manual/R-patched/library/base/html/substr.html" target="_blank">More on the documentation for *substr*</a>

**Split characters from strings**

One function is *strsplit* which gets string and the character(s) from which it will be split as arguments. It returns a list and a list of splits in that list. So, to get a direct list of splits. You can use *unlist*.

```R
str1 <- "Gungor"
unlist(strsplit(str1, "ng")) # Output: [1] "Gu" "or"
```

<a href="http://stat.ethz.ch/R-manual/R-patched/library/base/html/strsplit.html" target="_blank">More on the documentation for *strsplit*</a>

**Check if character(s) are present in strings**

Here, you can use *grep* functions. *grepl* takes pattern and string as arguments and returns TRUE if it matches and FALSE otherwise.

```R
str1 <- "Gungor"
grepl("A", str1) # Output: [1] FALSE
```

<a href="http://stat.ethz.ch/R-manual/R-patched/library/base/html/grep.html" target="_blank">More on the documentation for *grep*</a>

**Replace character(s) in strings**

*gsub* is the function I use for this. It takes pattern, replacement and string as arguments. It returns changed string directly.

```R
str1 <- "Gungor"
gsub("ng", "gn", str1) # Output: [1] "Gugnor"
```

<a href="http://stat.ethz.ch/R-manual/R-patched/library/base/html/grep.html" target="_blank">More on the documentation for *gsub*</a>

These are the ones I use most, but there are many more and I will be adding them to this post in the future.
