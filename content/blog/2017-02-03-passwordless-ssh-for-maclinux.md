---
author: Güngör Budak
date: '2017-02-03T14:47:28+03:00'
slug: passwordless-ssh-for-maclinux
tags:
- passwordless
- ssh
- mac
- linux
title: Passwordless SSH for Mac/Linux
year: '2017'
---

You don't have to enter the ssh password everytime you make a connection. Use below method to generate a key, copy it to the host you want to connect and connect anytime without entering your password.

Generate a keygen:

```bash
ssh-keygen
```

Copy the key to remote host:

```bash
ssh-copy-id root@linuxconfig.org
```
