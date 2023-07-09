---
author: Güngör Budak
date: '2015-05-08T10:41:02+03:00'
slug: aws-start-an-instance-and-connect-to-it
tags:
- amazon
- aws
- ssh
- chmod
- launch instance
title: AWS Start an Instance and Connect to it
year: '2015'
---

Go to EC2 management console

Create a new key-pair if necessary and download it

Launch an instance

Add HTTP security group for web applications over HTTP

Get public DNS

Change permissions on key-pair file:

```bash
chmod 400 path/to/your/file.pem
```

Connect:

```bash
ssh -i path/to/your/file.pem ubuntu@PUBLIC_DNS
```

Note: `ubuntu` is for connecting an Ubuntu 64 bit instance. It’s different for others
