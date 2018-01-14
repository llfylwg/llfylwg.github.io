---
layout: post
title: js红宝书学习之路-第三章
description: 复习总结概括高程知识.
category: blog
---


## 重新复习回顾js高级程序设计  

> 感觉还是基础不够扎实所以看完书都整理下写出来  



### 数据类型  

js共包括6种数据类型，Undefined，Null,Boolean,String,Number和Object（Es6新增了symbol）;  

在数据类型这一节，基本的语法不在总结，只总结遇到的有疑问的，容易混淆的。  

关于向数字类型转换方法：Number（+）,parseInt和parseFloat,主要区别如下：  

* 1、Number解析规则是碰到不是数字字符就返回NaN,而parseInt和parseFloat从头开始解析，直到碰到非数字字符；距离如下：  

`Number("123.4blue")     //NaN; ` 

`parseInt("123.4blue")   //123  `

`parseFloat("123.4blue")   //123.4  `
* 2、parseFloat只能解析10进制的数字字符串，而Number和parseInt可以解析八进制和十六进制，parseFloat始终会忽略传入的数字字符串的第一个0，因此对于八进制会按十进制处理，对于16进制因为0后碰到x，解析停止，所以返回0；  
* 3、parseInt在解析八进制时，EM3和EM5不一致，所以支持传入第二个参数，指明传入数字字符串的基数，建议始终传入第二个参数；如下:  
`parseInt（"0xaf",16）`  
  
关于浮点数运算的，0.1+0.2==0.3会返回false，是因为基于IEEE754浮点数计算的原因，基于IEEE754浮点数计算的语言都有这个问题，不只是js。个人理解原因是，计算时数值都会首先转换成64位二进制，然后进行二进制运算，因为实际精度达不到64位，所以会做近似值操作，所以不相等。  

建议浮点数计算时不要用==，用足够精度的范围表示，例如：(范围不一定准确，但是思路这样)  

`0.1+0.2 > 0.29999 && 0.1+0.2 < 0.300001`  
  
再说一个转换为字符串的：  

toString(),String(), 变量+"";
除了null和undefined之外，其他都可以使用toString这个方法；

String方法可以用于所有变量，实际底层调用首先调用toString方法，没有该方法时，才会用String()去转；

业务中更建议使用  变量+""，这种方式，简单直接，支持任意类型。  

Object对象指明了所有对象都有的方法，constructor指向该对象的构造函数，hasOwnProperty方法检查实例对象是否有该属性，isPrototypeOf用于检测该对象的原型对象，toString方法和valueOf方法  

第三章未完，待续。。。


 