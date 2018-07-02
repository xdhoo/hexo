---
title: JavaScript 高阶函数
date: 2017-08-01 11:26:54
tags: [JavaScript]
description: '>>>关于什么是高级函数，以及JavaScript中一些接收函数作为参数的数组方法...'
---
# 什么是高阶函数(higher-order-function)？
## 定义
    把函数作为参数或者返回值的一类函数 即 高阶函数
## 例子
```
function example(a, fn) { //接收一个变量a 以及一个函数fn 两个参数
    return fn(a);
}
var result = example(3.5, Math.round); //将函数Math.round作为参数传入 
console.log(result); //4
```

# JavaScript中一些接收函数作为参数的数组方法

    forEach / map / filter / sort / reduce / reduceRight / every / some / indexOf / lastIndexOf

## forEach() & map()

forEach方法遍历数组，未每个元素调用指定的函数

**array.forEach(function(currentValue, index, arr), thisValue)**

**currentValue** 必需，当前元素的值
**index** 可选，当前元素索引值
**arr** 可选， 当前元素所从属对象
**thisValue** 可选，对象作为该执行回调时使用，传递给函数，用作 "this" 的值。如果省略了 thisValue ，"this" 的值为 "undefined"

eg：

```
arr = [1, 2, 3];
result = arr.forEach(function(value, index, arr) { arr[index] = value + 1});
console.log(result); //[2, 3, 4];
```

map()调用数组的每个元素传递给指定元素，传递给map()的函数调用方式与forEach()一样，但传递给map的函数应该有返回值，【map()返回的是新数组，不修改原有数组】

eg：

```
arr = [1, 2, 3];
result = arr.map(function(value) { return x + 1});
console.log(result); //[2, 3, 4];
```

## filter()
filter()方法返回的数组元素是调用的数组的一个子集。传递的函数用来逻辑判定，filter()会跳过稀疏数组中缺少的元素，返回的数组总是稠密的

**array.filter(function(currentValue, index, arr), thisValue)**

**currentValue** 必需，当前元素的值
**index** 可选，当前元素索引值
**arr** 可选， 当前元素所从属对象
**thisValue** 可选，对象作为该执行回调时使用，传递给函数，用作 "this" 的值。如果省略了 thisValue ，"this" 的值为 "undefined"

eg：

```
arr = [1, 2, 3];
result = arr.filter(function(value) { return x <3 });
console.log(result); //[1, 2];
```

## reduce() & reduceRight()

reduce()和reduceRight()使用指定的函数将数组元素进行组合，生成单个值，必须接受两个参数
**array.reduce (function (total, currentValue, currentIndex, arr), initialValue)**

**total** 必需， 初始值，计算结束后的返回值
**currentValue** 必需， 当前元素
**currentIndex** 可选， 当前元素索引
**arr** 可选， 当前元素所属的数组对象
**initalValue** 可选，传递给函数的初始值
eg：

```
arr = [1, 2, 3];
result = arr.reduce(function(x, y) { return x + y});
console.log(result); //6
```

## every() & some()
every()和ome()对数组元素应用指定的函数进行判断，返回true或false

every()针对所有，当且仅当数组中的所有元素调用判定函数后都返回true，才返回true
some()当数组中至少有一个元素调用判定函数true时 即返回true

**array.some(function(currentValue, index, arr), thisValue)**
**array.every(function(currentValue, index, arr), thisValue)**

**currentValue** 必需，当前元素的值
**index** 可选，当前元素索引值
**arr** 可选， 当前元素所从属对象
**thisValue** 可选，对象作为该执行回调时使用，传递给函数，用作 "this" 的值。如果省略了 thisValue ，"this" 的值为 "undefined"
eg：

```
arr = [1, 2, 3];
result = arr.every(function (x) {return x < 5}); //true
result = arr.some(function (x) {return x < 2}); //true
result = arr.every(function (x) {return x < 2}); //false

```

## indexOf() & lastIndexOf()
indexOf()和lastIndexOf()搜索整个数组中具有给定值的元素，返回找到的第一个元素的索引，没有找到则返回-1，indexOf()从头至尾搜索，lastIndexOf()则反之

**array.indexOf(item, start)**
**array.lastIndexOf(item, start)**

**item** 必需， 查找元素
**start** 可选， 整数参数 ，规定在字符串中开始检索的位置。它的合法取值是 0 到 stringObject.length - 1。如省略该参数，则将从字符串的首字符开始检索。

eg：

```
arr = [1, 2, 3, 4];
result = arr.indexOf(1); //0
result = arr.lastIndexOf(1); //3
result = arr.indexOf(5); //-1

```