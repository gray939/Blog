﻿# 第三周学习总结

### 一. this

**this介绍**

当一个函数被调用时，会建立一个活动记录，也称为执行上下文。这个记录包含函数是从何处被调用的，函数是如何被调用的，被传递了什么参数等信息。这个记录的属性之一，就是在函数执行期间将被使用的 this 引用

this 关键字是JavaScript中最复杂的机制之一
this 被自动定义在所有函数的作用域中

**this特点**

>函数的调用方式决定了 this的值，运行期间绑定
 每次函数被调用时 this 的值也可能会不同
 this 不能被赋值
 this 不进行作用域传递
 
 **this作用**
 
 复用代码
 
 提供了一个更加优雅而灵便的方案，传递一个隐式的对象引用让代码变得更加简洁
 
 **this绑定规则**
 
 默认绑定
 
 1.独立函数调用。可以把这条规则看作是无法应用其他规则时的默认规则。
 2.使用非严格模式，this 会绑定到全局对象 window 上
 3.使用严格模式， this 会绑定到 undefined
 4.函数嵌套时，需注意 this 不进行作用域传递
 5.函数嵌套时，this 绑定（变量 _this、that、self 锁定 this、bind( ) 锁定）

 隐式绑定
 
 1.调用位置是否有上下文对象，函数作为对象的方法调用时，函数上下文指向这个对象
 2.调用位置是否有上下文对象
 3.数组中存放函数，被数组索引调用。this上下文指向这个数组
 对象属性引用链中只有最顶层或者说最后一层会影响调用位置
 
 显示绑定
 
 1.对象属性引用链中只有最顶层或者说最后一层会影响调用位置
 2.使用 call()、apply()、bind() 方法显示改变 this 的指向为指定对象
 
 new绑定
 
 1.new 来调用函数，或者说发生构造函数调用时，会自动执行下面的操作
 创建（或者说构造）一个全新的对象
 
 这个新对象会被执行 [[ 原型 ]] 连接
 这个新对象会绑定到函数调用的 this
 如果函数没有返回其他对象，那么new表达式中的函数调用会自动返回this (新对象)
 
 **绑定优先级**
 
 >new 绑定 > 显式绑定 > 隐式绑定 > 默认绑定
 
 判断 this 的顺序
 
 函数是否在 new 中调用,如果是的话 this 绑定的是新创建的对象;
 函数是否通过 call、apply、bind调用,如果是的话this绑定的是指定的对象;
 函数是否在某个上下文对象中调用,如果是的话，this绑定的是那个上下文对象;
 如果都不是的话，使用默认绑定,如果在严格模式下，就绑定到undefined，否则绑定到全局对象

### 二. 函数式编程

关注结果非过程
代码专业与可靠

**纯函数**

它符合两个条件：
1. 此函数在相同的输入值时，总是产生相同的输出。函数的输出和当前运行环境的上下文状态无关
2. 此函数运行过程不影响运行环境，也就是无副作用（如触发事件、发起http请求、打印/log等）

JavaScript内置函数又纯函数，也有非纯函数

特点：可移植性、可缓存性

**高阶函数**

函数作为一种数据类型
>将函数赋值给变量
 将函数作为参数传递
 将函数作为另一个函数的返回值
 
 1.在封装一个函数时，对于一个不确定的变量，我们使用传递参数的方式来指定
 2.在封装一个函数时，对于一个不确定的过程，我们往函数中传入另一个函数来指定
 
 **单例模式**
 
 1.只有仅有一个实例
 2.提供一个访问它的全局访问点
 3.对象字面量是最简单的单例模式
 4.全局变量不是单例模式，但在JavaScript开发中，我们经常会把全局变量当成单例来使用
 
 **实现单例模式**
 
 要实现一个标准的单例模式并不复杂，无非是用一个变量来标志当前是否已经为某个类创建过对象，如果是，则在下一次获取该类的实例时，直接返回之前创建的对象
 
 当我们单击登录按钮的时候，页面中会出现一个登录浮窗，而这个登录浮窗是唯一的，无论单击多少次登录按钮，这个浮窗都只会被创建一次，那么这个登录浮窗就适合用单例模式来创建
 
 **数学偏导数**
 
 偏导数表示固定面上一点的切线斜率；
 偏导的计算和单变量导数类似，只是把其中一个变量看成常量

**柯里化**

将一个低阶函数转换为高阶函数的过程就叫柯里化；
把接受多个参数的函数变换成接受一个单一参数的函数，并且返回接受余下的参数而且返回结果的新函数的技术

特点：
参数复用
提前返回
延迟计算/运行

**柯里化函数**

把一个函数转换为柯里化函数后，成为可以自由处理函数参数的函数；
柯里化函数是一个不断收集参数的函数

**bind()**

绑定 this；
把 bind()方法第一个参数以后的所有参数作为返回函数的起始实；
返回新函数

bind() 方法所返回的函数的 length（形参数量）等于原函数的形参数量减去传入bind()方法中的实参数量（就是剩下没有传的参数），因为传入 bind 中的实参都会绑定到原函数的形参

### 三. JavaScript对象与属性

**JavaScript对象**

1.对象是一种复合值：将很多值复合在一起（包括原始类型值、对象、函数）
2.对象是若干无序属性的集合，可以直接通过属性名来访问对象的属性（键值对）
3.函数作为某一个对象的属性时，称其为该对象的方法

**对象的重要性**

 >一切数据都是通过变量（标识符）保存
 对象将相应的数据封装在一起统一管理
 
 **属性的重要性**

 操作数据就是操作对象的属性
 
 **对象分类**
 
 内置对象（native object）
由 ECMAScript 规范定义的对象或构造器对象（数组、函数等）

 宿主对象（host object）
由 JavaScript 解析器所嵌入的宿主环境定义的（如：window、document）

 自定义对象（user-defined object）
运行中的用户自定义JS代码创建的对象

 **属性的种类**
 
 数据属性（Property）
 对象中的普通属性，从字符串的键到值的映射，是最常见的属性类型
 
 访问器属性（Accessor）
类似于读、写属性的特殊方法，访问器可以计算属性的值

 内置属性（Internal  property）
只存在于ECMAScript语言规范中，不能直接访问，有可能存在间接访问方式。
规范将内置属性的键置于方括号中。比如[[Scope]]、[[Prototype]]
__ proto__可以访问[[Prototype]]

**对象和属性操作**

 >定义对象
 定义属性
 访问属性
 添加属性
 修改属性
 删除属性
 遍历属性
 
 **属性访问方式**
 
 对象名.属性名
 对象名["属性名"]
 
 （.）点操作符
 属性的键必须是标识符
 
 （[]）中括号操作符
 通过表达式计算并强制转换为字符串类型的键访问属性
 
 **数据属性**
 
 特点：
  value（属性的值）：对应属性的值
  writable（可写特性）	：确定属性是否可改写性
  configurable（可配置特性）：确定属性是否能删除和其他特性是否可配置
  enumerable（可枚举特性）：属性是否可枚举
  
  **属性描述符**
 属性特性描述符是一个用来查看对象属性的特性的对象，该对象包含4个属性，对应4个特性；
 封装了属性特性的对象，方便实现数据属性特性的设置和查询
 
 **设置属性描述符**
 
Object.defineProperty
>obj —— 要在其上定义属性的对象。
prop —— 要定义或修改的属性的名称。
descriptor —— 将被定义或修改的属性描述符

 **查询属性描述符**
 
 Object.getOwnPropertyDescriptor
 
 >返回指定对象上一个自有属性对应的属性描述符。
 obj —— 需要查找的目标对象
 prop —— 目标对象内属性名称
 
 **枚举性**
 
 enumerable：枚举性
 
 一般来说，系统创建的属性不可枚举，而用户创建的属性可枚举。
通常不应该给内置原型和对象添加属性和方法。如果需要添加，应该设置属性不可枚举，避免破坏现有代码

 枚举的主要目的是判断 for-in 循环中的那些属性应该被忽略。
 枚举性影响的操作
 for-in 循环
 Object.keys()
 JSON.stringify()
 
 **可配置性**
 
 configurable：可配置特性;
 确定属性是否能删除和其他特性是否可配置
 
 **定义属性**
 
 >如果属性不存在，会创建一个新的属性，它的特性由描述符指定，若果未指定，则使用默认值
 
 >如果属性已经存在，会更新描述符指定的属性特性。但是描述符中的特性没有对应的特性，则特性不变
 
 **访问器属性的特性**
 >get：读取属性时调用的函数，该函数计算读取的结果，默认是 undefined
  set: 设置属性值时调用的函数，该函数接受设置的值作为参数，默认是undefined
 configurable（可配置特性）：确定属性是否能删除和其他特性是否可配置
 enumerable（可枚举特性）：属性是否可枚举
 
 **设置访问器属性特性**
 
1. 访问器属性（存取器属性）定义一个或两个和属性同名的函数，这个函数定义没有使用 function 关键字，而是使用 get 和 set;
2. 属性名和函数体没有冒号分隔;
3. 函数体结束和下一个属性有逗号分隔;
4. JavaScript 把这些函数当做对象的方法调用，函数中的 this 指向这个对象

设置属性的一些特性，设置权限，保护属性，比如 Math.PI;
访问器属性可用于对数据的一些计算，比如数据验证;
对属性的封装、判断、校验、默认值等操作

 
 




 

