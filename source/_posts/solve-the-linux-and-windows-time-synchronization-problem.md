---
title: 解决Linux和Windows时间不同步问题
date: 2017-01-15
tag:
  - Linux
category: Linux
---

## 老方法
每次装完双系统之后，时间总是不同步，之前在网上看到过这个方法：
```
sudo gedit /etc/default/rcS
utc=yes 改成utc=no
```
然而新版本已经没用了，据说ubuntu16.04里面根本就没有utc这一项了……

## 新方法
### 确认Ubuntu时间
```
sudo apt-get install ntpdate
sudo ntpdate time.windows.com
```
先用这个命令确认下当前Ubuntu上的时间是无误的，当然如果你确定的话这句就可以不用执行了。

### 将时间同步到硬件上
```
sudo hwclock --localtime --systohc
```

## 相关文章
[windows10和ubuntu16.04双系统下时间不对的问题](http://www.cnblogs.com/qf19910623/p/5559514.html)
