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
  
关于浮点数运算的，0.1+0.2==0.3会返回false，是因为基于IEEE754浮点数计算的原因，基于IEEE754浮点数计算的语言都有这个问题，不只是js。个人理解原因是，计算时数值都会首先转换成64位二进制，再转换成32位二进制，然后进行二进制运算，再将结果转换为64位，在这个过程中有做近似值操作，所以不相等。  

建议浮点数计算时不要用==，用足够精度的范围表示，ES6提供了一种方法，如果值的绝对值误差在这个范围就算是精确的，  
例如 ：` 0.1+0.2 == 0.3  //false`，  
`Math.abs(0.1+0.2-0.3)<Number.EPSILON`(如果该表达式返回true，就认为相等)
  
再说一个转换为字符串的：  

toString(),String(), 变量+"";
除了null和undefined之外，其他都可以使用toString这个方法；
toString方法对于数字支持传入第二个参数，指明输出值的进制；

String方法可以用于所有变量，实际底层调用首先调用toString方法，没有该方法时，才会用String()去转；

业务中更建议使用  变量+""，这种方式，简单直接，支持任意类型。  

Object对象指明了所有对象都有的方法，constructor指向该对象的构造函数，hasOwnProperty方法检查实例对象是否有该属性，isPrototypeOf用于检测该对象的原型对象，toString方法和valueOf方法    

### 操作符 

这个小节是js最坑的地方，因为js是弱类型语言，会自动进行类型转换，基本的用法不做赘述，只做总结。  

* 1、+法操作符，如果有一个是字符串，则将另一个转换为字符串进行拼接，而-法操作符相反，如果有一个是字符串，则试着将其转换为数字，再进行减法计算。  例如：`true+"34"  // "true34"`； `5-"4"  // 1`
* 2、一元+操作符，类似于Number()函数，例如： `+"123" //123`;  
* 3、像其他数学运算，基本都是将非数值隐形转换为数值进行计算，注意比较符两边都是字符串的特殊计算方式，例如：` "23"<"3" // true`;  
原因是此时，字符串按位进行字符编码比较。  
* 4、特别注意null和undefined，null和undefined与其他类型变量用==比较时，不会进行转换，所以除了null == undefined,undefined == undefined和null == null其他都是返回false;  

### 语句  

注意有个label语句，可以用此配合break和continue，在多重循环时，跳出到最外层；  

break和continue不能用在数组的filter,forEach,some,map和every方法中，如果要用break和continue,请用for循环。  

switch语句，表达式和case中的结果比较时用的是===；  

函数无重载，函数体中有个arguments类数组，收集传入的参数，注意此数组的长度不是定义函数时参数的长度，是调用函数时实际传入的参数个数，而且arguments的值与参数的值始终保持一致。  

将类数组转换为数组的方法，`[].slice.call(arguments)`  

`for(a;b;c){}`;b省略时，默认为true；



 