---
author: Güngör Budak
date: '2015-05-27T15:59:32+03:00'
slug: running-script-on-cluster-starcluster
tags:
- amazon
- aws
- csh
- shell
- script
- bash
- starcluster
- put
- sshmaster
title: Running Script on Cluster (StarCluster)
year: '2015'
---

Start a new cluster with the configuration file you modified:

    starcluster start cluster_name

Send the script to the running cluster:

    starcluster put cluster_name myscr.csh /home/myscr.csh

Run it using source:

    starcluster sshmaster cluster_name "source /home/myscr.csh >& /home/myscr.log"
