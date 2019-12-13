---
title: Hadoop数据倾斜问题定位
date: 2019-12-23 09:56:51
categories: 
           - Bigdata
tags:
           - Bigdata,Hdfs,Balance
---
Hadoop集群Datanode数据倾斜，部分节点hdfs空间使用率达到90%以上，于是新增Datenode节点，并进行balance操作。

```shell
sh start-balancer.sh -threshold 5
```

如果需要提高blance的速度，将默认的balance速度从1MB/s增大到50MB/s

```shell
#set balance to 50M/s
hdfs dfsadmin -setBalancerBandwidth 52428800
```
