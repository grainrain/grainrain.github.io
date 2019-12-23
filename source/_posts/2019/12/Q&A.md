---
title: Support Q&A
date: 2019-12-24 10:27:19
categories: 
           - Azure
tags:
           - DataFactory
           - DataLake
---

## Azure HDInsight
+ MVP
```shell
1. 拨通雀巢VPN访问跳板机。
2. 登陆跳板机，在跳板机host文件里添加如下记录  
10.236.77.178  shenzhou-mvp-hdinsight-hbase.azurehdinsight.cn
3. 通过url  在浏览器输入
shenzhou-mvp-hdinsight-hbase.azurehdinsight.cn:8080访问hive view

```
+ DEV
```shell
本地host文件里添加如下记录，并通过雀巢VPN访问集群
10.236.80.81 gw1-stg-hb.mqtdsswgysfelkcmbgy1nohcwa.cx.internal.chinacloudapp.cn gw1-stg-hb  stg-hbase-shenzhou-hdinsight.azurehdinsight.cn

hive url:http://10.236.80.86:8080

```

+ STG
```shell
本地host文件里添加如下记录，并通过雀巢VPN访问集群
10.236.80.145 gw1-stg-sp.mqtdsswgysfelkcmbgy1nohcwa.cx.internal.chinacloudapp.cn gw1-stg-sp stg-spark-shenzhou-hdinsight.azurehdinsight.cn

hive url:http://10.236.80.86:8080
```

## Azure DataFactory
目前已经注册Azure DataFactory

+ MVP
  + shenzhou-mvp-datafactory01            [ATOS]
  + shenzhou-mvp-dscc-datafactory         
  + shenzhou-mvp-hand-datafactory
  + shenzhou-mvp-mdm-datafactory          [IBM]
  + shenzhou-mvp-paperless-datafactory    [xspeed]
  + shenzhou-mvp-qrcode-datafactory

+ DEV
  + shenzhou-dev-bypass-datafactory       [xspeed]
  + shenzhou-dev-dscc-datafactory       
  + shenzhou-dev-fc-datafactory
  + shenzhou-dev-hand-datafactory
  + shenzhou-dev-hr-datafactory           [xspeed]
  + shenzhou-dev-paperless-datafactory    [xspeed]
  + shenzhou-dev-qrcode-datafactory

+ STG
  + shenzhou-stg-bypass-datafactory
  + shenzhou-stg-datafactory              [ATOS]
  + shenzhou-stg-dscc-datafactory
  + shenzhou-stg-fc-datafactory
  + shenzhou-stg-hand-datafactory
  + shenzhou-stg-hr-datafactory
  + shenzhou-stg-paperless-datafactory
  + shenzhou-stg-qrcode-datafactory

  ## Azure DataLake
数据湖目录新规范
![](http://ningyylin.top/image/other/DL.png)
![](http://ningyylin.top/image/other/L3.png)
![](http://ningyylin.top/image/other/L5-L6.png)

+ MVP
  + https://shenzhoumvpdatalake.blob.core.chinacloudapi.cn/mvpdatalake (存放数据)
      + mvp
        + inbound
        + archive
        + error
        + process
        + qrcode
        + solutions

  + https://shenzhoumvpdatalake02.blob.core.chinacloudapi.cn/workspace (存放scripts)
    + scripts
      + dscc
      + fc
      + paperless
      + hr
      + qrcode
      + dscc

+ DEV
  + https://shenzhoudevdatalake.blob.core.chinacloudapi.cn/devdatalake  (存放数据)
      + dev
        + inbound
        + archive
        + error
        + process
        + qrcode
        + solutions

  + https://shenzhoudevdatalake02.blob.core.chinacloudapi.cn/workspace (存放scripts)
    + scripts
      + dscc
      + fc
      + paperless
      + hr
      + qrcode
      + dscc


                





