# (function($){})(jquery)
## concept
用于存放开发插件的代码

## demo
```js
var fn = function($){....};
fn(jQuery);
```

## insight
这就相当于定义了一个形参为$的匿名函数，并且将jQuery作为参数来调用这个匿名函数
