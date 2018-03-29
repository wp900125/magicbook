# Javascript异步
## concept
每一个任务有一个或多个回调函数（callback），前一个任务结束后，不是执行后一个任务，而是执行回调函数，后一个任务则是不等前一个任务结束就执行，所以程序的执行顺序与任务的排列顺序是不一致的、异步的。

## demo
假定有两个函数f1和f2，后者等待前者的执行结果。
* 回调函数
```js
function f1(callback){
　　　　setTimeout(function () {
　　　　　　// f1的任务代码
　　　　　　callback();
　　　　}, 1000);
　　}
```
* 事件监听
```js
f1.on('done', f2);

function f1(){
　　　　setTimeout(function () {
　　　　　　// f1的任务代码
　　　　　　f1.trigger('done');
　　　　}, 1000);
　　}
```
* 发布/订阅
```js
jQuery.subscribe("done", f2);

function f1(){
  setTimeout(function () {
    // f1的任务代码
    jQuery.publish("done");
  }, 1000);
}

jQuery.unsubscribe("done", f2);
```
发布/订阅的一种实现
```js
(function($) {
  var o = $({});
  $.subscribe = function() {
    o.on.apply(o, arguments);
  };
  $.unsubscribe = function() {
    o.off.apply(o, arguments);
  };
  $.publish = function() {
    o.trigger.apply(o, arguments);
  };
}(jQuery));
```
* Promises对象
```js
function f1(){
  var dfd = $.Deferred();
  setTimeout(function () {
    // f1的任务代码
    dfd.resolve();
  }, 500);
  return dfd.promise;
}
  
f1().then(f2).then(f3);
f1().then(f2).fail(f3);
```

## insight
