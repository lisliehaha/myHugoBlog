---
title: "Excel数据导入Hive解决中文乱码"
date: 2019-07-19T18:55:35+08:00
lastmod: 2019-07-19T18:55:35+08:00
description: ""
tags: ["Hive"]
categories: ["大数据"]
author: "codecat"
keywords: ["Hive","Excel","中文乱码"]
comment: true
toc: true
autoCollapseToc: true
postMetaInFooter: true
hiddenFromHomePage: false
contentCopyright: false
reward: true
mathjax: true
mathjaxEnableSingleDollar: true
mathjaxEnableAutoNumber: false
---

Excel导hive： 

1. hive建表； 
2. 将Excel 导出另存为文本文档（制表符分隔）； 

3. 上传到Linux上：SecureCRT 可用rz命令； 

4. 更改编码格式：文件路径上执行 piconv -f gb2312 -t UTF-8 a.txt > c.txt （解决中文乱码） 

5. 导入Hive：hive上执行 load data local inpath ‘/path/c.txt’ into table table_name；