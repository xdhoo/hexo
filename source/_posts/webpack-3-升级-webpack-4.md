---
title: 'webpack 3 升级 webpack 4 '
date: 2018-10-28 16:04:46
tags: [webpack]
description: '>>> 关于项目Webpack 3 升级 Webpack 4 记录...'
---
# 关于项目Webpack 3 升级 Webpack 4 记录
## webpack-cli
因为webpack需要使用到webpack-cli，所以webpack 4 需要安装webpack-cli
``` 
npm install webpack-cli --save-dev
```

## 升级 webpack
``` 
npm install webpack@4 --save-dev
```

## 升级相关依赖包
例如：` webpack-dev-server`,` html-webpack-plugin` 等等...

## 关于代码分割
webpack 4 移除了*CommonsChunkPlugin*, 分割代码换用*SplitChunksPlugin*
官网地址：https://webpack.js.org/plugins/split-chunks-plugin/
配置：
```
module.exports = {
  //...
  optimization: {
    splitChunks: {
      chunks: 'async', // 'initial' | 'all' | 'async'
      minSize: 30000,
      maxSize: 0,
      minChunks: 1,
      maxAsyncRequests: 5,
      maxInitialRequests: 3,
      automaticNameDelimiter: '~',
      name: true,
      cacheGroups: {
        vendors: {
          test: /[\\/]node_modules[\\/]/,
          priority: -10
        },
        default: {
          minChunks: 2,
          priority: -20,
          reuseExistingChunk: true
        }
      }
    }
  }
};
```

end...