---
author: Güngör Budak
date: '2015-09-16T08:42:00.004+03:00'
slug: install-cairo-graphics-and-pycairo-on
tags:
- py2cairo
- cairo 1.14.2
- python
- cairo
- cairo graphics
- py2cairo 1.10.1
title: Install Cairo Graphics and PyCairo on Ubuntu 14.04 / Linux Mint 17
year: '2015'
---

<a href="http://cairographics.org/" target="_blank">Cairo</a> is a 2D graphics library implemented as a library written in the C programming language but if you'd like to use Python programming language, you should also install <a href="http://cairographics.org/pycairo/" target="_blank">Python bindings for Cairo</a>.

![Cairo Logo](/public/images/cairo-logo.png)

This guide will go through installation of Cairo Graphics library version 1.14.2 (most recent) and py2cairo Python bindings version 1.10.1 (also most recent).

**Install Cairo**

It's very easy with the following repository. Just add it, update your packages and install.

```bash
sudo add-apt-repository ppa:ricotz/testing
sudo apt-get update
sudo apt-get install libcairo2-dev
```

**Install py2cairo**

```bash
cd ~
git clone git://git.cairographics.org/git/py2cairo
```

**See what's your prefix**

```bash
python -c "import sys; print sys.prefix"
/usr
```

**Install dependencies**

```bash
sudo apt-get install automake pkg-config libtool
```

**Build**

```bash
cd ~/py2cairo
./autogen.sh --prefix=/usr
./configure
sudo make
sudo make install
```

**Verify**

```python
python
>>> import cairo
>>> cairo.cairo_version_string()
'1.14.2'
>>> cairo.version
'1.10.1'
```

Now, you can use up-to-date versions of these softwares in your computer.
