---
title: 修改npm默认配置路径
date: 2018-01-20 09:18:06
tags: [npm, NodeJs]
description: '>>> 关于修改npm默认安装路径配置笔记...'
---
` 
安装nodejs过程中顺带把npm也安装好了，但是默认会把后续所有全局模块安装在C盘中。
下面介绍如何将路径配置F盘(依据自己习惯，随意放在X盘)
`
- 1.首先打开` cmd `输入命令` npm config ls`查看当前配置,默认情况下全局安装包将放置在以下目录中

 ![configls](/img/npm/configls.png) 
- 2.使用命令设置` cache & prefix` 例如将路径修改为: **E:\NodeJS\npm** & **E:\NodeJS\npm-cache**(可随意自定义)

``` 
npm config set prefix "E:\NodeJS\npm"
npm config set cache "E:\NodeJS\npm-cache"
```
- 3.修改nodejs安装路径下的**npmrc**文件,路径：{安装位置}\node_modules\npm\npmrc

``` 
//prefix=${APPDATA}\npm //删除该行默认配置
prefix=E:NodeJS\npm
cache=E:NodeJS\npm-cache
```

- 4.修改环境变量
` 控制面板 >> 系统 >> 高级系统设置 >> 环境变量 >> 编辑Path`
![setpath](/img/npm/setpath.png)

- 5.测试安装
``` npm install -g bower ```
bower相关包将被安装在新配置目录下

END.