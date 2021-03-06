﻿# 第七周学习总结

### 一.事件与事件流

**事件绑定**

事件绑定分为两种：
一种是传统事件绑定(内联模型，脚本模型)，一种是现代事件绑定(DOM2级模型)

 内联模型
>< button onclick="tell();"> 弹出提示框 < /button >
 违反了“内容与行为相分离的原则”，尽量少用
 
 脚本模型
>document.getElementById('btn').onclick = function(){  }
实现了“内容与行为相分离”但元素只能绑定一个监听函数

**DOM2 模型**

 element.addEventListener(type， listener[， useCapture])
 type —— 表示监听事件类型的字符串，不需要加“on”前缀
 listener —— 指定事件触发时执行的函数
 useCapture —— 布尔值，指定事件是否在捕获或冒泡阶段触发
 
 实现了“内容与行为相分离”;
 元素可以绑定多个监听函数;
 删除事件处理程序;
 removeEventListener(type，listener)
 具名函数可删除，匿名函数不可删除
 
 **事件三要素说明**
 
 事件是被动触发的，并不是我们能主动“加”上去的;
 元素只要符合某种事件的触发条件（比如鼠标点击），事件就必定会触发;
 我们所谓的“加”上去的是JavaScript对事件的处理函数（没有加的话就不会对事件做任何处理，但并不等于说事件就没有触发）
 
**事件流**

 描述从页面接受事件的顺序
>当几个都具有事件的元素层叠在一起的时候，那么你点击其中一个元素，并不是只有当前被点击的元素会触发事件，而层叠在你点击范围的所有元素都会触发事件

 事件流包括两种模式：冒泡和捕获
>现代浏览器默认情况下都是冒泡模型
IE 不支持捕获，只支持冒泡

**冒泡**

JavaScript 中的事件冒泡
 事件按照从目标元素到根元素（document对象）的顺序触发;
 即事件发生的顺序为：
 >button — div — body — html — document
 
 使用 stopPropagation() 方法阻止事件冒泡
 >event.stopPropagation();
 
 **冒泡事件**
 
 >event.bubbles
(返回一个布尔值，表明当前事件是否会向DOM树上层元素冒泡)
 onmouseover onmouseout —— 支持冒泡
 onmouseenter onmouseleave —— 不支持冒泡
 
 **事件委托（event delegation）**
 
 需求 —— 如果想要在大量子元素中单击任何一个都可以运行一段代码，可以将事件监听器设置在其父节点上，并将事件监听器的影响设置为每个子节点，而不是每个子节点单独设置事件监听器
 
 **捕获设置**
 
 element.addEventListener(type， listener[， useCapture])
>useCapture
布尔值，指定事件是否在捕获或冒泡阶段触发
true，指定事件在捕获阶段执行
false，指定事件在冒泡阶段执行，默认

**事件处理周期**

触发一个事件后，在 HTML 元素间进行传播过程
 1.第一阶段：事件的捕获，事件对象沿DOM树向下传播
 2.第二阶段：目标触发，执行事件监听函数
 3.第三阶段：事件冒泡，事件沿DOM树向上传播
 
 **JavaScript引擎线程**
 
 JavaScript引擎线程是单线程;
 JavaScript 的主要用途是与用户互动，以及操作DOM;
 单线程就意味着，所有任务需要排队，前一个任务结束，才会执行后一个任务。如果前一个任务耗时很长，后一个任务就不得不一直等着
 
 **同步/异步任务**
 
 任务可以分成两种，一种是同步任务，另一种是异步任务。
 
 >同步任务指的是，在主线程上排队执行的任务，只有前一个任务执行完毕，才能执行后一个任务
 
 >异步任务指的是，不进入主线程、而进入"任务队列"（task queue）的任务，只有"任务队列"通知主线程，某个异步任务可以执行了，该任务才会进入主线程执行
 
 **事件轮询（Event Loop）**
 
 消息队列：消息队列是一个先进先出的队列，它里面存放着各种消息（任务）
 
 事件循环：事件循环是指主线程重复从消息队列中取消息、执行的过程
 
### 二.ES6

ECMAScript 6.0（ES6）是 JavaScript 语言的下一代标准，已经在 2015 年 6 月正式发布了

>查看当前环境对 ES6 的支持情况
 https://ruanyf.github.io/es-checker/index.cn.html
 https://kangax.github.io/compat-table/es6/  
 兼容问题时将 ES6 转为 ES5
 http://babeljs.io/
 
 **var声明**
 
 ES5 通过 var 声明变量（无块作用域，可能造成变量污染）;
 变量声明提升
 
**let 命令**

let 声明变量
 >ES6 新增了 let 命令，用于声明变量，用法与 var 类似
 与 var 的不同在于，用 let 声明的变量只在 let 命令所在的代码块 { }内有效
 
 let 声明的特点:
 禁止重复声明
let 不允许在相同作用域内，重复声明同一个变量

 不存在变量提升
 
 暂时性死区
只要块级作用域内存在 let 命令，它所声明的变量就“绑定”（binding）这个区域，不再受外部的影响
 
 **代码块（块级作用域）**
 
 ES5 只有全局作用域和函数作用域，没有块级作用域，ES6 引入块级作用域，块级作用域在如下情况被创建：
1. 在一个函数内部
2. 在一个代码块（由一对花括号包裹）内部

 块级声明让所声明的变量在指定块的作用域外无法被访问
 
 **const 命令**
 
 const 命令
 声明一个只读的常量;
 一旦声明，常量的值就不能改变（声明时进行初始化）
 
 const 声明的特点
 >禁止重复声明
 不存在变量提升
 暂时性死区
 变量不可修改
 
 当在全局作用域上使用var时，它会创建一个新的全局变量，并成为全局对象（在浏览器中是 window ）的一个属性;
 使用 let、const创建一个新的全局变量，不会在全局对象上创建属性
 
 **函数默认值**
 
 ES6 之前，不能直接为函数的参数指定默认值，只能采用变通的方法;
 ES6 允许为函数的参数设置默认值，即直接写在参数定义的后面;
 
 **解构赋值**
 
  ES6 允许按照一定模式，从数组和对象中提取值，对变量进行赋值;
 这种写法属于“模式匹配”，只要等号两边的模式相同，左边的变量就会被赋予对应的值
 
 **对象解构赋值**
 
 对象解构语法在赋值语句的左侧使用对象字面量
 解构不成功，变量的值就等于 undefined
 解构赋值允许指定默认值
当数组/对象成员严格等于 undefined，默认值才会生效
 赋值给和属性不同的本地变量（别名）
 对象的解构赋值的内部机制，是先找到同名属性，然后再赋给对应的变量。真正被赋值的是后者，而不是前者
 
 **数组解构赋值**
 
 数组的元素是按次序排列的，变量的取值由它的位置决定;
 对象的属性没有次序，变量必须与属性同名，就能取到正确的值
 
 数组解构赋值有一个非常独特的用例，能轻易地互换两个变量的值。互换变量值在排序算法中十分常用，而在 ES5 中需要使用第三个变量作为临时变量
 
 **混合解构**
 
 对象与数组解构能被用在一起，以创建更复杂的解构表达式
 
**扩展运算符**

扩展运算符用三个点号表示，功能是把数组或类数组对象展开成一系列用逗号隔开的值

 >扩展运算符可以进行数组，对象的合并
 
 **rest运算符**
 
 定义一个 log 方法，让它可以代理 console.log 方法;
 rest 运算符也是三个点号（形式为...变量名），不过其功能与扩展运算符恰好相反，把逗号隔开的值序列组合成一个数组;
 rest 参数之后不能再有其他参数（即只能是最后一个参数），否则会报错
 
 **模板字符串**
 
 是增强版的字符串，用反引号（` `）标识;
 可以当作普通字符串使用，也可以用来定义多行字符串;
 可以在字符串中嵌入变量，需要将变量名写在${expression}之中
 
 **字符串方法**

>includes(), startsWith(), endsWith();
includes()：返回布尔值，表示是否找到了参数字符串;
startsWith()：返回布尔值，表示参数字符串是否在原字符串的头部;
endsWith()：返回布尔值，表示参数字符串是否在原字符串的尾部

 repeat(), padStart(), padEnd()
 repeat(n)：返回一个新字符串，表示将原字符串重复 n 次;
 padStart()：用另一个字符串重复填充当前字符串，以便产生的字符串达到给定的长度。填充从当前字符串的开始(左侧)应用的;
 padEnd()：用另一个字符串重复填充当前字符串，以便产生的字符串达到给定的长度。填充从当前字符串的开始(右侧)应用的
 
 **箭头函数**
 
 ES6 允许使用“箭头”（=>）函数表达式定义函数
 箭头函数不需要参数或需要多个参数，就使用一个圆括号代表参数部分;
 箭头函数的代码块部分多于一条语句，就要使用大括号将它们括起来，并且使用 return 语句返回

箭头函数特点:
 函数体内的 this 对象，就是定义时所在的对象，而不是使用时所在的对象;
 不可以当作构造函数，也就是说，不可以使用new命令，否则会抛出一个错误;
 不可以使用 arguments对象，该对象在函数体内不存在。如果要用，可以用 rest 参数代替
 
 this 对象的指向在普通函数中是可变的，但是在箭头函数里面根本没有自己的 this，而是引用外层的 this
 
 **类似数组转数组**
 
 类似数组（array-like）
 不是数组（不能够继承 Array.prototype 对象上的属性和方法）
 有 length 属性，且属性值为非负 Number 类型即可
 
 Array-Like to Array
 Array.prototype.slice.call(arguments)
 
**Array静态方法**

Array.from()
 Array.from 方法用于将类似数组的对象（array-like object）转为真正的数组 
 
  Array.of()
 Array.of() 方法用于将一组值，转换为数组
 
 **数组原型扩展**
 
 copyWithin()  find()  findIndex()  fill()
 entries()  keys()   values()
 includes()
 flat()，flatMap()
 
 **对象扩展**
 
 对象的扩展
 对象简洁表示法
 属性名表达式
 super 关键字
 静态方法
Object.is()  Object.assign()
Object.keys()，Object.values()，Object.entries()

**属性名表达式**

使用字面量方式定义对象（使用大括号），在 ES5 中只能使标识符定义属性;
 ES6 允许字面量定义对象时，用表达式作为对象的属性名，即把表达式放在方括号内
 
 **super关键字**
 
 this 关键字总是指向函数所在的当前对象;
 super 关键字指向当前对象的原型对象;
 super 关键字表示原型对象时，只能用在对象的方法（对象方法的简写法）之中
 
**Object 静态方法扩展**

 >Object.is()  Object.assign()
 Object.keys()，Object.values()，Object.entries()
