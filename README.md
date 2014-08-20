node-repl-info
==============

REPL - Read-Eval-Print-Loop（读取-执行-打印-循环）


### exit事件


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
