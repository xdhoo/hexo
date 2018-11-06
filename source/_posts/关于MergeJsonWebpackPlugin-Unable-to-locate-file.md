---
title: '关于MergeJsonWebpackPlugin: Unable to locate file'
date: 2018-11-06 10:00:41
tags: [webpack]
---
在使用`merge-jsons-webpack-plugin`合并json文件时，之前一直没有错误，但今天打包后突然提示以下错误;即：找不到该路径文件，但该提示路径文件是确定正确且存在的....
![merge_json](/img/webpack/merge_json.png)

`package.json`中版本为：` "merge-jsons-webpack-plugin": "^1.0.14"`
```
//配置代码，已将路径处理为绝对路径
new MergeJsonWebpackPlugin({
  'encoding': 'utf-8',
  'files': [path.join(__dirname,'src/i18n/en.json'), path.join(__dirname,'src/assets/i18n/en.json')],
  'output': {
    'fileName': `i18n/zh.${METADATA.translationTimestamp}.json`
  }
})
```
之前一直没有问题，今天重新装包后出现在这个问题，所以为什么呢？？后来发现是`merge-jsons-webpack-plugin`版本的问题...

**寻找原因**
  - 在源码中找到` Unable to locale file `报错的定位，如图：
  *github：[\>>点击查看<<](https://github.com/tettusud/merge-jsons-webpack-plugin/blob/master/index.ts)*
  ![error](/img/webpack/error.png)  
  - 观察以上`154`行，发现此处也对路径进行了一次`join`操作
  - 导致拿到的路径`filePath`变成了类似这样的路径
  `C:\Users\Dell18090903\Desktop\C:\Users\Dell18090903\Desktop\src\i18n\en.json`
  - 抛出错误的路径是我们传入的路径，并非其真实使用的路径，所以这个问题还蛮隐蔽的
  - 综上，在配置该插件时，传入的值使用绝对路径，不需要将其处理未绝对路径

**至于为什么原先打包能够执行成功（无报错）**
  - 注意上面给到的package.json文件中该插件的版本，`安装1.0.14或者以上小版本`，所以重新`npm install`后安装了`1.0.18`
  - 翻一下源码`1.0.14` 和 ` 1.0.18`版本的区别
  - 确切来说，应该是在`1.0.17`版本的时候，该插件对于读取文件的路径做了以下修改

  *github：[\>>点击查看<<](https://github.com/tettusud/merge-jsons-webpack-plugin/commit/17ce282203b44fc51e68cf3aecf44c88df33cccb) *
  ![path_change](/img/webpack/change.png)
  - 也就是说在`1.0.17`版本以前传入绝对路径是没有问题的，`1.0.17`以及以上版本便会报路径错误

**注意**
  - `package.json`文件中的依赖包版本管理，尽量避免使用` ^ `,防止有些依赖包为遵循小版本向下兼容的情况