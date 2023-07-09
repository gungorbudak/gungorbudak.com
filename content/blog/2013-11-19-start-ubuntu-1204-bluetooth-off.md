---
author: Güngör Budak
date: '2013-11-19T19:07:07+03:00'
slug: start-ubuntu-1204-bluetooth-off
tags:
- ubuntu
- bluetooth
title: Start Ubuntu 12.04 Bluetooth Off
year: '2013'
---

On Terminal:

    sudo gedit /etc/rc.local

Add following before the line "exit 0"

```
rfkill block bluetooth
```

Save

[Source](http://askubuntu.com/a/2568)
