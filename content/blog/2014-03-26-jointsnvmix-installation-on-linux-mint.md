---
author: Güngör Budak
date: '2014-03-26T06:41:00.001+03:00'
slug: jointsnvmix-installation-on-linux-mint
tags:
- cython
- jointsnvmix
- ez_setup
- python
- pysam
- distribute
title: JointSNVMix Installation on Linux Mint 16 Cython, Pysam Included
year: '2014'
---

<a href="http://code.google.com/p/joint-snv-mix/" target="_blank">JointSNVMix</a> is a software package that consists of a number of tools for calling somatic mutations in tumour/normal paired NGS data.

It requires Python (>= 2.7), Cython (>= 0.13) and Pysam (== 0.5.0).

Python must be installed by default ona Linux machine so I will describe the installation of others and JointSNVMix.

Note this guide may become outdated after some time so please make sure before following all.

Install <a href="http://cython.org/" target="_blank">Cython</a>

You may need Python development headers for these Python packages so make sure you have them:

```bash
$ sudo apt-get update
$ sudo apt-get install python-dev
$ sudo apt-get install libevent-dev
```

To install Cython:

```bash
$ cd ~/Downloads
$ wget http://cython.org/release/Cython-0.20.1.tar.gz
$ tar xzvf Cython-0.20.1.tar.gz
$ cd Cython-0.20.1
$ sudo python setup.py install
```

Install <a href="http://code.google.com/p/pysam/" target="_blank">Pysam</a>

Pysam installation requires ez_setup that requires distribute.

To install <a href="https://pypi.python.org/pypi/distribute/0.7.3" target="_blank">distribute</a>:

```bash
$ cd ~/Downloads
$ wget https://pypi.python.org/packages/source/d/distribute/distribute-0.7.3.zip
$ unzip distribute-0.7.3.zip -d distribute-0.7.3
$ cd distribute-0.7.3
$ sudo python setup.py install
```

To install <a href="https://pypi.python.org/pypi/ez_setup" target="_blank">ez_setup</a>:

```bash
$ cd ~/Downloads
$ wget https://pypi.python.org/packages/source/e/ez_setup/ez_setup-0.9.tar.gz
$ tar xzvf ez_setup-0.9.tar.gz
$ cd ez_setup-0.9
$ sudo python setup.py install&nbsp; 
```

Ready to install Pysam now:

```bash
$ cd ~/Downloads
$ wget http://pysam.googlecode.com/files/pysam-0.5.tar.gz
$ tar xzvf pysam-0.5.tar.gz
$ cd pysam-0.5
$ sudo python setup.py install
```

Now, install JointSNVMix:

```bash
$ cd ~/Downloads
$ wget http://joint-snv-mix.googlecode.com/files/JointSNVMix-0.7.5.tar.gz
$ tar xzvf JointSNVMix-0.7.5.tar.gz
$ cd JointSNVMix-0.7.5
$ sudo python setup.py install
```

Run

```bash
$ jsm.py
usage: JointSNVMix [-h] {train,classify} ...
JointSNVMix: error: too few arguments
```

<a href="http://code.google.com/p/joint-snv-mix/wiki/running" target="_blank">Follow running guide</a> for all arguments and options.
