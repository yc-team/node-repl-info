node-repl-info
==============

REPL - Read-Eval-Print-Loop（读取-执行-打印-循环）


### exit事件

当用户用一些定义好的方式离开REPL：

在REPL会话里面输入.exit或者按了ctrl+c两次发送SIGINT，或者按ctrl+d来发送input流的end信号

示例：

```javascript
r.on('exit', function () {
  console.log('Got "exit" event from repl!');
  process.exit();
});
```

### REPL特性

在REPL里面，按ctrl+d可以退出。可以输入多行表达式。
对于全局和局部变量都支持tab键提示。

这个特殊的变量（下划线）包含上一次表达式的结果


```javascript
> [ "a", "b", "c" ]
[ 'a', 'b', 'c' ]
> _.length   // _ 就是 [ 'a', 'b', 'c' ]
3
> _ += 1     // _ 就是 3
4
```


REPL提供在全局作用域访问任何一个变量。

通过暴露一个变量给每一个REPLServer关联的context对象。


```javascript
var repl = require('repl'),
	msg = "zhangyaochun";

repl.start('> ').context.m = msg;
```

context对象里面的东西会在REPL里面出现：

```
mjr:~$ node repl_test.js
> m
'zhangyaochun'
```


有一些特殊的REPL命令：

* .break  当输入一个多行表达式的时候，有时候你
* .clear  把context对象重置为一个空对象并且清空所有的多行表达式
* .exit   关闭I/O流，使得REPL退出
* .help   显示特殊命令的列表
* .save	  把当前的REPL会话保存到一个文件		.save ./file/to/save.js
* .load   加载一个文件到当前的REPL会话里面   .load ./file/to/load.js





下面的组合键在REPL里面有一些特殊的效果：

* ctrl+c 和 .break关键字类似。
* ctrl+d 和 .exit关键字类似。

