---
title: About angular coustomize webpack config
date: 2019-05-27 14:39:03
tags: [Angular, webpack]
---
## 关于Angular自定义webpack配置
  - 在Angular-cli 1.x(对应Angular 5)中，可以使用 ` ng eject` 命令 暴露出webpack配置
  - 在Angular-cli 6 中 该命令无效，Angular-cli 6中使用 `ng eject` 命令提示

  `The 'eject' command has been temporarily disabled, as it is not yet compatible with the new angular.json format. The new configuration format provides further flexibility to modify the configuration of your workspace without ejecting. Ejection will be re-enabled in a futurerelease of the CLI. If you need to eject today, use CLI 1.7 to eject your project. `
  
  - 在 `ng eject` 无效情况下如何自定义配置webpack
    a. 安装 @angular-builders/custom-webpack

    ```
    npm install @angular-builders/custom-webpack --save-dev 
    ```
    **[注]该包依赖 @angular-devkit/build-angular>=0.7.0**
    b. 修改angular.json文件
    ` @angular-devkit/build-angular:browser` > ` @angular-buliders/custom-webpack:browser`

    ```
    "architect": {
      ...
      "build": {
        "builder": "@angular-builders/custom-webpack:browser"
        "options": {
          ...
        }
        ...
      }
    }
    ```
    c. 增加 `customWebpackConfig`

    ```
    "architect": {
      ...
      "build": {
      "builder": "@angular-builders/custom-webpack:browser"
      "options": {
        "customWebpackConfig": {
            "path": "./extra-webpack.config.js"
        }  
        ...
      }
      ...
    }
    ```
    d. 在根目录创建 `extra-webpack.config.js`
      `extra-webpack.config.js` 文件只需修改或添加默认webpack中没有的配置即可，打包过程中会将该文件与默认的webpack配置文件合并

## 关于 ng serve
  若要在开发模式下使用自定义webpack配置
  - 安装 `@angular-builders/dev-server`
  - `@angular-devkit/build-angular:dev-server` > `@angular-builders/dev-server:generic`