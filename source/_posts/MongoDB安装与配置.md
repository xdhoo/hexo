---
title: MongoDB安装与配置(Windows)
date: 2018-05-03 16:02:03
tags: [MongoDB]
---
` 两种安装方式 - msi安装 & zip安装`

# msi安装(未成功)

## 下载地址：
https://www.mongodb.com/download-center#community 
(起初没有在这里找到zip下载，所以下载了msi，然后就掉进了坑了...)
![下载](/img/mongodb/download.png)
## 安装：
直接运行下载得到的文件，安装三次，三次不成功，错误如下
![错误](/img/mongodb/error.png)
## 说明：
或许是网络或者其他什么原因，最终未找到原因【懵】，于是放弃msi，换用zip安装 (知道原因同学欢迎留言)

#zip安装(成功)

## 下载地址：
[>>>下载地址<<<](https://www.mongodb.org/dl/win32/x86_64-2008plus?_ga=2.67605713.1130691981.1525313225-1975521497.1525313225)
请选择喜欢的版本进行下载

## 安装：

### 将下载得到的zip文件解压到 D:\mongodb 目录下(也可其他磁盘)，解压后如图
![目录](/img/mongodb/catalog.png)

## 配置：
创建存放数据库的文件 新建 data 并在内部新建 db 文件夹，目录如：` D:\mongodb\data\db `
执行 ` D:\mongodb\bin>mongod --dbpath D:\mongodb\data\db  ` 
可访问localhost:27017查看是否连接成功

创建一下两个文件
D:\mongodb\data\log\mongodb.log
D:\mongodb\mongo.config

mongo.config中内容如下

```
dbpath=D:\mongodb\data\db
logpath=D:\mongodb\data\log\mongodb.log  
```

以上完成后，以管理员身份打开CMD
执行 `mongod --config D:\mongodb\mongo.config --install --serviceName "MongoDB"  ` 
查看日志是否成功

cmd输入 ` services.msc` 可查看MongoDB服务，点击启动即可，如图：
![服务](/img/mongodb/services.png)

# 可视工具
可使用studio-st
地址：https://studio3t.com/