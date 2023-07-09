---
author: Güngör Budak
date: '2013-11-12T16:12:00+03:00'
slug: hotkeys-special-keys-volumebrightness-controls
tags:
- ubuntu
- lenovo
- volume controls
- brightness controls
title: Hotkeys (special keys) Volume/Brightness Controls Don't Work After Suspend
year: '2013'
---

What seems to solve this problem on Ubuntu 12.04 LTS (Lenovo Z500):

Open this file:

    sudo gedit /etc/default/grub

Modify the line as this:

    GRUB_CMDLINE_LINUX="noapic"

Close it and run the following:

    sudo update-grub

Restart your computer

[Source](http://www.kubuntuforums.net/showthread.php?60298-function-keys-change-after-suspend)
