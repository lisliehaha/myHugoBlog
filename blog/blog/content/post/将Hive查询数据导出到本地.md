---
title: "将Hive查询数据导出到本地"
date: 2019-07-19T18:38:39+08:00
lastmod: 2019-07-19T18:38:39+08:00
description: ""
tags: ["Hive"]
categories: ["大数据"]
author: "codecat"
keywords: ["Hive"]
comment: true
toc: false
autoCollapseToc: false
postMetaInFooter: false
hiddenFromHomePage: false
contentCopyright: false
reward: false
mathjax: true
mathjaxEnableSingleDollar: false
mathjaxEnableAutoNumber: false
---

1.在Hive上执行：
```
    set mapred.reduce.tasks =50;
    insert overwrite directory '/user/hdfspath/part_0000'
    ROW FORMAT DELIMITED FIELDS TERMINATED BY ','
    select ...
```
2.将hdfs上的文件拷贝到Linux本地：
```
    sudo -u user hadoop fs -get  /user/hdfspath/part_0000 /tmp/a.txt
```

3.将Linux本地下载到本机：

       SecureCRT，Xshell 可执行 `sz /tmp/a.txt`
       会话选项--X/Y/Zmodem 更改下载目录   
       假如sz命令不可用：需要在你的Linux上安装lrzsz包