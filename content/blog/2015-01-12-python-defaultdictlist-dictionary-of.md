---
author: Güngör Budak
date: '2015-01-12T09:29:00.001+03:00'
slug: python-defaultdictlist-dictionary-of
tags:
- python
- dictionary of lists
- defaultdict
title: 'Python: defaultdict(list) Dictionary of Lists'
year: '2015'
---

Most of the time, when you need to work on large data, you'll have to use some dictionaries in Python. Dictionaries of lists are very useful to store large data in very organized way. You can always initiate them by initiating empty lists inside an empty dictionary but when you don't know how many of them you'll end up with and if you want an easier option, use `defaultdict(list)`. You just need to import it, first:

```python
from collections import defaultdict
```

And then initiate anywhere:

```python
dict = defaultdict(list)
```

You can always collect data in this way:

```python
dict["some_id"].append("some_value")
```
