---
author: Güngör Budak
date: '2015-10-29T23:18:04+03:00'
slug: miclip-13-installation
tags:
- miclip
- r
- r programming
- install r package from source
title: MiClip 1.3 Installation
year: '2015'
---

MiClip is a CLIP-seq data peak calling algorithm implemented in R but currently it doesn’t show up in the CRAN but you can obtain it from the archive and install from the source or tar.gz file.

Download the tar.gz file:

    wget https://cran.r-project.org/src/contrib/Archive/MiClip/MiClip_1.3.tar.gz

Start R:

    R

Install dependencies:

```R
install.packages("moments")
install.packages("VGAM")
```

Finally install MiClip 1.3:

```R
install.packages("MiClip_1.3.tar.gz", repos = NULL, type="source")
```

Then you can test it by loading the package and viewing its help file.
