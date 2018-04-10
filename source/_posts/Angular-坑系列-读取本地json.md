---
title: 'Angular 坑系列 #读取本地json'
date: 2017-12-21 10:02:58
tags: [Angular]
description: '>>>填了一个坑...'
---
## 读取本地json & 图片路径问题（Not Found） ##
####    -- 描述：
----------
项目开发前期，通过http请求本地的json文件来作临时展示，在获取json文件过程中一直遇到文件*not found* 错误。

**`项目目录结构`：**
![这里写图片描述](http://img.blog.csdn.net/20180125113249875?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMzMyMTM2ODM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
**`错误`：**
![not-found](http://img.blog.csdn.net/20180125112850806?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMzMyMTM2ODM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
![这里写图片描述](http://img.blog.csdn.net/20180125134750901?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMzMyMTM2ODM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
####   -- 解决：####

----------
######i.配置angular-cli.json
```
"assets": [
  "assets",
  "json",//将存放json文件配置进assets中
  "images",//将images文件配置进assets中
  "favicon.ico"
],
```
######ii.将静态资源文件放置在assets文件目录下
![这里写图片描述](http://img.blog.csdn.net/20180125135518112?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMzMyMTM2ODM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
####   关于相对路径细节：
图片访问路径是依据***index.html*** 的位置来确定的，而非当前目录文件夹

以上...希望能帮助你加快填坑