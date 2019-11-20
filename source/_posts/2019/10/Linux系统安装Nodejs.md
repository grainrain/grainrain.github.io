---
title: Linux系统安装Nodejs
date: 2019-10-31 09:49:08
categories: 
           - Web
tags:
           - Nodejs
---

##  文件下载
1.下载地址 : https://nodejs.org/en/download/

![](http://ningyylin.top/image/nodejs/nodejs_1_1.png)

2.选择合适环境的linux版本下载
<!-- more -->

![](http://ningyylin.top/image/nodejs/nodejs_1_2.png)
##  安装NODEJS

1.将安装包上传到指定位置(/usr/local/src/)目录，并解压
```shell
tar -xvf node-v12.13.0-linux-x64.tar.xz
```
2.重命名文件夹
```shell
mv node-v12.13.0-linux-x64.tar.xz
```
3.通过建立软连接变为全局
```shell
ln -s /usr/local/src/nodejs/bin/npm /usr/local/bin/
ln -s /usr/local/src/nodejs/bin/node /usr/local/bin/
```
4.检查是否安装成功，命令：node -v,npm -v
```shell
node -v

v12.13.0
```

```shell
 npm -v

 6.12.0
  ```