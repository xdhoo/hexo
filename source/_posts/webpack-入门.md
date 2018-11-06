---
title: webpack 入门
date: 2018-10-26 15:58:40
tags: [webpack]
description: '>>> webpack基本配置入门整理 ...'
---
# webpack打包方式
 - 使用webpack命令打包：` webpack hello.js helllo.bundle.js`
 - 使用webpack配置文件：默认去找webpack.config.js文件，若配置名改为其它：` webpack --config fileName`

# webpack 配置文件
  配置文件使用commonJs的方式exports，基本的配置文件包含了*entry（入口）*、*mode（模式，用于配置区分生产、测试环境）*、*output（出口）*、*module（用于各种loader）*、*plugins（插件）*
  ```
  /** webpack.config.js*/
  module.exports = {
    mode:'development',     // 'development' | 'production'
    entry:{
      app:'./src.app.js'
    },
    ouput:{
      filename:'[name].bundle.js',
      path:'/dist'
    },
    module:{
      rules:[
        {
          test://,      // 正则匹配文件
          use:          // 使用相关loader
        }
      ]
    },
    plugins:[]
  }
  ```