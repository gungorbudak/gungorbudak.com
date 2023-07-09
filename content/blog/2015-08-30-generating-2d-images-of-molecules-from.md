---
author: Güngör Budak
date: '2015-08-30T06:41:00.000+03:00'
slug: generating-2d-images-of-molecules-from
tags:
- 2d molecule
- molecule image
- 2d image
- open babel
- mol file
title: Generating 2D Images of Molecules from MOL Files using Open Babel
year: '2015'
---

<a href="http://openbabel.org/wiki/Main_Page" target="_blank">Open Babel</a> is a tool to work with molecular data in any way from converting one type to another, analyzing, molecular modeling, etc. It also has a method to convert MOL files into SVG or PNG images to represent them as 2D images.

Install Open Babel in Linux as following or go to their page for different operating systems

```bash
sudo apt-get install openbabel
```

Open Babel uses the same command to generate SVG or PNG and recognizes the file format using the given filename to as the output option `-O`. Also, it's possible to generate transparent images in SVG using option `-xb` with a value `none`. This doesn't work for PNGs. There are also other options, one of which is `--title` to write the name of the molecule to the image. Leave it blank if you don't want to see any title.

An example PNG generation from MOL file of benzene molecule.

```bash
gungor@gungors-mint ~/Desktop $ obabel benzene.mol -O benzene.png --title Benzene
1 molecule converted
```

![Benzene](/public/images/benzene.png)

To see all other options for available image formats, follow the <a href="http://open-babel.readthedocs.org/en/latest/FileFormats/Image_Formats.html" target="_blank">Open Babel documentation Image formats page</a>.
