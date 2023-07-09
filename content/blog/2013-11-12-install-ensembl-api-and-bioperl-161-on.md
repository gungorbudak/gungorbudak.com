---
author: Güngör Budak
date: '2013-11-12T04:37:00.000+03:00'
slug: install-ensembl-api-and-bioperl-161-on
tags:
- ubuntu
- ensembl api
- install
- perl
- install bioperl
- api
- bashrc
- bioperl
- lib
- ensembl
- gedit
title: Install Ensembl API and BioPerl 1.2.3 on Your System
year: '2013'
---

I'm going to work on a project that requires lots of queries on Ensembl databases so I wanted to install Ensembl API to begin with. Since it's programmed in Perl, I will be using Perl in this project.

There is a nice <a href="http://www.ensembl.org/info/docs/api/api_installation.html" target="_blank">tutorial on Ensembl website for API installation</a>. Here I will describe some steps.

**1\. Download the API and BioPerl**

Go to Ensembl FTP <a href="ftp://ftp.ensembl.org/pub/">ftp://ftp.ensembl.org/pub/</a> and download "ensembl-api.tar.gz" or <a href="ftp://ftp.ensembl.org/pub/ensembl-api.tar.gz" target="_blank">click here</a>

Go to BioPerl downloads page <a href="http://bioperl.org/DIST/old_releases/">http://bioperl.org/DIST/old_releases/</a> download stable <strike>1.6.1</strike> 1.2.3 version (in tar.gz)

**2\. Place your in a source directory**

On Ubuntu, you can use the code below to generate your source folder, extract the downloads and then move the content to your source folder

```bash
mkdir ~/src
tar xvfz ensembl-api.tar.gz
mv ensembl ~/src/ensembl
mv ensembl-compara ~/src/ensembl-compara
mv ensembl-functgenomics ~/src/ensembl-functgenomics
mv ensembl-tools ~/src/ensembl-tools
mv ensembl-variation ~/src/ensembl-variation
tar xvfz BioPerl-1.2.3.tar.gz
mv BioPerl-1.2.3 ~/src/bioperl-1.2.3
```

**3\. Set your environment variables so tat Perl 5 can find the source directory and files inside**

```bash
gedit ~/.bashrc
```

Add following lines to at the end of .bashrc;

```bash
PERL5LIB=${HOME}/src/bioperl-1.2.3
PERL5LIB=${PERL5LIB}:${HOME}/src/ensembl/modules
PERL5LIB=${PERL5LIB}:${HOME}/src/ensembl-compara/modules
PERL5LIB=${PERL5LIB}:${HOME}/src/ensembl-variation/modules
PERL5LIB=${PERL5LIB}:${HOME}/src/ensembl-functgenomics/modules
export PERL5LIB
```

Then;

```bash
source ~/.bashrc
```

**4\. Check if the installation is successful**

```bash
perl ~/src/ensembl/misc-scripts/ping_ensembl.pl
```

If you get "Installation is good. Connection to Ensembl works and you can query the human core database", it's done.

For more information and the steps in installation on Mac and Windows <a href="http://www.ensembl.org/info/docs/api/api_installation.html" target="_blank">see the original tutorial</a>.
