---
title: TypeScript 类
date: 2018-01-18 19:23:33
tags: [TypeScript,Angular]
description: '>>> TypeScript  类...'
---

## TypeScript  类 ##
----------
类
`一个简单类：`
```
class Animal{

    name: string; //属性

    constructor(name: string) {//构造函数
        this.name = name;
    }

    speak() {//方法
        return this.name + ' speak...';
    }
}
let animal = new Animal('Dog');
```
animal中具有speak方法，name属性：
![animal中具有speak方法，name属性](http://img.blog.csdn.net/20180112154910232?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMzMyMTM2ODM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

`一个基本的继承`：
```
class Animal{//基类（超类）

    speak() { };
}

class Dog extends Animal{//派生类（子类）

    eat() { };
}
let dog = new Dog();//创建一个Dog的实例
```
dog中包含speak()和eat()方法：
![这里写图片描述](http://img.blog.csdn.net/20180112155848333?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMzMyMTM2ODM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

`派生类包含构造函数的继承`：

```
class Animal{//基类（超类）

    name: string;

    constructor(name: string) {
        this.name = name;    
    };
     
    speak() { 
        return 'Animal Speak...';
    };
}

class Dog extends Animal{//派生类（子类）
    constructor(name:string) {
        super(name);
    };

    speak() {//重写重基类中继承的speak方法
        return 'Dog Speak...';
    }

    eat() { };
}
let dog = new Dog('husky');//创建一个Dog的实例
```
成员修饰符（public、private、protected）

 - public：公有，可以在任何地方访问，默认所有属性、方法都为public
 - private：私有，不允许在申明类的外部访问
 - protected：受保护，与private类似，区别在于：在其子类中允许被访问
 
存取器 - getter & setter
抽象类 - abstract

 - 抽象类不能被实例化 - new操作
 - 区别于接口，它可以包含成员的实现细节
 - 抽象类中的抽象方法不包含具体实现并且必须在派生类（子类）中实现

----------
未完.....