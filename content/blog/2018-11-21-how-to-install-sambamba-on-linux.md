---
author: Güngör Budak
date: '2018-11-21T11:00:00+03:00'
slug: how-to-install-sambamba-on-linux
tags:
- sambamba
- linux
- installation
- install
title: How to Install Sambamba on Linux
year: '2018'
---

Sambamba is a great utility to work with alignment file formats in bioinformatics such as BAM and CRAM. Follow below steps on any 64-bit Linux machine to install (this guide installs version `0.6.8` go to [Sambamba releases page](https://github.com/biod/sambamba/releases/) for the most up-to-date version):

**Create a softwares directory (optional but recommended)**

```
cd ~/
mkdir softwares
cd softwares/
```

**Download the static executable**

```
wget https://github.com/biod/sambamba/releases/download/v0.6.8/sambamba-0.6.8-linux-static.gz
```

**Unzip the package and rename the executable unpacked**

```
gunzip sambamba-0.6.8-linux-static.gz
mv sambamba-0.6.8-linux-static.gz sambamba-0.6.8
```

Keeping version in the name, can be useful.

**Change permissions to make it executable**

```
chmod +x sambamba-0.6.8
```

**Creating a symbolic link so you can call it anywhere**

```
ln -s /opt/sambamba-0.6.8 /usr/local/bin
```

This step requires superuser permission, if you don't have it just skip

**Verify installation**

```
sambamba-0.6.8 --version

sambamba 0.6.8 by Artem Tarasov and Pjotr Prins (C) 2012-2018
    LDC 1.10.0 / DMD v2.080.1 / LLVM6.0.1 / bootstrap LDC - the LLVM D compiler (0.17.4)


sambamba 0.6.8 by Artem Tarasov and Pjotr Prins (C) 2012-2018
    LDC 1.10.0 / DMD v2.080.1 / LLVM6.0.1 / bootstrap LDC - the LLVM D compiler (0.17.4)
```

or

```
./sambamba-0.6.8 --version

sambamba 0.6.8 by Artem Tarasov and Pjotr Prins (C) 2012-2018
    LDC 1.10.0 / DMD v2.080.1 / LLVM6.0.1 / bootstrap LDC - the LLVM D compiler (0.17.4)


sambamba 0.6.8 by Artem Tarasov and Pjotr Prins (C) 2012-2018
    LDC 1.10.0 / DMD v2.080.1 / LLVM6.0.1 / bootstrap LDC - the LLVM D compiler (0.17.4)
```

Notice the second verification is using `./` before executable which means it runs from the current working directory.

**All in one line**

```
wget https://github.com/biod/sambamba/releases/download/v0.6.8/sambamba-0.6.8-linux-static.gz && gunzip sambamba-0.6.8-linux-static.gz && mv /opt/sambamba-0.6.8-linux-static /opt/sambamba-0.6.8 && chmod +x /opt/sambamba-0.6.8 && ln -s /opt/sambamba-0.6.8 /usr/local/bin
```

Visit [Sambamba GitHub page](https://github.com/biod/sambamba) for more information.
