# express app.use()
## tags
`node`
## concept
app.use是express“调用中间件的方法”。所谓“中间件（middleware），就是处理HTTP请求的函数，用来完成各种特定的任务，比如检查用户是否登录、分析数据、以及其他在需要最终将数据发送给用户之前完成的任务。
简而言之，app.use() 里面使用的参数，主要是函数。但这个使用，并不是函数调用，而是使能的意思。当用户在浏览器发出请求的时候，这部分函数才会启用，进行过滤、处理。

## demo
```js
var express = require(‘express’);
var app = express();

app.use(express.static(__dirname + '/public'));
app.use(logger());
app.use(function(req, res){
  res.send('Hello');
});
```

## insight

## reference
[Express框架](http://javascript.ruanyifeng.com/nodejs/express.html#toc5)
