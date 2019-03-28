---
title: 关于yarn的一次记录
date: 2018-12-18 22:14:28
tags: [yarn, npm]
description: '关于yarn的一次记录'
---
## 关于yarn.lock文件
在yarn.lock文件存在且满足package.json中的依赖的情况下会根据yarn.lock文件进行安装，在package.json有更新的情况下会更新相应的包，并更新yarn.lock文件
## 关于node_sass这个依赖包
windows环境中yarn install，始终卡在node_sass这个包，切换国内镜像后可安装成功，起初以为是墙的原因，后来发现mac osx环境中不用切换国内镜像也能够安装成功。
原因：因为node_sass这个包需要用到python的原因。因为windows环境缺少python，安装一下python 2，并设置环境变量` 计算机 >> 属性 >> 高级系统设置 >> 环境变量 >> 在系统path中增加python安装目录` 即可。mac osx环境下能够成功的原因是mac osx默认自带了python 2.