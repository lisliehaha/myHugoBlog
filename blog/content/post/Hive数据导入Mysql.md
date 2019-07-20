---
title: "Hive数据导入Mysql"
date: 2019-07-19T18:51:31+08:00
lastmod: 2019-07-19T18:51:31+08:00
description: ""
tags: ["Hive","数据同步"]
categories: ["大数据"]
author: "codecat"
keywords: ["Hive","Mysql"]
comment: true
toc: false
autoCollapseToc: false
postMetaInFooter: false
hiddenFromHomePage: false
contentCopyright: false
reward: true
mathjax: true
mathjaxEnableSingleDollar: false
mathjaxEnableAutoNumber: false
---

方法一（适用于批处理，调度）：
利用sqoop工具：

    sqoop export 
    --connectjdbc:mysql://192.168.56.104:3306/test?useSSL=false \
    --username root \
    --password123456 \
    --table t2 \
    --export-dir /user/hive/warehouse/test.db/mysql_t1 \
   更多详情可参见sqoop官网：
   [http://sqoop.apache.org/docs/1.99.7/user.html](http://sqoop.apache.org/docs/1.99.7/user.html)

方法二（适用于临时导出）：
1.在Hive上查看表的存储路径：`show create table tablename`

2.在hdfs上将路径复制到Linux本地：   
```
    sudo -u user hadoop fs -get  /.../part-00000  /localpath/part-00000
```

3.将拷贝下来的数据导入Mysql：    
```
    mysql -h host -u user -P 3321 -D db -ppassword --default-character-set=utf8 --local-infile=1 -e "LOAD DATA LOCAL INFILE '/localpath/part-00000' INTO TABLE longtrip_search_info(column_name)"
```
column_name 以逗号分隔；

另外：如果想导入多天数据，可以在步骤2中将 -get 替换成 -getmerge
         （-getmerge ： 将一个路径下的文件合并成一个文件进行拷贝）
         
   其他方法：利用DataX等开源数据同步工具，详情可参见github项目
   [https://github.com/alibaba/DataX](https://github.com/alibaba/DataX)
   
 
