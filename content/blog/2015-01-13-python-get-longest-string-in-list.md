---
author: Güngör Budak
date: '2015-01-13T08:17:00.003+03:00'
slug: python-get-longest-string-in-list
tags:
- longest string
- python
- string
- list
title: 'Python: Get Longest String in a List'
year: '2015'
---

Here is a quick Python trick you might use in your code.

Assume you have a list of strings and you want to get the longest one in the most efficient way.

```python
>>>l=["aaa", "bb", "c"]
>>>longest_string = max(l, key = len)
>>>longest_string
'aaa'
```
