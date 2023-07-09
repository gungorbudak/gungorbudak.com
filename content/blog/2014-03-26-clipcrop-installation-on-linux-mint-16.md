---
author: Güngör Budak
date: '2014-03-26T21:09:00.001+03:00'
slug: clipcrop-installation-on-linux-mint-16
tags:
- npm
- bwa
- node
- clipcrop
- install nodejs
- nodejs
- linux mint
- shrimp2
- install clipcrop
- nvm
- sam
title: ClipCrop Installation on Linux Mint 16 nvm, Node, npm Included
year: '2014'
---

<a href="https://github.com/shinout/clipcrop" target="_blank">ClipCrop</a> is a tool for detecting structural variations from SAM files. And it's built with <a href="http://nodejs.org/">Node.js</a>.

ClipCrop uses two softwares internally so they should be installed first.

Install <a href="http://compbio.cs.toronto.edu/shrimp/" target="_blank">SHRiMP2</a>

SHRiMP is a software package for aligning genomic reads against a target genome.

```bash
$ mkdir ~/software
$ cd ~/software 
$ wget http://compbio.cs.toronto.edu/shrimp/releases/SHRiMP_2_2_3.lx26.x86_64.tar.gz
$ tar xzvf SHRiMP_2_2_3.lx26.x86_64.tar.gz
$ cd SHRiMP_2_2_3
$ file bin/gmapper
$ export SHRIMP_FOLDER=$PWD 
```

Install <a href="http://bio-bwa.sourceforge.net/" target="_blank">BWA</a>

BWA is a software package for mapping low-divergent sequences against a large reference genome.

BWA requires zlib so install it first

```bash
$ sudo apt-get install zlib1g-dev
```

Download latest BWA software from SourceForge

```bash
$ cd ~/Downloads
$ tar xjvf bwa-0.7.7.tar.bz2
$ cd bwa-0.7.7
$ make
$ sudo mv ~/Downloads/bwa-0.7.7 /usr/local/bin
$ sudo ln -s /usr/local/bin/bwa-0.7.7 /usr/local/bin/bwa
$ sudo nano /etc/profile
```

Copy-paste this at the end the document

```
PATH="$PATH:/usr/local/bin/bwa"
```

Save it pressing CTRL + X, then Y and hit ENTER

Now, NVM and Node should be installed but before there are some dependencies.

```bash
$ sudo apt-get install build-essential
$ sudo apt-get install libssl-dev curl
```

Install <a href="https://github.com/creationix/nvm" target="_blank">NVM</a>

NVM is Node Version Manager and allows you to use different versions of Node.js 

```bash
$ git clone git://github.com/creationix/nvm.git ~/.nvm
$ source ~/.nvm/nvm.sh
$ nvm install v0.6.1
$ nvm use v0.6.1
Now using node v0.6.1 
```

This installation also sets up Node.js v0.6.1, check:

```bash
$ node -v
v0.6.1
```

To install ClipCrop we need one last thing which is NPM - Node Package Manager.

Install <a href="https://www.npmjs.org/" target="_blank">NPM</a>

```bash
$ sudo apt-get install -y python-software-properties python g++ make
$ sudo add-apt-repository ppa:richarvey/nodejs
$ sudo apt-get update
$ sudo apt-get install nodejs npm
$ node -v
v0.10.21 
```

This last step will also install a Node.js version but before using ClipCrop, using NVM, Node.js version will be set to v0.6.1 like this:

```bash
$ nvm use v0.6.1
Now using node v0.6.1 
```

If it says `No command 'nvm' found`:

```bash
$ source ~/.nvm/nvm.sh
```

Install <a href="https://github.com/shinout/clipcrop" target="_blank">ClipCrop</a>

```bash
$ cd ~ 
$ npm install clipcrop
$ cd ~/node_modules/clipcrop
$ npm link
```

Run

```bash
$ clipcrop
```

This will tell you how to use the package and what options it has. More is available <a href="https://github.com/shinout/clipcrop" target="_blank">here</a>. 

Some pages to refer

Installation notes for BWA version 0.7.5a-r405, <a href="http://www.vcru.wisc.edu/simonlab/bioinformatics/programs/install/bwa.htm">http://www.vcru.wisc.edu/simonlab/bioinformatics/programs/install/bwa.htm</a>

Installing Node.js using NVM on Ubuntu, <a href="http://achinth.com/post/58263924087/installing-node-js-using-nvm-on-ubuntu" target="_blank">http://achinth.com/post/58263924087/installing-node-js-using-nvm-on-ubuntu </a>

How to install node.js and npm in ubuntu or mint, <a href="http://developwithguru.com/how-to-install-node-js-and-npm-in-ubuntu-or-mint/">http://developwithguru.com/how-to-install-node-js-and-npm-in-ubuntu-or-mint/</a>

Installing Node.js via package manager, <a href="https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager">https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager</a>

npm documentation, <a href="https://www.npmjs.org/doc/">https://www.npmjs.org/doc/</a>
