---
title: VPS安装小记(二) - 搭建Hexo博客
date: 2017-02-19
tag:
  - VPS
  - VPS安装小记
category: VPS
---

## 前言
最近把VPS重新安装了一次，依次对安装过程做了下记录，整理成该系列博文，以方便自己日后查阅。这是博文的第二篇，整个系列可以点击此TAG查看：[VPS安装小记](https://blog.otorb.com/tags/VPS安装小记/)。

客户端环境：Windows 10
服务器环境：Linode 1024 & LNMP 1.4
SSH客户端程序：Git Bash

## 安装Node.js
在 [Node.js](nodejs.org) 上有直接的安装包下载，解压设置环境变量即可，但还是建议使用包管理器更为方便。以下是Ubuntu16.10安装命令：
```
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install -y nodejs
```

其他系统的安装方法可以参考官方指南： [《Installing Node.js via package manager》](https://nodejs.org/en/download/package-manager/)

## 安装Hexo
安装Hexo过程很简单，具体细节可以查看[Hexo中文文档](https://hexo.io/zh-cn/docs/)。
```bash
npm install -g hexo-cli # 安装Hexo
hexo init blog          # 初始化Hexo到blog文件夹，blog参数可以不填，则为当前文件夹
hexo generate           # 或者是hexo g，根据博客文章生成网页
```

## 利用Git的Webhook实现自动发布的博客系统
每写一篇博客都得手动生成一次网页实在有点麻烦，但是网页会自动刷新就能省去很多工夫。
考虑过两个方案：
- 用DropBox、OwnCloud或者NextCloud同步`blog/source`文件夹，然后写个脚本监听文件夹的变化，一旦发生变化就执行`hexo g`命令
- 用Git管理`blog/source`文件夹，利用Git提交时产生的回调通知服务器执行命令
当然，最后我还是选择了后者。
