---
author: Güngör Budak
date: '2013-11-19T18:29:17+03:00'
slug: install-spotify-on-ubuntu-1204
tags:
- ubuntu
- spotify
title: Install Spotify on Ubuntu 12.04
year: '2013'
---

Start `Software Sources` from Dash Home

Add following in `Other Sources` tab:

    deb http://repository.spotify.com stable non-free

Close `Software Sources`

Add Spotify repo key on Terminal:

    sudo apt-key adv –keyserver keyserver.ubuntu.com –recv-keys 94558F59

Install Spotify on Terminal:

    sudo apt-get update && sudo apt-get install spotify-client

Find Spotify in Dash Home

[Source](http://www.omgubuntu.co.uk/2013/01/how-to-install-spotify-in-ubuntu-12-04-12-10)
