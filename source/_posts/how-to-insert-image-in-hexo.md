---
title: 如何在Hexo博客中插入图片？
date: 2017-02-26
tag:
  - Hexo
category: VPS
---

## 前言
前两天在[《如何选择开源许可证？》](https://blog.otorb.com/2017/02/23/how-to-choose-free-software-licenses/)这篇博客中直接引用了阮一峰大神博客里的图片，但是大神博客并没有开启`HTTPS`，所以每次打开我这篇博客时，总会提示不安全，所以还是不要偷懒，自己管理博客图片吧。

在网上大概找了下，发现了[hexo-asset-image](https://github.com/CodeFalling/hexo-asset-image)方案，感觉还不错，使用这种方法的最大好处就是路径保证了和文章的一致，看起来不那么突兀。接下来介绍下如何接入：

## 接入流程

### 安装 `hexo-asset-image`
在Hexo博客文件夹下调用命令安装插件
```bash
npm install hexo-asset-image --save
```

### 修改 `_config.yml` 配置
打开根目录下的 `_config.yml` 文件，找到 `post_asset_folder` 属性，将其值改为 `true`。
**Tips:用 `vi` 的时候可以使用 `/` 进行搜索。**

### 引用图片
将图片保存到与日志同名的同级文件夹下，如：
```
MacGesture2-Publish
├── apppicker.jpg
├── logo.jpg
└── rules.jpg
MacGesture2-Publish.md
```
在日志中，使用 `![logo](logo.jpg)` 进行引用。

相关资料：
- [在 hexo 中无痛使用本地图片](http://www.tuicool.com/articles/umEBVfI)