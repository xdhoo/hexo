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

# Symbol
- let s = Symbol(),可添加参数描述
- Symbol值不能与其它类型的值进行运算，可以显式转为字符串，可转为boolean值
- Symbol作为属性名是不能使用点运算符
- Symbol.for() & Symbol.keyFor()

# Set &Map
- 内部使用`===`比较，所以 5 和 '5'为不同数据，注：NaN 等于NaN
- 操作方法：add / delete / has / clear
- Array.from可以将set结构转为数组
- 遍历：keys() - 键名 / values() - 键值 / entries() - 键值对 / forEach() - 回调函数遍历整个成员
- 由于Set结构没有键名，所以keys方法和values方法行为完全一致
- WeakSet结构，成员只能是对象
- WeakMap: 只接受对象作为键名

# Promise
- 对象状态不受外界影响，状态：pending(进行中) / fulfilled(已成功) / rejected(已失败)