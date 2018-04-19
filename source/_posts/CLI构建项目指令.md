---
title: 'VueJs / ReactJs / Angular 构建项目'
date: 2018-03-07 10:49:13
tags: [VueJs,ReactJs,Angular]
description: '>>>整理VueJs / ReactJs / Angular 快速构建脚手架...'
---

## Node环境

安装Node.js  [**>>下载地址<<**](https://nodejs.org/en/download/)

## Angular

### 安装 Angular CLI
``` 
$ npm install -g @angular/cli 
//注：若有部分包安装失败，请使用科学上网或者使用淘宝镜像，使用淘宝镜像请确认安装cnpm 

$ npm install -g cnpm --registry=https://registry.npm.taobao.org
$ cnpm install -g @angular/cli
```

验证Angular CLI 是否安装成功 ` $ ng -v` 如下结果即成功

![ngcli](/img/npm/ngcli.png)

### 新建Angular项目
``` $ ng new project-name```

### 一些命令

| 常用命令 | 简写版本 | 说明 |
|:-----|:-----|:-----|
| ng generate component i-component | ng g c i-component | 新建组件 |
| ng generate directive i-directive | ng g d i-directive | 新建指令 |
| ng generate pipe i-pipe | ng g p i-pipe | 新建管道 |
| ng generate service i-service | ng g s i-service | 新建服务 |
| ng generate class i-class | ng g cl i-class | 新建类 |
| ng generate guard i-guard | ng g g i-guard | 新建路由守卫 |
| ng generate interface i-interface | ng g i i-interface | 新建接口 |
| ng generate enum i-enum | ng g e i-enum | 新建枚举 |
| ng generate module i-module | ng g m i-module | 新建模块 | 

 
## Vue.js

### 安装Vue-cli 

` npm install g vue-cli `

验证 vue-cli 是否安装成功 ` $ vue -V` 出现版本号即成功

### 新建Vue项目
- 使用webpack-simple模板

    `vue init webpack-simple project-name`
![Vue-init use webpack-simple](/img/npm/vueinit.png)

- 使用webpack模板

    `vue init webpack project-name`
![Vue init use webpack](/img/npm/vueinit2.png)

- 安装依赖
进入目录执行` npm install`

## React.js
使用create-react-app快速构建React开发环境

### 安装create-react-app

` $ npm install -g create-react-app`

### 新建React项目

` $ create-react-app project-name`

END.