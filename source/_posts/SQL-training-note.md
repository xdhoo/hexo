---
title: SQL training note
date: 2019-05-09 10:31:16
tags: [ SQL ]
---
- `RPAD` & `LPAD`
参数(string, padded_length, [pad_string])
**string**: 待填充字符
**padded_length**: 填充后字符串长度，若小于原字符串长度，会截取n个(RPAD:从右至左，LPAD:从左至右)
**pad_string**: 可选参数，填充字符串，若为空，填充空格

- `LOWER` & `UPPER`
大小写转换函数

- `POWER`
POWER(n, m): 幂运算

- `取整`
  - `round()`: 遵循四舍五入原则取整
  - `floor()`: 向下取整
  - `ceiling()`: 向上取整

- `coalesce()` & `nullif`
**coalesce()**: 返回第一个非null值
**nullif(exp1,exp2)**: exp1,exp2相等返回null，否则返回exp1