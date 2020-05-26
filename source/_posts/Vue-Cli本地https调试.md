---
title: Vue-Cli本地https调试
date: 2019-11-05 17:38:28
tags:
---

​	这几天在做H5的语音录制，但是getUserMedia必须在https环境下运行，本地调试使用http://localhost:port/ 无法正常运行，需要配置本地https环境。

​	网上通常使用生成本地证书的方案：

1. 生成根SSL证书
2. 信任根SSL证书
3. 在node的Express服务中读取生成的证书

```javascript
var path = require('path')
var fs = require('fs')
var express = require('express')
var https = require('https')

var certOptions = {
  key: fs.readFileSync(path.resolve('build/cert/server.key')),
  cert: fs.readFileSync(path.resolve('build/cert/server.crt'))
}

var app = express()

var server = https.createServer(certOptions, app).listen(443)
```

后来查看[vue-cli文档](https://vue-cli3.lovejade.cn/)的时候偶然发现vue-cli-service有一个--https选项

通过命令：vue-cli-service serve --https启动项目发现启动的时候修改为https启动

![image-20191105180014056](/images/image-20191105180014056.png)

配置参数：

![image-20191105174349270](/images/image-20191105174349270.png)