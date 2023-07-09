---
author: Güngör Budak
date: '2015-08-12T11:00:08+03:00'
slug: transfer-files-to-your-aws-s3-storage-in-linux
tags:
- aws
- amazon
- aws s3
- s3cmd
title: Transfer Files to Your AWS S3 Storage in Linux
year: '2015'
---

Uploading files to an AWS S3 storage can be difficult through the GUI with many files included or if your files are in a server where you don't have a GUI option. Use following tool to transfer files to an S3 bucket.

Download following tool and install:

    cd ~/Downloads
    git clone https://github.com/s3tools/s3cmd.git
    cd s3cmd/
    sudo python setup.py install

Next, execute following to create a configuration file to connect to your AWS S3 account:

    s3cmd --configure

And finally use the following command to transfer any directory to your bucket:

    s3cmd sync <path-to-folder> s3://<s3-bucket-name>

[More on installation, setup and usage of s3cmd](https://github.com/s3tools/s3cmd)
