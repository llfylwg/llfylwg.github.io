---
layout: post
title: js红宝书学习之路-第四章
description: 复习总结概括高程知识.
category: blog
---


## 重新复习回顾js高级程序设计  

> 感觉还是基础不够扎实所以看完书都整理下写出来  



### 疑惑点  

* 1、基本变量类型存在栈中，对象，数组和函数等引用类型存在堆内存中，全局变量存在全局变量区；  
* 2、基本变量类型的赋值操作，相互独立，但是引用类型赋值复制的是地址（指针），所以指向同一个对象；  
* 3、js不允许直接操作内存区域，但实际上给变量赋值对象时，操作的是引用，但是给对象添加属性时，实际上操作的是对象（内存）；  
* 4、函数参数的是按值传递，基本类型都能理解，就是复制一份给了参数；但是引用类型的（数组，对象），其实是复制了一个地址给参数； （所以会有影响） 
* 5、内存泄漏指的是对象引用完毕，但是其占用的内存仍然不能释放；（避免内存泄漏，最好使用局部变量，使用完自动销毁） 
* 6、理解作用域和上下文，作用域主要是变量存储和访问，而上下文一般指this的指向；（常见于函数）；具体的创建过程看链接
[点击我](https://zhuanlan.zhihu.com/p/26576232)

