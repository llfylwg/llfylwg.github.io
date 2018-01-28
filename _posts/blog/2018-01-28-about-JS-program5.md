---
layout: post
title: js红宝书学习之路-第五章
description: 复习总结概括高程知识.
category: blog
---


## 重新复习回顾js高级程序设计  

> 感觉还是基础不够扎实所以看完书都整理下写出来  



### 疑惑点  

#### 数组  
  
  * 数组提供了很多操作方法，只有concat和slice不改变原数组，返回新数组，其他操作方法都会改变原数组（不包括every，some，filter，map和forEach）;    

#### 函数
  * apply和call的作用有两个，传递参数和扩充作用域；  
  `Math.max(Math,[1,2,3,4,5])`是传递参数；  
  `name="wxy";o={name:"me"};function a(){ return this.name };a.call(o)`;是扩充作用域，相当于o赋值给了函数里的this;  
  * bind是把this始终绑定到某个对象，例如：`function bb(){ return this.name };o={name:111};var func = bb.bind(o)`,func执行的上下文是o对象；    
  * `var b = function(){}()`;这是一个IIFE(立即执行函数)；对比`(function(){return this}())`;个人理解前面的代码不需要在function外面再包一层圆括号，是因为没有必要，解析器认识；而后面的因为以function开头，不包括号，解析器会以为是函数声明；  
  
#### Date  
  * UTC+时区差 = 本地时间；  
  * 月份以0开始，0表示1月；小时范围0-23；星期0-6，0表示星期日，分钟数0-59；秒数0-59；  
  * 转换为时间戳的方法：1、`+new Date()`；2、`new Date().valueOf()`；3、`new Date().getTime()`  

#### String
 * split() ==split(',')  
 * split('')返回看实例`var str="ab,cd,ee";str.split('');//["a","b",",","c","d",",","e","e"]`