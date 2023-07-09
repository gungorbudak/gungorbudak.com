---
author: Güngör Budak
date: '2018-08-02T10:00:00+03:00'
slug: correct-installation-and-configuration-of-pip2-and-pip3
tags:
- python 2
- python 3
- pip
- python package manager
- install
title: Correct Installation and Configuration of pip2 and pip3
year: '2018'
---

You may have to keep both Python version, the old 2 and 3, at the same time due to your projects and they will require corresponding `pip` installation so you can separately install and maintain packages for both version.

There are multiple ways of installing `pip` to a system but the version configuration and setting the default version for `pip` executable can be tricky.

Below is the easiest solution I've found. This solution assumes you already have installed both Python versions and they can be executed as `python2` and `python3` for Python 2 and Python 3 respectively.

Check executables (optional):

```
$ python2 --version
Python 2.7.10
$ python3 --version
Python 3.6.4
```

Download the installer script:

```
$ wget https://bootstrap.pypa.io/get-pip.py
```

Now, if you want to use `pip3` as `pip`, you need to install `pip2` first, which I recommend.

Install `pip2`:

```
$ sudo python2 get-pip.py
```

Finally, install `pip3`:

```
$ sudo python3 get-pip.py
```

Now, check their versions:

```
$ pip2 --version
pip 18.0 from /Library/Python/2.7/site-packages/pip (python 2.7)
$ pip3 --version
pip 18.0 from /usr/local/lib/python3.6/site-packages/pip (python 3.6)
$ pip --version
pip 18.0 from /usr/local/lib/python3.6/site-packages/pip (python 3.6)
```

As you see now we have both, and the default `pip` points to Python 3.6 installation.

[Source from SO](https://stackoverflow.com/a/46466323/1597907)
