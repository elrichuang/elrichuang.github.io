---
layout: post
title:  导出MySQL数据字典
date:   2017-06-24 23:36:27 +0800
categories: mysql
---

执行以下SQL，将结果导出为csv文件，然后导入Excel即可。

```sql
SELECT cols.TABLE_NAME AS `表名`, tabs.TABLE_COMMENT AS `表注释`, COLUMN_NAME AS `列名`, COLUMN_TYPE AS `列类型`, COLUMN_COMMENT AS `列注释`
FROM information_schema.columns cols LEFT JOIN information_schema.TABLES tabs ON cols.TABLE_NAME = tabs.TABLE_NAME
AND cols.TABLE_SCHEMA = tabs.TABLE_SCHEMA
WHERE cols.TABLE_SCHEMA = '目标数据库名'
ORDER BY cols.TABLE_NAME ASC
```