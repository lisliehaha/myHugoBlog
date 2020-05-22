---
title: "Mac装机"
date: 2020-05-22T17:39:13+08:00
lastmod: 2020-05-22T17:39:13+08:00
description: ""
tags: []
categories: []
author: "codecat"
keywords: []
comment: true
toc: true
autoCollapseToc: true
postMetaInFooter: false
hiddenFromHomePage: false
contentCopyright: true
reward: true
mathjax: true
mathjaxEnableSingleDollar: false
mathjaxEnableAutoNumber: false
---

### 1、安装软件无法打开 显示移到废纸篓

- 在系统的“安全与隐私”中允许“任何来源”，再打开终端。

* 在终端输入以下命令

  ``` sh
  sudo xattr -d com.apple.quarantine /Applications/xxxx.app
  ```

+ 重启APP即可

+++++



### 2、安装brew显示拒绝连接

运行以下命令：

``` sh
/bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"
```









