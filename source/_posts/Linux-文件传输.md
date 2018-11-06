---
title: Linux 文件传输
date: 2018-11-02 10:04:46
tags: [Linux]
description: '>>>关于Linux服务器与本地Windows文件交互方法整理'
---
# 关于Linux服务器与本地Windows文件交互

## 方式一：使用filezilla
  - 下载地址 \>> https://filezilla-project.org/ \>> Download FileZilla Client
  - 安装完成后，界面如图所示
  ![filezilla](/img/linux/filezilla.png)
  - 通过 ` 文件` \>> ` 站点管理器` \>> ` 新建站点` \>> ` 选择SFTP协议` \>> ` 录入站点用户名及密码`
  - 直接可进行可视化文件上传下载

## 方式二：使用pscp
  - 下载PuTTY：下载地址 \>> https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html
  - 安装完成后会有pscp.exe
  - 将pscp.exe配置到环境变量以方便命令行使用（也可直接将其复制到c:\windows\system32下）
  - 命令行输入` pscp`,出现一下命令即为成功
  ![pscp](/img/linux/pscp.png)
  - 使用方法如图所示的 ` Usage`
  ` pscp [options] [user@]host:source target` 指从linux下载文件或文件夹至本地
  ` pscp [options] source [source...] [user@]host:target` 指从本地上传文件至linux服务器
  ` pscp [options] -ls [user@]host:filespec` 查看远程主机目录