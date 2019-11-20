---
title: Supervisor使用
date: 2019-11-12 09:16:13
categories: 
           - Linux
tags:
           - Supervisor
---
## Surpervisor介绍

+ 官方链接 [Supervisor](http://supervisord.org/ "Supervisor: A Process Control System").
+ 官方介绍 
```shell
Supervisor is a client/server system that allows its users to monitor and control a number of processes on UNIX-like operating systems.
```
## 环境说明
+ Python版本
```shell
2.7.5
```
+ 操作系统
```shell
Distributor ID:	CentOS
Description:	CentOS Linux release 7.6.1810 (Core) 
Release:	7.6.1810
Codename:	Core
```
## Surpervisor安装
### 1.Pip在线安装
```shell
pip install supervisor
```
 
### 2.发布包安装(centos为例)

+ yum install 的方式
```shell
yum install -y supervisor
```

+ easy_install的方式
```shell
yum install -y python-setuptools
easy_install supervisor
echo_supervisord_conf > /etc/supervisord.conf
```

## Surpervisor配置

###  默认supervisord配置

1.查看默认配置
```shell
echo_supervisord_conf
```
2.yum install方式安装 以下文件和目录会自动生成,如果没有,请自行创建
> /etc/supervisord.conf  
> /etc/supervisord.d

3.在 /etc/supervisord.d下创建conf和log两个目录,用于存储管理进程配置文件和日志文件
```shell
cd /etc/supervisord.d
mkdir conf log
```
4.修改/etc/supervisord.conf的[include]
```shell
vim /etc/supervisord.conf
```

5.将/etc/supervisord.d/conf目录所用应用配置包含进来

> [include]  
> files = supervisord.d/conf/*.conf


### 应用配置

`需要说明的是 在启动Nginx命令需要增加daemon off参数`

创建nginx.conf配置文件,内容如下
```shell
[program:nginx]
directory = /usr/local/nginx/sbin ; 程序的启动目录
command = /usr/local/nginx/sbin/nginx -g 'daemon off;' 
autostart = true     ; 在 supervisord 启动的时候也自动启动
startsecs = 5        ; 启动 5 秒后没有异常退出，就当作已经正常启动了
autorestart = true   ; 程序异常退出后自动重启
startretries = 3     ; 启动失败自动重试次数，默认是 3
user = root          ; 用哪个用户启动
redirect_stderr = true  ; 把 stderr 重定向到 stdout，默认 false
stdout_logfile_maxbytes = 20MB  ; stdout 日志文件大小，默认 50MB
stdout_logfile_backups = 20     ; stdout 日志文件备份数
; stdout 日志文件，需要注意当指定目录不存在时无法正常启动，所以需要手动创建目录（supervisord 会自动创建日志文件）
stdout_logfile = /etc/supervisord.d/log/nginx.log  ;日志统一放在log目录下
; 可以通过 environment 来添加需要的环境变量，一种常见的用法是修改 PYTHONPATH
; environment=PYTHONPATH=$PYTHONPATH:/path/to/somewhere
```

## Surpervisor启动

+ 方式一
```shell
# supervisord二进制启动
supervisord -c /etc/supervisord.conf
# 检查进程
ps aux | grep supervisord
```

+ 方式二
```shell
#!/bin/sh
#
# /etc/rc.d/init.d/supervisord
#
# Supervisor is a client/server system that
# allows its users to monitor and control a
# number of processes on UNIX-like operating
# systems.
#
# chkconfig: - 64 36
# description: Supervisor Server
# processname: supervisord

# Source init functions
. /etc/rc.d/init.d/functions

prog="supervisord"

prefix="/usr"
exec_prefix="${prefix}"
prog_bin="${exec_prefix}/bin/supervisord"
PIDFILE="/var/run/$prog.pid"

start()
{
       echo -n $"Starting $prog: "
       daemon $prog_bin --pidfile $PIDFILE -c /etc/supervisord.conf
       [ -f $PIDFILE ] && success $"$prog startup" || failure $"$prog startup"
       echo
}

stop()
{
       echo -n $"Shutting down $prog: "
       [ -f $PIDFILE ] && killproc $prog || success $"$prog shutdown"
       echo
}

case "$1" in

 start)
   start
 ;;

 stop)
   stop
 ;;

 status)
       status $prog
 ;;

 restart)
   stop
   start
 ;;

 *)
   echo "Usage: $0 {start|stop|restart|status}"
 ;;

esac
```

## supervisorctl&supervisord

###  supervisorctl
```shell
 supervisorctl stop programxxx，停止某一个进程(programxxx)，programxxx 为[program:beepkg] 里配置的值，这个示例就是 beepkg。  
 supervisorctl start programxxx，启动某个进程。  
 supervisorctl restart programxxx，重启某个进程。  
 supervisorctl status，查看进程状态。  
 supervisorctl stop groupworker ，重启所有属于名为 groupworker 这个分组的进程(start,restart 同理)。  
 supervisorctl stop all，停止全部进程，注：start、restart、stop 都不会载入最新的配置文件。  
 supervisorctl reload，载入最新的配置文件，停止原有进程并按新的配置启动、管理所有进程。  
 supervisorctl update，根据最新的配置文件，启动新配置或有改动的进程，配置没有改动的进程不会受影响而重启。  
```
### supervisord

supervisord，初始启动 Supervisord，启动、管理配置中设置的进程

## Supervisor控制台
在/etc/supervisord.conf中修改[inet_http_server]的参数，具体如下：
```shell
[inet_http_server]         ; inet (TCP) server disabled by default
port=*:9001        ; ip_address:port specifier, *:port for all iface
username=root             ; default is no username (open server)
password=xxxx               ; default is no password (open server)
```

修改后重启supervisor进程，在浏览器访问 http://<host-ip>:9001

参考：  
http://supervisord.org/  
https://blog.csdn.net/huwh_/article/details/80497790