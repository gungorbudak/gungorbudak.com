---
author: Güngör Budak
date: '2017-02-14T15:31:56+03:00'
slug: replace-entire-column-with-a-number-in-bash
tags:
- awk
- replace column
- one-liner
title: Replace Entire Column with a Number in Bash
year: '2017'
---

Use below awk one-liner to replace all values in a column (5th column in example) with a value (1 in example).

    awk "{$5=1} {print}" filename > filename.replaced
