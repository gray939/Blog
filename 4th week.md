# 第四周学习总结

### 一 .原型与原型链

**prototype/constructor**

只有函数才会有 prototype 属性，它引用了一个对象；
只要创建一个新函数，JS引擎会根据一组特定的规则为该函数创建一个 prototype 对象

prototype 对象初始化时有一个属性constructor，用来引用函数

**__proto__**

任何对象都有__proto__属性，指向构造函数的prototype 对象

**原型继承**

实例继承原型的属性，可以访问这个属性，就像本身拥有该属性一样

**属性访问机制**

当通过对象访问属性时，JavaScript首先从本对象查找，接着是它的原型，以及原型的原型。即按照原型链查找属性

**属性屏蔽**

当在本对象和原型对象具有相同的属性时，不会再去原型上访问。也就是说本对象“遮蔽”或者“隐藏”了原型对象中的属性

**覆写**

一个对象的属性可以覆写原型对象相同键的属性。此时，前者的属性最被找到，可以隐藏原型对象的属性，使得原型对象的属性不能被访问

**属性分类**

自有属性

>自有属性指的是直接赋予该对象的属性，不需要从原型链上进行查找的属性

obj.hasOwnProperty(prop) 
 返回一个布尔值，指示对象自身属性中是否具有指定的属性
 prop —— 要检测的属性字符串名 
 
 Object.getOwnPropertyNames(obj)
 返回一个由指定对象的所有自身属性的属性名（包括不可枚举属性）组成的数组

继承属性

>从原型链上查找的属性

**遍历属性**

Object.getOwnPropertyNames(obj)
返回一个由指定对象的所有自身属性的属性名（包括不可枚举属性）组成的数组
 		
Object.keys(obj)
返回一个由指定对象的所有自身属性的属性名（不包括不可枚举属性）组成的数组

for in 循环
遍历一个对象的所有可枚举属性键

**检测属性**

obj.hasOwnProperty(prop) 

prop  in  obj
obj —— 检查它（或其原型链）是否包含具有指定名称的属性的对象;
如果指定的属性在指定的对象或其原型链中，则in运算符返回 true

**原型链**

JavaScript 基于原型的语言 (prototype-based language)

>每个对象拥有一个原型对象，对象以其原型为模板、从原型继承方法和属性。原型对象也可能拥有原型，并从中继承方法和属性，一层一层、以此类推。这种关系常被称为原型链;
解释了为何一个对象会拥有定义在其他对象中的属性和方法


>每个实例对象（object ）都有一个属性（__proto__）指向它的原型对象（prototype）。该原型对象也有一个自己的原型对象(__proto__) ，层层向上直到一个对象的原型对象为 null。根据定义，null 没有原型，并作为这个原型链中的最后一个环节。
 可通过实例化出来的对象的__proto__属性来确认原型
 
 所有对象具有 __ proto__ 属性
 函数具有 prototype属性，Function.prototype是例外，虽然是函数，但是不具有 prototype 属性
 函数具有prototype、__ proto__属性
 
 Function created by Function
 Function.__ proto__==Function.prototype
 
 Object created  by Function
 Object.__ proto__==Function.prototype
 
 Function.prototype.__ proto__ == Object.prototype
 给 Object.prototype 添加方法和属性，Function.prototype也会拥有相同的方法和属性，相反则不具有
 
 Function.prototype 是函数的起源，Object.prototype 是对象的起源
 函数也是对象，是对象中的一等公民
 
 **获取/设置/判断原型对象**
 
 Object.getPrototypeOf(obj) 
 返回指定对象的原型，如果没有继承属性，则返回 null
 
 Object.create(proto)
 创建一个新对象，使用现有的对象来提供新创建的对象的__ proto__
 
 prototypeObj.isPrototypeOf(object)
 测试 prototypeObj 对象是否存在 object 对象的原型链上
 
 **数据类型检测**
 
 1. typeof
 
 2. constructor

(1).对象的 constructor 属性用于返回创建该对象的函数，也就是我们常说的构造函数。例如：Array、Boolean、Date、Function、Number、Object、String

(2). 在 JavaScript 中，通过构造函数创建的实例对象可以访问原型对象的constructor 属性

3. object instanceof constructor

测试 constructor构造函数的prototype对象是否出现在object对象的原型链中的任何位置;

 object —— 要检测的对象
 constructor —— 某个构造函数
 
 4. toString

toString 是 Object 原型对象上的方法，使用 call 来调用该方法会返回调用者的类型字符串，格式为 [object,xxx]，xxx 是调用者的数据类型

 包括：String、Number、Boolean、Undefined、Null、Function、Date、Array、RegExp、Error、HTMLDocument 等， 基本上，所有的数据类型都可以通过这个方法获取到
 
 需要注意的是，必须通过 call 或 apply 来调用，而不能直接调用 toString ， 从原型链的角度讲，所有对象的原型链最终都指向了 Object， 按照JavaScript 属性访问规则，其他对象应该也可以直接访问到 Object 的 toString 方法，而事实上，大部分的对象都实现了自身的 toString 方法，这样就可能会导致 Object 的 toString 被终止查找，因此要用 call/apply 来强制调用 Object 的 toString 方法
 
 
 
 

