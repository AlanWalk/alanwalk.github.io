---
title: VPS安装小记(一) - 利用SSH私钥实现无密访问VPS
date: 2017-02-19
tag:
  - VPS
  - VPS安装小记
category: VPS
---

## 前言
最近把VPS重新安装了一次，依次对安装过程做了下记录，整理成该系列博文，以方便自己日后查阅。这是博文的第一篇，整个系列可以点击此TAG查看：[VPS安装小记](https://blog.otorb.com/tags/VPS安装小记/)。

客户端环境：Windows 10
服务器环境：Linode 1024 & LNMP 1.4
SSH客户端程序：Git Bash

## 生成 `rsa key`
执行`ssh-keygen`生成公私钥，过程大致如下：
```bash
$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/Alan/.ssh/id_rsa):        # 私钥存储位置，如果是windows客户端，请输入全部路径，不要使用~/.ssh/
Enter passphrase (empty for no passphrase):                             # 建议回车跳过，不然每次连接时VPS用户密码可以省略，但得输入这个密码
Enter same passphrase again:
Your identification has been saved in /c/Users/Alan/.ssh/id_rsa.
Your public key has been saved in /c/Users/Alan/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:R0ShLCM6EXM468dLdy4l25wbLf1tnqhsLpPc9U5R/t0 Alan@DESKTOP-2AND0P2
The key's randomart image is:
+---[RSA 2048]----+
|  o..    .+.     |
|  o+   . o       |
|  .o. o o .     .|
|  .o . o .     o |
| .o.    S .   . .|
|  ..+ o o+  .  .+|
|   o o Xo+o. .. E|
|    . o X+o. +o. |
|       ..*+.o+=  |
+----[SHA256]-----+
```

## 上传 `public key`
执行`ssh-copy-id`将公钥上传到VPS上
```bash
$ ssh-copy-id -i /c/Users/Alan/.ssh/id_rsa root@139.162.120.244
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/c/Users/Alan/.ssh/id_rsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
root@139.162.120.244's password:                                        # 输入VPS用户密码

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh 'root@139.162.120.244'"
and check to make sure that only the key(s) you wanted were added.
```

## 利用SSH的Config管理SSH会话
这个时候再执行`ssh`命令，会发现已经不再需要密码。通过配置Config，我们能使登录过程更加简便。
```bash
$ vi ~/.ssh/config
```
配置内容如下，需要注意缩进。
```
Host otorb                          #别名
    HostName        otorb.com       #主机名
    Port            22              #端口(一般默认22)
    User            root            #用户名
    IdentityFile    ~/.ssh/id_rsa   #密钥文件的路径
```

## 测试结果
以后只要输入`ssh 别名`即可直接登录VPS了。
```bash
$ ssh otorb
```