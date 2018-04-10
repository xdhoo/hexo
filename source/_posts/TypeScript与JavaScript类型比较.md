---
title: TypeScript与JavaScript类型比较
date: 2018-01-08 15:58:14
tags: [TypeScript,JavaScript]
description: '>>> TypeScript与JavaScript类型比较...'
---

# TypeScript与JavaScript类型比较

## 布尔值（boolean）
` TypeScript/JavaScript:` 两个字面值（true/false）

```TypeScript
//TypeScript
let isShow: boolean = false;

//JavaScript
var isShow = false;
```

## 数字（number）
` TypeScript:` 所有数字都为浮点数，支持十进制、十六进制、二进制及八进制字面量
` JavaScript:` 所有数字都为浮点数，支持十进制、十六进制、二进制及八进制【八进制在严格模式下无效】字面量
``` 
//TypeScript
let age: number = 18;

//JavaScript
var age = 18;
```
## 字符串（string）
` TypeScript/JavaScript:` 使用双引号（"）或单引号（'）表示字符串
` TypeScript:` 还可以使用**模板**字符串，可以定义多行文本和内嵌表达式。使用反引号（`），并且以${ expr }形式嵌入表达式
```
//TypeScript
let str: string = 'typescript';

let sentence: string = `Hello ${ str }.`;

//JavaScript 
var str = 'javascript';

var sentence = 'Hello ' + str +'.';
```

## 数组（Array）
` TypeScript:` 两种定义数组的方式
` JavaScript:` 可通过构造函数/字面量创建数组
```
//TypeScript
let list: number[] = [1, 2, 3];

let list: Array<number> = [1, 2, 3]; //使用数组泛型，Array<元素类型>

//JavaScript
var list = [1, 2, 3];

var list = new Array(1, 2, 3);
```
## 枚举（enum）
` TypeScript:` 枚举类型是对JavaScript标准数据类型的补充
```
//TypeScript
enum Colors {Red, Yellow, Blue}/*默认从0开始为元素编号*/
let color: Colors = Colors.Yellow; //1 

////////////////////////////////
//以上代码相对应的JavaScript代码
///////////////////////////////
var Colors;
(function (Colors) {
    Colors[Colors["Red"] = 0] = "Red";
    Colors[Colors["Yellow"] = 1] = "Yellow";
    Colors[Colors["Blue"] = 2] = "Blue";
})(Colors || (Colors = {}));
var color = Colors.Yellow;
```
```
//TypeScript
enum Colors {Red = 1, Yellow, Blue};//改为从1开始编号
let color: Colors = Colors.Yellow;//2

enum Colors {Red = 1, Yellow  = 3, Blue = 5};//全部手动赋值
let color: Colors = Colors.Yellow;//3
let colorName: string = Colors[3];//Yellow
```
## Any
` TypeScript:` 用于为不清楚类型的变量指定一个类型
## Void
` TypeScript:`  表示没有任何类型，一般用于表示函数返回值
```
//TypeScript
function voidFunc(): void {
    console.log('This is voidFunc.');
} 
```
## null和undefined
` TypeScript:`  undefined和null两者各自有自己的类型分别叫做undefined和null
```
let u: undefined = undefined;
let n: null = null; 
```
## never
` TypeScript:`  表示永不存在的值的类型，never类型是任何类型的子类型，也可以赋值给任何类型

-------------------

[参考文档](https://www.tslang.cn/docs/handbook/basic-types.html)  





