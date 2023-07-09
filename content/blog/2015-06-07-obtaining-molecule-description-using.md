---
author: Güngör Budak
date: '2015-06-07T08:51:00.000+03:00'
slug: obtaining-molecule-description-using
tags:
- cheminformatics
- hba
- logp
- molecular weight
- hbd
- chiral centers
- clogp
- open babel
- pybel
- molecule
title: Obtaining Molecule Description using Open Babel / PyBel
year: '2015'
---

<a href="http://openbabel.org/wiki/Main_Page" target="_blank">Open Babel</a> is a great tool to analyze and investigate molecular data (.MOL, .SDF files). Its Python API is particularly very nice if you are familiar with Python already. In this post, I'll demonstrate how you can obtain molecule description such as molecular weight, HBA, HBD, logP, formula, number of chiral centers using PyBel.

**Installation**

```bash
$ sudo apt-get install openbabel python-openbabel
```

**Usage for MW, HBA, HBD, logP**

After reading .MOL file, we need to use `calcdesc` method with `descnames` argument for getting the descriptions. Getting formula is different, though.

```python
gungor@gungors-mint ~/Desktop $ python
Python 2.7.6 (default, Mar 22 2014, 22:59:56)
[GCC 4.8.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from pybel import *
>>> mol = readfile('mol', 'benzene.mol').next()
>>> desc = mol.calcdesc(descnames=['MW', 'logP', 'HBA1', 'HBD'])
>>> desc['formula'] = mol.formula
>>> print desc<br />{'HBA1': 0.0, 'HBD': 0.0, 'MW': 78.11184, 'logP': 1.6865999999999999, 'formula': 'C6H6'}
```

**Usage for Number of Chiral Centers**

This is not included in PyBel, or I couldn't find it but Open Babel comes with obchiral terminal command which returns the chiral atoms found in the molecules. We can parse this output to get the number of chiral centers.

```python
>>> from subprocess import Popen, PIPE
>>> p = Popen(['obchiral', 'brg_flap_1.mol'], stdout=PIPE, stderr=PIPE)
>>> stdout, stderr = p.communicate()
>>> chiral_num = stdout.count('Is Chiral')
>>> print chiral_num
1
```

So you can use above codes to get molecule description including molecular weight, HBA, HBD, logP, formula, number of chiral centers.
