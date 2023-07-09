---
author: Güngör Budak
date: '2014-02-24T11:28:00.000+03:00'
slug: how-to-convert-plink-binary-formats-to
tags:
- bim
- binary
- ms-dos
- format conversion
- plink
- windows
- map
- fam
- bed
- ped
- non-binary
title: How to Convert PLINK Binary Formats into Non-binary Formats
year: '2014'
---

<a href="http://pngu.mgh.harvard.edu/~purcell/plink/index.shtml" target="_blank">PLINK</a> is a whole genome association analysis toolset and to save time and space, you need to convert your data files to <a href="http://pngu.mgh.harvard.edu/~purcell/plink/data.shtml#bed" target="_blank">binary formats (BED, FAM, BIM)</a> but of course when you need to view the files, you have to convert them back to <a href="http://pngu.mgh.harvard.edu/~purcell/plink/data.shtml#ped" target="_blank">non-binary formats (PED, MAP)</a> to be able to open them in your text editor such as Notepad on Windows OS.

This operation is really easy. It requires PLINK of course, and the following line of code written to DOS window (Run -> type cmd; hit ENTER) in the directory of PLINK:

plink --bfile YOUR_BINARY_FILE --recode --out YOUR_NON-BINARY_FILE

First, you need to install PLINK if you don't have.

Note this tut is for Windows OS.

<a href="http://pngu.mgh.harvard.edu/~purcell/plink/download.shtml#download" target="_blank">Go to Download section</a> and download the correct version for your system. For Windows OS, it's MS-DOS.

Then, extract it to "C:" folder in your Computer. Make sure that you have plink.exe in the extracted folder. That's it.

To convert your files, start a new DOS window and navigate to your PLINK directory which is "C:\plink-1.07-dos". To do that type:

```
cd c:\plink-1.07-dos
```

[![PLINK conversion](/public/images/plink-conversion.png)](/public/images/plink-conversion.png)

When you changed the directory to PLINK's dir, you are ready to start conversion.

Not to confuse, it's better to create a folder inside "C:\plink-1.07-dos", say, "files". Then, move BED, FAM and BIM files inside this folder. Then with the code below, you can convert these files into non-binary forms.

```
plink --bfile files/YOUR_BINARY_FILE_NAME --recode --out files/YOUR_NON-BINARY_FILE_NAME
```

Change "YOUR_BINARY_FILE_NAME" with the name of your files (they have the same name except for the extension). And change "YOUR_NON-BINARY_FILE_NAME" with anything you want.

Next, hit ENTER and wait for the analysis. After it's done you'll see:

```
Analysis finished: CURRENT DATE
```

You can navigate to your files folder (C:\plink-1.07-dos\files) and see your non-binary forms PED and MAP.

More about PLINK and information for other operating systems can be found on <a href="http://pngu.mgh.harvard.edu/~purcell/plink/index.shtml" target="_blank">PLINK website</a>.
