---
title: Git多账号配置
date: 2019-11-15 11:04:15
categories: 
           - Git
tags:
           - Git
           - Github
           - Gitee
           - Gitlab`
---

## 1.生成新的 SSH keys
```shell
ssh-keygen -t rsa -f ~/.ssh/id_rsa.github -C "xxxx@163.com"
ssh-keygen -t rsa -f ~/.ssh/id_rsa.gitee -C "xxxx@163.com"
ssh-keygen -t rsa -f ~/.ssh/id_rsa.gitlab -C "xxxx@163.net"
```
## 2.多账号必须配置 config 文件(重点)
```shell
$ touch ~/.ssh/config 
```
## 3.config 里需要填的内容

```shell
#Default gitHub user Self
Host github.com
HostName github.com
User git
IdentityFile ~/.ssh/id_rsa.github
	
# gitee
    Host gitee.com
    HostName gitee.com
    User git
    IdentityFile ~/.ssh/id_rsa.gitee
	
	
#Add gitLab user 
    Host git@DiEP-Infra
    HostName DiEP-Infra
    IdentityFile ~/.ssh/id_rsa.gitlab
```	
## 4.在 github 和 gitlab 网站添加 ssh

拷贝的~/.ssh/id_rsa.xxx.pub文件内容粘帖到 key 一栏，在点击 “add key” 按钮就可以了。

https://gitee.com/profile/sshkeys
https://github.com/settings/keys


## 5.测试是否连接成功
```shell
ssh -T git@github.com
ssh -T  git@gitLab-host
ssh -T git@gitee.com
```	