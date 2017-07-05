---
layout: post
title:  数据库命名规范
date:   2017-07-05 10:16:25 +0800
categories:
- MySQL
---

1. 布尔值字段用`is_`或者`has_`开头，例如：`is_deleted`，`has_power`；
2. 数量字段使用`num_`开头，例如：`num_pv`，`num_read`；
3. 当一对多或多对一关联时，外表的ID需要加表名前缀，例如：商品表中的分类ID为`catalog_id`；
4. 状态是`status`，类型`type`；
5. 索引使用`idx_`作为前缀命名；