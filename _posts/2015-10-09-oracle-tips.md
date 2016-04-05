---
layout: post
title: oracle的一些常用技巧			
date: 2015-10-09 13:20
modified: 				
category: SQL
tags: ["oracle","sql"]
excerpt: 使用oracle的一些常用的技巧
comments: true
---


###1. Oracle中针对中文进行排序
Oracle9i之前，中文是按照二进制编码进行排序的。 在oracle9i中新增了按照拼音、部首、笔画排序功能。

* 按中文拼音进行排序:`SCHINESE_PINYIN_M`
* 按中文部首进行排序:`SCHINESE_RADICAL_M` 按照部首（第一顺序）、笔划（第二顺序）排序
* 按中文笔画进行排序:`SCHINESE_STROKE_M` 按照笔划（第一顺序）、部首（第二顺序）排序

直接写在SQL中：

~~~sql
SELECT * FROM TEAM ORDER BY NLSSORT(col_name,'NLS_SORT = SCHINESE_PINYIN_M');
SELECT * FROM TEAM ORDER BY NLSSORT(col_name,'NLS_SORT = SCHINESE_STROKE_M');
SELECT * FROM TEAM ORDER BY NLSSORT(col_name,'NLS_SORT = SCHINESE_RADICAL_M');
~~~

配置在初始化参数`NLS_SORT`中,这可以在数据库创建时指定,也可以通过alter session来修改.如果是前者，则在所有session中生效。

* 使用`select * from NLS_SESSION_PARAMETERS;`语句可以看到`NLS_SORT`的值.
* 更改配置文件:`alter system set nls_sort='SCHINESE_PINYIN_M' scope=spfile;`
* 更改session:`alter SESSION set NLS_SORT = SCHINESE_PINYIN_M;`

注意一下性能问题,按oracle官方文档的解释,oracle在对中文列建立索引时,是按照2进制编码进行排序的,所以如果`NLS_SORT`被设置为`BINARY`时，排序则可以利用索引.如果不是2进制排序，而是使用上面介绍的3种针对中文的特殊排序，则oracle无法使用索引，会进行全表扫描.这点一定要注意,多用plsql工具比较一下执行效率.解决方法是,在此列上建立linguistic index.
例如:
`CREATE INDEX nls_index ON my_table (NLSSORT(col_name, 'NLS_SORT = SCHINESE_PINYIN_M'));`

###2. Oracle添加和查看表、字段的注释

* 给表添加注释

~~~sql
COMMENT ON TABLE TABLENAME IS '注释内容';
~~~

* 查看表的注释

~~~sql
SELECT TABLE_NAME, TABLE_TYPE, COMMENTS WHERE TABLE_NAME = '表名';
~~~

* 给字段添加注释

~~~sql
COMMENT ON COLUMN 表名.字段名 IS '注释内容';
~~~

* 查看字段的注释

~~~sql
SELECT TABLE_NAME, COLUMN_NAME, COMMENTS WHERE TABLE_NAME = '表名';
~~~




