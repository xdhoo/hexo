---
title: Git 常用命令整理
date: 2018-11-08 09:55:37
tags: [git]
description: '关于项目开发过程中，常用git命令梳理'
---
## 1. 配置 & 创建项目 

**a. 配置**
  - ` git config --global user.name [用户名]`：配置全局用户名
  - ` git config --global user.email [邮箱]`：配置全局邮箱

**b. 初始`.git`文件**
  - 初始到当前目录下，使用` git init`
  - 初始化到新文件中，使用` git init [文件名]`

## 2. 使用

**a. 查看相关命令**
  - ` git status`：查看当前状态，展示当前所在分支，以及代码提交情况
  - ` git log`：查看提交日志，展示提交详细信息，包含Author，Date等等
  - ` git log --oneline`：同上，区别在于将一条信息显示在一行，方便阅读
  - ` git diff`：查看当前代码与仓库代码的差异，用于查看修改了那些内容，该命令与` git status`的区别在于，该命令会详细显示哪一行代码做了更改，新增的文件不会显示,而` git status`显示的是那个文件做了修改。

**b. 提交相关命令（本地仓库）**
  - ` git add .`：将*所有*修改的代码添加到暂存区
  - ` git add [文件]`：将*某个*修改的文件添加到暂存区
  - ` git reset HEAD .`：将所有暂存文件取消暂存
  - ` git reset HEAD [文件]`：将某个已暂存文件取消暂存
  - ` git commit -m "说明"`：将所有暂存的修改提交到本地仓库
  - ` git reset --hard <commit_id>`：删除对应commit_id版本之后的commit,【该方式**不会**保留修改后的代码】
  - ` git reset --soft <commit_id>`：删除对应commit_id版本之后的commit,【该方式**会**保留修改后的代码,若要提交可直接重新提交】

**c. 远程仓库相关操作**
  - ` git clone [远程仓库地址]`：从远程仓库克隆代码到本地
  - ` git fetch`：获取远程仓库，但不将代码合并到本地，例如获取远程分支情况
  - ` git pull`：获取远程仓库代码，并与本地代码合并
  - ` git push`：将本地仓库代码推送至远程仓库
  - ` git push -u [远程仓库名] [地址]`:

**d. 分支相关命令**