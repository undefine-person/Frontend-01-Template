# 每周总结可以写在这里
JavaScript 中的对象分类
对象分类。

宿主对象（host Objects）：由 JavaScript 宿主环境提供的对象，它们的行为完全由宿主环境决定。
内置对象（Built-in Objects）：由 JavaScript 语言提供的对象。
固有对象（Intrinsic Objects ）：由标准规定，随着 JavaScript 运行时创建而自动创建的对象实例。
原生对象（Native Objects）：可以由用户通过 Array、RegExp 等内置构造器或者特殊语法创建的对象。
普通对象（Ordinary Objects）：由{}语法、Object 构造器或者 class 关键字定义类创建的对象，它能够被原型继承。

宿主对象
JavaScript 宿主对象千奇百怪，但是前端最熟悉的无疑是浏览器环境中的宿主了。
在浏览器环境中，我们都知道全局对象是 window，window 上又有很多属性，如 document。
实际上，这个全局对象 window 上的属性，一部分来自 JavaScript 语言，一部分来自浏览器环境。

内置对象·固有对象
固有对象是由标准规定，随着 JavaScript 运行时创建而自动创建的对象实例。
固有对象在任何 JS 代码执行前就已被创建，通常扮演类似基础库的角色。
ECMA 标准为我们提供了一份固有对象表，里面含有 150+ 个固有对象。通过这个链接查看。

内置对象·原生对象
原生对象个种类
基本类型：Boolean、String、Number、Symbol、Object
基础功能和数据结构: Array、Date、RegExp、Promise、Proxy、Map、WeakMap、Set、WeapSet、Function
错误类型：Error、EvalError、RangeError、ReferenceError、SyntaxError、TypeError、URIError
二进制操作： ArrayBUffer、SharedArrayBUffer、DataView
带类型的数组： Float32Array、Float64Array、Int8Array、Int16Array、Int32Array、UInt8Array、UInt16Array、UInt32Array、UInt8ClampedArray
通过这些构造器，可用 new 运算创建新的对象，所以我们把这些对象称作原生对象。
几乎所有这些构造器的能力都是无法用纯 JavaScript 代码实现的，它们也无法用 class/extend 语法来继承。

特殊行为的对象
除了上面介绍的对象之外，在固有对象和原生对象中，有一些对象的行为跟正常对象有很大区别。

它们常见的下标运算（就是使用中括号或者点来做属性访问）或者设置原型跟普通对象不同，这里我简单总结一下。

Array：Array 的 length 属性根据最大的下标自动发生变化。
Object.prototype：作为所有正常对象的默认原型，不能再给它设置原型了。
String：为了支持下标运算，String 的正整数属性访问会去字符串里查找。
Arguments：arguments 的非负整数型下标属性跟对应的变量联动。
模块的 namespace 对象：特殊的地方非常多，跟一般对象完全不一样，尽量只用于 import 吧。
类型数组和数组缓冲区：跟内存块相关联，下标运算比较特殊。
bind 后的 function：跟原来的函数相关联。