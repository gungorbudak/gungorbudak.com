---
author: Güngör Budak
date: '2015-05-09T15:18:12+03:00'
slug: uploading-files-to-aws-using-sshscp
tags:
- amazon
- aws
- ssh
- scp
- upload
title: Uploading Files to AWS using SSH/SCP
year: '2015'
---

Here is a small command for uploading files to AWS through SSH's command `scp` (secure copy).

    scp -i path/to/your/key-pairs/file path/to/file/you/want/to/upload ubuntu@PUBLIC_DNS:path/to/the/destination
