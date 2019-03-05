﻿# 第一周学习总结

### 一. 学习所使用的软件

**VSCode、思维导图、Markdown、git与github**

### 二. JS介绍

**JavaScript 和 DOM 并不是不可分割的，它们的语言标准相互独立。
DOM 对 JavaScript 来说，是宿主对象，是语言中可更换的部分。
ECMAScript 对 JavaScript 来说，是核心语言，是不可被替代的功能。**

**ECMAScript（ES）是 JavaScript 的语法标准**

**ECMAScript 的版本（ES5、ES6）**

>ES5（2009年12月发布）当前网络上大部分用的是 ES5
ES6（2015年06月发布）增加了许多新特性，并解决了很多 ES5 中的缺陷，逐渐流行开来
ES7（2016年06月发布）完善 ES6 规范
ES8（2017年06月发布） 增加新的功能，如并发、原子操作等
ES9（2018年06月发布） 增加了异步迭代，RegExp 等相关功能

### 三. JS数据类型分类

**ES5 数据类型（6种）及其划分（2类）**
 **基本（原始）类型**
 Number、String、Boolean、Null、Undefined
 **引用（对象）类型**
 Object（Array、Function、Date、Error等
 
**typeof操作符**
返回一个字符串，表示未经计算的操作数的类型
 类型|结果
--|:--:|
Undefined|"Undefined"
Null|"object"
Boolean|"boolean"
Number|"number"
String|"string"
函数对象|"function"
任何其他对象|"object"

**值和类型**
 JavaScript 中的变量是没有类型的，只有值才有。变量可以随时持有任何类型的值。（动态类型）
 
 在对变量执行 typeof 操作时，得到的结果并不是该变量的类型，而是该变量持有的值的类型，因为 JavaScript 中的变量没有类型。
 
 
 
### 四. JS数据类型储存

**栈/堆**

 栈内存|堆内存
--|:--:|
存储基础数据类型|存储引用数据类型/或基础数据类型如闭包中的数据
按值访问|按引用访问
存储的值大小固定|存储的值大小不定，可动态调整
由系统自动分配内存空间|由程序员通过代码进行分配
主要用来执行程序|主要用来存放对象
空间小，运行效率高|空间大，但是运行效率相对较低
先今后出，后进先出|无序储存，可根据引用直接获取

**基本类型与引用类型的区别**

 1.访问机制不同
 2.复制变量不同
 3.比较变量不同
 4.参数传递不同

### 四. JS数据类型转换

**类型转换 —— 将值从一种类型转换为另一种类型**

 隐式类型转换：通常是某些操作的副作用，不易看出
 
 显示类型转换：可以在代码中明显看出
 
 **包装对象**
 JavaScript 对象是一种复合值，是属性的集合。
 包装对象
 存取字符串、数字或布尔值的属性时创建的临时对象称为包装对象
 区分字符值和字符串对象、数字和数值对象、布尔值和布尔对象
 字符串、数字和布尔值的属性时只读的
 通过 String()，Number()，Boolean() 构造函数显示创建包装对象

**宽松相等**

不同数据类型判断宽松相等

 >undefined 和 null，它们被认为是宽松相等的（undefined == null //true）;
 一个字符串和一个数字，则将字符串转换为一个数字;
 一个布尔值和一个非布尔值，则将布尔值转换为一个数字，然后(再次)进行宽松比较;
 一个对象和一个数字，字符串，布尔值，则尝试转换此对象为一个原始值然后(再次)进行宽松比较;
不符合上述提到的情况，宽松比较的结果是 false。