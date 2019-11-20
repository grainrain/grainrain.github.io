---
title: pip设置阿里云的镜像源
date: 2019-11-20 14:36:31
categories: 
           - Python
tags:
           - Python
           - Pip
---

## 1.Linux配置路径
```shell
vi ~/.pip/pip.conf
```
## 2.Windows配置路径
如果没有pip文件夹,那么新建pip
```shell
%HOMEPATH%\pip\pip.ini
```

```shell
[global]  
index-url=http://mirrors.aliyun.com/pypi/simple/  
[install]  
trusted-host=mirrors.aliyun.com
```
