---
author: Güngör Budak
date: '2015-09-16T07:44:00.000+03:00'
slug: install-rdkit-2015-03-build-on-ubuntu
tags:
- rdkit
- ubuntu
- boost
- python
- linux mint
title: Install RDKit 2015-03 Build on Ubuntu 14.04 / Linux Mint 17
year: '2015'
---

<a href="http://www.rdkit.org/" target="_blank">RDKit</a> is an open source toolkit for cheminformatics. It has <a href="http://www.rdkit.org/docs/Overview.html#functionality-overview" target="_blank">many functionalities</a> to work with chemical files.

![RDKit Logo](/public/images/rdkit-logo.png)

Follow the below guide to install RDKit 2015-03 build on an Ubuntu 14.04 / Linux Mint 17 computer. Since <a href="http://packages.ubuntu.com/trusty/python-rdkit" target="_blank">Ubuntu packages don’t have the latest RDKit for trusty</a>, you have to build RDKit from its source.

**Install Dependencies**

```bash
sudo apt-get install flex bison build-essential python-numpy cmake python-dev sqlite3 libsqlite3-dev libboost1.54-all-dev
```

**Download the Build**

```bash
cd /usr/local
sudo wget http://sourceforge.net/projects/rdkit/files/rdkit/Q1_2015/RDKit_2015_03_1.tgz
sudo tar -xzf RDKit_2015_03_1.tgz
sudo mv rdkit-Release_2015_03_1/ rdkit
cd rdkit/
sudo mkdir build
```

**Set Environment Variables**

```bash
vim ~/.bashrc
```

Enter following three lines at the end of .bashrc

```bash
export RDBASE="/usr/local/rdkit"
export PYTHONPATH="$RDBASE:$PYTHONPATH"
export LD_LIBRARY_PATH="$RDBASE/lib"
```

```bash
source ~/.bashrc
```

**Download InChi API**

Optional, remove the argument `-DRDK_BUILD_INCHI_SUPPORT=ON` in the next step if you skip.

```bash
cd $RDBASE/External/INCHI-API
sudo bash download-inchi.sh
```

**Build**

```bash
cd $RDBASE/build
sudo cmake -DRDK_BUILD_INCHI_SUPPORT=ON ..
sudo make
sudo make install
```

**Verify**

```python
python
>>> import rdkit
>>> rdkit.rdBase.rdkitVersion
'2015.03.1'
```

Please comment if you have any issue with this installation.
