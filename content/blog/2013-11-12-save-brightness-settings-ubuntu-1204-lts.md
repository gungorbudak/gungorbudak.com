---
author: Güngör Budak
date: '2013-11-12T16:25:50+03:00'
slug: save-brightness-settings-ubuntu-1204-lts
tags:
- ubuntu
- brightness
title: Save Brightness Settings Ubuntu 12.04 LTS
year: '2013'
---

If your laptop starts with minimized or maximized brightness and you want to have a fixed default value for that do following:

Run terminal and type to get maximum brightness:

    cat /sys/class/backlight/acpi_video0/max_brightness

Now set the brightness as you want and run following which give you the value for current setting:

    cat /sys/class/backlight/acpi_video0/brightness

Edit `/etc/rc.local` to have that value as default after each reboot / start:

    sudo gedit /etc/rc.local

Add this line before `exit 0`:

    echo YOUR_VALUE > /sys/class/backlight/acpi_video0/brightness

Save `/etc/rc.local`

Now, the problem should be solved

[Source](http://askubuntu.com/questions/145314/how-to-save-brightness-settings)
