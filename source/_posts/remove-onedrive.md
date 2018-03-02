---
title: Win10彻底移除OneDrive
date: 2017-11-06
tag:
  - Win10
category: Windows
---

## 卸载OneDrive
- Windows菜单图标右键选择 `应用和功能`
- 找到OneDrive卸载

## 移除导航栏图标
- `Win+R`快捷键打开运行，输入`regedit`打开注册表
- `Ctrl+F`搜索`018D5C66-4533-4307-9B53-224DE2ED1FE6`
- 在搜到的内容对照下是不是`HKEY_CLASSES_ROOT\CLSID\{018D5C66-4533-4307-9B53-224DE2ED1FE6}`，一般是没问题的
- 展开这一项的ShellFolder，双击右侧Attributes，将值`f080004d`修改为`f090004d`
- 重启资源管理器