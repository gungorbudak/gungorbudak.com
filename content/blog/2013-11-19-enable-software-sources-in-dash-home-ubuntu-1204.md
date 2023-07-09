---
author: Güngör Budak
date: '2013-11-19T18:19:01+03:00'
slug: enable-software-sources-in-dash-home-ubuntu-1204
tags:
- ubuntu
title: Enable Software Sources in Dash Home Ubuntu 12.04
year: '2013'
---

First copy the software sources desktop file to your local applications folder:

    mkdir -p ~/.local/share/applications
    cp /usr/share/applications/software-properties-gtk.desktop ~/.local/share/applications/

Edit the file & change the line `NoDisplay=true` to `NoDisplay=false`:

    gedit ~/.local/share/applications/software-properties-gtk.desktop

Save, logout and login

[Source](http://askubuntu.com/a/131464)
