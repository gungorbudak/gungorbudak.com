---
author: Güngör Budak
date: '2015-01-12T08:58:00.001+03:00'
slug: python-extend-append-elements-of-list
tags:
- list of elements
- append elements to a list
- extend
- python
- python methods
- append
title: 'Python: extend() Append Elements of a List to a List'
year: '2015'
---

When you append a list to a list by using <a href="https://docs.python.org/2/tutorial/datastructures.html#more-on-lists" target="_blank">append()</a> method, you'll see your list is going to be appended as a list:

```python
>>>l=["a"]
>>>l2=["a", "b"]
>>>l.append(l2)
>>>l
['a', ['a', 'b']]
```

If you want to append elements of the list directly without creating nested lists, use extend() method:

```python
>>>l=["a"]
>>>l2=["a", "b"]
>>>l.extend(l2)
>>>l
['a', 'a', 'b']
```
