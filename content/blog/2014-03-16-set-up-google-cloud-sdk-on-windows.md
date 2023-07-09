---
author: Güngör Budak
date: '2014-03-16T19:17:00.001+03:00'
slug: set-up-google-cloud-sdk-on-windows
tags:
- cygwin
- cygwin 32-bit
- google cloud
- google cloud sdk
- openssh
- windows
- curl
- python
title: Set Up Google Cloud SDK on Windows using Cygwin
year: '2014'
---

Windows isn't the best environment for software development I believe but if you have to use it there are nice softwares to make it easy for you. Cygwin here will help us to use Google Cloud tools but installation requires certain things that you should be aware of beforehand.

**You'll need**

* <a href="https://www.python.org/download/" target="_blank">Python latest 2.7.x</a>
* <a href="https://developers.google.com/cloud/sdk/" target="_blank">Google Cloud SDK</a>
* <a href="http://cygwin.com/install.html" target="_blank">Cygwin 32-bit</a> (i.e. setup-x86.exe - note only this one works)
* <b>openssh</b>, <b>curl </b>and latest 2.7.x <b>python</b> Cygwin packages

Note: You'll need to select these packages during Cygwin installation. If you already have Cygwin 32-bit, just rerun the installer and make sure you select them all and later install all dependencies when you're asked.

**To set up**

* Open up Cygwin Terminal by right clicking and choosing "<b>Run as administrator</b>"
* Navigate to the folder that has "google-cloud-sdk" (what's in GCloud SDK download so move it somewhere like "C:\")
* Run `./google-cloud-sdk/install.sh`
* Follow instructions

Hopefully, you won't have any error and will get it working.

Last note is to be able to run GCloud tools in Cygwin Terminal, you'll always have to run it "<b>Run as administrator</b>", or you'll get "Permission denied" errors.
