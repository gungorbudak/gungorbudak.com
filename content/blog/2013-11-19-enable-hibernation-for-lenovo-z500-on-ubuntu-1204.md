---
author: Güngör Budak
date: '2013-11-19T18:32:11+03:00'
slug: enable-hibernation-for-lenovo-z500-on-ubuntu-1204
tags:
- ubuntu
- lenovo
- hibernation
title: Enable Hibernation for Lenovo Z500 on Ubuntu 12.04
year: '2013'
---

Using Terminal add this file:

    sudo gedit /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla

This:

    [Re-enable hibernate by default]
    Identity=unix-user:*
    Action=org.freedesktop.upower.hibernate
    ResultActive=yes

Save & reboot

[Source](http://askubuntu.com/a/94963)
