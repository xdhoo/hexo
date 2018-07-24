---
title: ECMAScript 6
date: 2018-07-10 15:30:50
tags: [ES6,JavaScript]
---
# 关于let

- for循环
循环变量是一个父作用域，循环体内为单独的子作用域
```
for(let i = 0; i < 1; i++){
  let i = 'hello';
  console.log(i);
} // hello
```
- 不存在变量提升
变量在未申明前使用抛出异常
- 不允许在相同作用域中，重复申明一个变量
- var & function 命令申明的全局变量，为顶层对象属性。let & const & class 申明的变量属于顶层对象属性

# 解构赋值

# 字符串
优化Unicode表示法
字符串能够被for...of遍历
新增includes() & startsWith() & endsWith()
repeat() - 返回新字符串，将原字符串重复n次，小数取整
ES2017引入字符串补全长度padStart() & padEnd()