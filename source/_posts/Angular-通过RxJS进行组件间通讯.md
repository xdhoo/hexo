---
layout: ew
title: Angular 通过RxJS进行组件间通讯
date: 2018-02-28 09:48:17
tags: [Angular,RxJS]
description: '>>>Angular 组件间通讯之RxJS解决方案...'
---

# Angular 通过RxJS进行组件间通讯

Angular组件间通讯有多种方式，通过路由，及父子组件之间的通讯，本文主要总结使用Service来处理任意关系组件之间的通讯问题。

- **举个栗子简单说明**
   - 首先看一下目录结构（如图），目录结构非常简单，两个组件（component1 、component2）以及一个服务（service）
![目录结构](/img/catolog.png)
	    -  场景描述：现有两个组件A and B，两个组件共用一组数据。倘若数据不变的话，直接获取渲染就好了，然而往往需求十分活跃，要求在A组件中更改数据以后，B能够感应到并且更新自己。那么B要如何知道A把数据改了呢？？（你或许有了一些想法，类似A触发某个事件，B监听并响应？）
	    - 如何实现？
	   为例子更加简洁，A B组件都只有输入框、按钮（触发数据修改）及p标签(两个组件内容一致)
```
<p>
  component1 {{user}}
</p>
<input type="text" [(ngModel)]="user">
<button (click)="edit()">click</button>
```
```

/* service.service.ts*/

import { Injectable } from '@angular/core';
import { BehaviorSubject } from 'rxjs/BehaviorSubject'; //引入BehaviorSubject

@Injectable()
export class ServiceService {

  private users = new BehaviorSubject<string>('Jhon'); //初始一个users
  cast = this.users.asObservable();
  constructor() { }

  EditUser(newName){
    this.users.next(newName);//发送一个数据流
  }
}
```
然后回到组件中，通过订阅该服务进行修改及更新**users**的数据
```

/*component1.component.ts*/
import { Component, OnInit } from '@angular/core';
import { ServiceService } from '../../service/service.service';//引入服务

@Component({
  selector: 'app-component1',
  templateUrl: './component1.component.html',
  styleUrls: ['./component1.component.css']
})
export class Component1Component implements OnInit {

  user:string;
  constructor(private userSer:ServiceService) { }

  ngOnInit() {
  //订阅
    this.userSer.cast.subscribe(value =>{this.user = value}
    )
  }
  edit(){
    this.userSer.EditUser(this.user);
  }
}
```
最后记得将Service provider进app.module中
**providers: [ServiceService],**  /*app.module.ts*/

- 这里只简要举了一个**BehaviorSubject**（ BehaviorSubject是Subject的一个衍生类）例子，后续再对RxJS的**Subject**作详细总结

[例子github](https://github.com/xdhoo/c-to-c)
