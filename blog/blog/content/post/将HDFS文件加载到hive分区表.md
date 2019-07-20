---
title: "将HDFS文件加载到hive分区表"
date: 2019-07-19T18:27:36+08:00
lastmod: 2019-07-19T18:27:36+08:00
description: ""
tags: ["Hive","HDFS"]
categories: ["大数据"]
author: "codecat"
keywords: ["Hive","HDFS"]
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

shell脚本如下：
如果目标表有分区，先清除分区

> alter table table_name drop partition (dt >= '20181211');

```
#!/bin/bash
cu_date=`date +%Y%m%d`
begin_date="20181211"

while [ "$begin_date" -le "$cu_date" ];
do
	echo "${begin_date}"
	
	hive -e "alter table table_name add partition (dt='${begin_date}') 
	locatition 'hdfs://Cluster/user/hive/warehouse/.../dt=${begin_date}'; "
	
	begin_date=$(date -d "${begin_date}+1days" +%Y%m%d)
done
echo "finished"
```
