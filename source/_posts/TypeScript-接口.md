---
title: TypeScript 接口
date: 2018-01-09 18:16:01
tags: [TypeScript,Angular]
description: '>>>TypeScript 接口...'
---
# 接口（interface）

接口的作用是为类型命名以及为代码定义契约：

- **接口的基本使用**
```
interface LabelledValue {
	label: string;
}

function printLabel(labelledObj: LabelledValue) {
	console.log(labelledObj.label);
};

let myObj = {size: 10, label: 'Size 10 Object'};
printLabel(myObj); //Size 10 Object
```
`*当传入对象（如：myObj）满足接口内的必要条件，则被允许。并不是传给printLabel的对象实现了这个接口。`

`*类型检查器不检查属性的顺序，当相应属性存在且类型正确即可。 `

- **关于接口属性**（可选属性、只读属性以及额外的属性检查）

`接口中的属性不全是必需的，可选属性能够对可能存在的属性进行预定义以及捕获引用了不存在属性时的错误`
```
interface SquareConfig { //通过‘?’表示可选属性
	color?: string;
	width?: number;
}

function createSquare(config:SquareConfig): {color:string; area: numner} {
	let newSquare = {color: "white", area: 100};
	if (config.color) {
	    newSquare.color = config.color;
	}
	if (config.width) {
	    newSquare.area = config.width * config.width;
    }
	return newSquare;
}
let mySquare = createSquare({color: "black"});
/***当使用以下语句创建时，对象字面量会经过额外属性检查***/
let mySquare2 = createSquare({colour: 'red', width: 100}); //error
```
上文代码片段error的三种处理方式：

①使用类型断言：
```
 let mySquare2 = createSquare({colour: 'red', width: 100} as SquareConfig);
```

②使用签名索引：

```
interface SquareConfig {
	color?: string;
	width?: number;
	[propName: string]: any; //允许带有任意数量的其他属性
}
```
将对象赋值给另一个变量：

```
let squareOptions = {colour: 'red', width: 7}; //squareOptions不会经过额外属性检查
let mySquare = createSquare(squareOptions);
```
使用readonly指定只读属性
```
interface Point {
	readonly x: number;
	readonly y: number;
} 

let p1: Point = { x: 1, y: 2};
p1.x = 3;//error
```
数组创建后不能被修改，可以使用ReadonlyArray<T>
``` 
let myArray: ReadonlyArray<number> = [1, 2, 3, 4];
myArray[0] = 7; //error
myArray.push(5); //error
myArray.length = 7; //error

let a: number[];
a = myArray; //error
a = myArray as number[];//success！使用类型断言重写

/***如果a为any类型***/
let a: any; a = myArray; //success!
```

- **关于接口类型**
`函数类型`：主要是用于对参数和返回值的检查

```
interface SearchFunc {
	(source: string, subString: string): boolean; //定义了传入参数、参数类型以及返回类型（boolean）
}

let mySearch = function(src: string, sub: string): boolean {
	return true;
}
```

` 可索引类型`：可索引类型具有一个索引签名，描述了对象索引的类型及相应的索引返回值的类型
```
interface stringArray {
	[index: number]: string;
}

let myArray: stringArray = ['Dog', 'Cat'];
let myStr: string = myArray[0]; //Dog
```
共有数字和字符串两种类型的索引签名，当使用number索引时，JavaScript会将其转换成string后再去索引，所以，当同时使用两种索引时，**数字索引的返回值**必须是**字符串索引返回值**类型的**子类型**
```
class Animal {
    name: string;
}

class Dog extends Animal {
    breed: string;
}

interface Test {
    [x: string]: Animal;  
    [x: number]: Dog;   
}

let myAnimal: Animal = { name: 'Dog' };
let myDog: Dog = { name: 'Cookies ', breed: 'husky' };

let myTest: Test = {
    0: myDog,
    myAnimal
}

let theName1 = myTest.myAnimal.name; //Dog  (string索引)
let theName2 = myTest[0].name; //Cookies  (number索引)
```
可以将索引设置为只读，以防止对索引进行赋值
```
interface ReadonlyStringArray {
    readonly [index: number]: string;
}
let myArray: ReadonlyStringArray = ["Dog", "Cat"];
myArray[2] = "Pig"; // error
```
` 类类型`：作用是强制一个类去符合某种契约
```
interface AnimalInterface {
	name: string;
	speak(s: string);
}

class Animal implements AnimalInterface {
	name: string;
	speak(s: string){
		console.log(s);
	}
	constructor(){};
}
//接口描述了类的公共部分，并不会检查类是否具有某些私有成员。
interface ClockConstructor {
    new (hour: number, minute: number);
}

class Clock implements ClockConstructor {//error！ constructor存在于类的静态部分，所以不在检查的范围内。 
    currentTime: Date;
    constructor(h: number, m: number) { }
}
```
` 混合类型`：一个对象可以同时作为函数和对象使用，并且带有额外的属性。
```
interface Animal{
	(name: string): string;
	age: number;
    speak(s: string): string;
    
}

function getAnimal(): Animal {
	let animal = <Animal>function(name: string) {};
	animal.age = 2;
	animal.speak = function(s:string): string{
        return s;
    }
    return animal;
}
```
` 继承接口` ：从一个接口中复制成员到另一个接口
```
interface Shape {
	color: string;
}
interface Square extends Shape {
	sideLength: number;
}
/***一个接口允许继承多个接口***/
interface Square extends Shape ，xxx, yyy{
	sideLength: number;
}
```
` 接口继承类` :当接口继承了一个类类型时，它会继承类的成员但不包括其实现
```
class Control {
    private state: any;
}

interface SelectableControl extends Control {
    select(): void;
}
class Button implements SelectableControl {//error!因为Button中没有state属性
    select() { }
}

class Button extends Control implements SelectableControl {//success!
    select() { }
}

class TextBox extends Button{

}
let tb: TextBox;
tb.select();
```
[参考文档](https://www.tslang.cn/docs/handbook/interfaces.html)


