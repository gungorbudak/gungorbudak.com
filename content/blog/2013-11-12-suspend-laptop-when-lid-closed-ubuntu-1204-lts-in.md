---
author: Güngör Budak
date: '2013-11-12T10:08:12+03:00'
slug: suspend-laptop-when-lid-closed-ubuntu-1204-lts-in
tags:
- ubuntu
- lenovo
- suspend
title: Suspend Laptop When Lid Closed Ubuntu 12.04 LTS in Lenovo Z500
year: '2013'
---

I guess this is a bug. Although suspend is set in Power settings, it doesn’t suspend the laptop when its lid is closed.

To solve it, I’ve found a workaround on web. Here is how you implement it:

Generate folder if it’s not present:

    sudo mkdir /etc/acpi/local

Set its permissions:

    sudo chmod 755 /etc/acpi/local

Generate the script:

    sudo gedit /etc/acpi/local/lid.sh.post

Copy-paste the following:

```
#!/bin/bash

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
/usr/sbin/pm-suspend
fi
```

Make script executable

    sudo chmod +x /etc/acpi/local/lid.sh.post

After these operations, you should be able to suspend it when lid is closed and awaken back when it’s open. Note: it doesn’t show lock screen.

[Source](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/863834/comments/30)
