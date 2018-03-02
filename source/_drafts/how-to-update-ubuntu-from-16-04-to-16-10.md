---
title: 如何从Ubuntu 16.04 LTS 升级到Ubuntu 16.10
date: 2017-02-16
tag:
  - VPS
  - Ubuntu
category: VPS
---

通过下面的指令检查下当前版本。
```
$ lsb_release -a
```


```bash
#[Update your system index & packages to latest version]
$ sudo apt-get update && apt-get upgrade

#[Perform Ubuntu OS version upgrade]
$ sudo do-release-upgrade
Checking for a new Ubuntu release
No new release found
```
We are in LTS version because of that, we didn’t get Ubuntu normal release. So, edit the file /etc/update-manager/release-upgrades and Change `Prompt=lts` to `Prompt=normal` shown below.

```bash
$ sudo nano /etc/update-manager/release-upgrades
Prompt=normal
```

```bash
$ sudo apt-get update
$ sudo do-release-upgrade
```
