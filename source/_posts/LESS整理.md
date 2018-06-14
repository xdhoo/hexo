---
title: LESS整理
date: 2018-06-05 11:20:54
tags: [LESS]
---
## -------------特性-------------
###  变量
@变量名：值
###  混合
将class A引入class B 中，可带参数调用
```
// LESS
.rounded-corners (@radius: 5px) {
  border-radius: @radius;
  -webkit-border-radius: @radius;
  -moz-border-radius: @radius;
}
#header {
  .rounded-corners;
}
#footer {
  .rounded-corners(10px);
}

/* 生成的 CSS */
#header {
  border-radius: 5px;
  -webkit-border-radius: 5px;
  -moz-border-radius: 5px;
}
#footer {
  border-radius: 10px;
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
}
```
###  可嵌套
在选择器中嵌套另一个选择起实现继承

### 函数 & 运算
提供加 减 乘 除操作，对属性值与颜色进行计算
## 语法

### 变量 & 混合 & 带参混合
【注】@arguments变量：包含所有传递进来的参数
### 匹配模式 & 引导表达式
依据不同参数进行匹配
引导：
使用when关键字，比较运算【>  、 <  、>=   、<=  、 =】
多条件引导序列使用逗号【,】分割，当且仅当所有条件符合事，才视为匹配成功
基于值类型进行匹配。可使用函数
```
iscolor();
isnumber();
isstring();
iskeyword();
isnull();
/***************/
ispixel();
ispercentage();
isem();
```
使用【and】关键字实现与条件，使用【not】关键字实现或条件
### 嵌套规则 & 运算
【注】：串联选择器或者伪类选择器可使用【&】符号
### color函数
颜色先被转换成HSL色彩空间，然后在通道级别操作
```
lighten(@color,10%); // 亮度增加10%
darken(@color,10%); // 亮度降低10%

saturate(@color,10%); // 饱和度增加10%
desaturate(@color,10%);  // 饱和度降低10%

fadein(@color,10%); // 透明度增加10%
fadeout(@color,10%); // 透明度降低10%
fade(@color,50%); // 设置透明度为50%

spin(@color,10); // 色相值增加10
spin(@color,-10); // 色相值减少10

mix(@color1,@color2); // 混合两种颜色

/*******提取颜色信息********/
hue(@color); // 从颜色中提取色相值
saturation(@color); // 从颜色中提取饱和度值
lightness(@color); // 从颜色中提取亮度值

/*******提取颜色信息（以HSV色彩空间表示）********/
hsvhue(@color); // 从颜色中提取色相值
hsvsaturation(@color); // 从颜色中提取饱和度值
hsvvalue(@color); // 从颜色中提取色调值

/*******在一个通道上创建另一种颜色********/
@new: hsl(hue(@oldColor),50%,50%);
```

[**>>更多函数参考<<**](http://www.cnblogs.com/zfc2201/p/3493335.html )

### Math函数

```
round(1.67);//四舍五入
ceil(2.4);
floor(2.8);
percentage(0.5);//转换成百分比
```
### 命名空间
将变量或者混合模块打包
```
#bundle {
  .button {...}        
  .tab{...}
  ...
}
/*******使用*******/
#header a {
  #bundle > .button;
}
```
### 作用域
首先从本级查找变量或者混合模块，未找到沿父级查找

### 注释
保留css中的`/***/`注释，同时支持双斜线注释，但是编译后会过滤双斜线注释

### import
语法：@import "文件";【引入less文件可不带后缀名。引入css文件而不想对它进行编译，只要使用.css后缀即可】
### 字符串插值
```
@base-url: "http://test.com";
background-image: url("@{base-url}/images/bg.png");
```
### 避免编译
当需要输出一些不正确的css语法或者使用一些非les专有的语法是，可以在这样的值前加上【~】符号
```
.class {
  filter:~"ms:alwaysHasItsOwnSyntax.For.Stuff()";
}
/*****输出*****/
.class {
  filter: ms:alwaysHasItsOwnSyntax.For.Stuff();
}
```
### JavaScript表达式
``` 
// 通过反引号的方式使用
@var: `"hello".toUpperCase() + '!'`;

// 访问javascript环境
@height:`document.body.clientHeight`; 
```