---
author: Güngör Budak
date: '2017-02-03T14:53:15+03:00'
slug: make-a-shortcut-for-ssh-connections
tags:
- make
- shortcuts
- ssh
- connections
- config
title: Make a Shortcut for SSH Connections
year: '2017'
---

It could be really annoying to reenter the host name again and again if you are working over ssh and the host name is really long (i.e. `mistral.ii.metu.edu.tr`). Using this method, you can set a shorcut for the host name (i.e. `mistral`) and use it whenever you connect.


Open `~/.ssh/config` for editing:

    subl ~/.ssh/config

Add your host definition as follows:

    Host mistral
        HostName mistral.ii.metu.edu.tr
        User gbudak
