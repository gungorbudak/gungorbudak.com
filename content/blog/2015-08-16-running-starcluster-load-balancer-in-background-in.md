---
author: Güngör Budak
date: '2015-08-16T00:06:27+03:00'
slug: running-starcluster-load-balancer-in-background-in
tags:
- starcluster
- loadbalancer
- run in background
- nohup
title: Running StarCluster Load Balancer in Background in Linux
year: '2015'
---

StarCluster loadbalancer command is regularly monitors the jobs in queue and it adds or removes nodes to the master node that is created beforehand to effectively complete the queue.

To run in in the background without killing it when the terminal closed:

    nohup starcluster loadbalance cluster_name >loadbalance.log 2>&1 &

or to keep standard output and standard error logs separate:

    nohup starcluster loadbalance cluster_name > loadbalance.access.log 2> loadbalance.error.log &

This will start the process and output the process ID (PID) which can be used to check or kill it. Also, the standard outputs and errors will be written into loadbalance.log file in current home directory.

Processes in Linux can be obtained with following command in Terminal:

    ps

To kill a process:

    kill <PID>
