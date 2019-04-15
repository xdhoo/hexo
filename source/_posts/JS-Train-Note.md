---
title: JS Train Note
date: 2019-03-28 13:40:56
tags: [JavaScript]
---
- ` repeat()` : 创建重复字符
- ` toString(2)` : 可用于十进制转换为二进制
- ` Array.from({length: n}).forEach()` : 用于循环n次
- ` replace(regexp/substr, replacement)` 
  replacement(字符串/函数)
  ` $`字符

| 字符 |  替换文本 |
|:---|:------------------|
| $1、$2、...、$99 | 与 regexp 中的第 1 到第 99 个子表达式相匹配的文本 |
| $& | 与regexp相匹配的子串 |
| $` | 位于匹配子串左侧的文本 |
| $' | 位于匹配子串右侧的文本 |
| $$ | 直接量符号 |

- ` sort()`: 数字排序
```
arr.sort((a,b) => a-b) //升序 
```