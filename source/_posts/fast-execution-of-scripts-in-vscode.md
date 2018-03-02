---
title: 在VSCode中快速执行脚本
date: 2017-01-31
tag:
  - VSCode
category: VSCode
---

一般的Code Editor都能直接调用命令执行脚本，VSCode也不例外。
下面以lua为例，简单介绍下操作方法：

## 准备工作
- 安装好命令，确保命令在Path中

## 设置VSCode
- 新建一个文件夹，用作环境目录，并用VSCode打开
- 按`F1`，敲入`Configure Task runner`，回车执行，会自动打开`task.json`配置文件
- lua配置如下
```
{
    "version": "0.1.0",
    "command": "lua",
    "isShellCommand": true,
    "args": ["${file}"],
    "showOutput": "always"
}
```
- `command`顾名思义，是调用执行的命令，如`lua`、`python`、`ruby`等
- `args`是执行的命令后所调用的参数
    - 如果固定一个文件作为入口，直接填写文件名，如`"main.lua"`
    - 如果是想运行当前激活的窗口文件的话，填写`"${file}"`

## 执行脚本
- 方法一：按`F1`，敲入'Run Build Task'，回车执行
- 方法二：按默认快捷键`ctrl+shift+b`直接快速执行
    - 由于三个键位挤在一块，按起来比较费劲，所以也可以采用自定义快捷键
    - 依次打开`File` - `Preferences` - `keyboard shortcuts`，在右侧的`keybindings.json`中加入你要的快捷键，如
```
{
    "key": "alt+r",
    "command": "workbench.action.tasks.build",
    "when": "editorTextFocus"
}
```

这只是简单的执行，未来可以再看看`task.json`详细用法。
