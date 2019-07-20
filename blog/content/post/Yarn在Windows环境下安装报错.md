---
title: "Yarn在Windows环境下安装报错"
date: 2019-07-20T15:54:22+08:00
lastmod: 2019-07-20T15:54:22+08:00
description: ""
tags: ["yarn"]
categories: ["软件安装"]
author: "codecat"
keywords: ["windows","yarn"]
comment: true
toc: true
autoCollapseToc: false
postMetaInFooter: true
hiddenFromHomePage: false
contentCopyright: false
reward: true
mathjax: true
mathjaxEnableSingleDollar: false
mathjaxEnableAutoNumber: false
---

**问题：**

安装yarn后，在命令行输入yarn --version 报错

> Error: Could not create the Java Virtual Machine.

输入yarn install ，报错：

> 错误: 找不到或无法加载主类 install

**原因：**

环境变量冲突，在yarn的环境变量之前有默认的yarn环境变量。

**解决：**

打开环境变量设置界面，将yarn的环境变量上移到最前。

**测试：**

> $ yarn --version
> 1.17.3
