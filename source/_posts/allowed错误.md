---
title: 'Nginx 处理跨域 - 405 Method not allowed错误'
date: 2018-04-18 17:37:56
tags: [Nginx]
description: '>>>Nginx 处理跨域 - 405 Method not allowed错误'
---
问题：`  在Nginx中配置以下内容后，依旧返回405 Method not allowed错误`
``` 
add_header 'Access-Control-Allow-Headers' 'Content-Type'; 
add_header 'Access-Control-Allow-Origin' '*'; 
add_header 'Access-Control-Allow-Methods' '*';
```
原因：` 当前端发起跨域请求时，会首先发起一个OPTIONS请求，来查询该接口是否支持跨域及对应的请求方法`

解决方案：` 将OPTIONS请求的状态码重定向为204,配置OPTIONS请求如下`

``` 
if ($request_method = 'OPTIONS') {
    add_header 'Access-Control-Allow-Headers' 'Content-Type'; 
    add_header Access-Control-Allow-Origin '*';
    add_header Access-Control-Allow-Methods '*';
    return 204;
}
```

END.

