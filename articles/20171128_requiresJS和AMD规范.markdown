### 1. 前言
一般网页开发，依赖都用script标签引入，如
```
<script src="1.js"></script>
<script src="2.js"></script>
<script src="3.js"></script>
<script src="4.js"></script>
<script src="5.js"></script>
<script src="6.js"></script>
```
由此带来的问题是加载无先后，而且未必会按你需要的顺序加载。require.js就是解决这个问题的。
### 2. require.js的下载和使用
下载:http://requirejs.org/docs/download.html
### 3. require.js的使用
```
// index.html
<script src="./require.js" data-main="./test.js"></script>
```
data-main中写的是require第一个加载的js
### 4. test.js的写法
当然可以这样写：
```
alert('hello world');
```
这样写没用到依赖，也就没必要使用require了。假设text.js同目录下有utils.js文件，那么可以
```
require(['utils'], function (utils) {
  console.log('this is test');
  utils.log();// utils里定义了log函数
});
```
### 5. define
utils中作为被加载模块，需要使用define
```
define(function () {
  var log = function (x, y) {
    console.log('this is utils');
  };
  return {
    log: log
  };
});
```
当然，define也可以写成第一个参数是依赖，第二个参数是回调函数的方式。
### 6. AMD规范
require和define一起构成了AMD规范。
### 7. 参考文章
[Javascript模块化编程（三）：require.js的用法](http://www.ruanyifeng.com/blog/2012/11/require_js.html)
[RequireJS和AMD规范](http://javascript.ruanyifeng.com/tool/requirejs.html)
