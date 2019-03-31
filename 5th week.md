# 第五周学习总结

### 一 .标准内置对象-构造器

**Number**

包装对象:
>当访问 Number 基本数据类型属性或方法时创建临时包装对象，访问的都是对象中的属性或方法;
访问对象属性时，首先访问自身属性，访问不到时，则会在原型链上寻找对应的属性和方法

原型方法:
>Number.prototype.toFixed(...)
 Number.prototype.toPrecision(...)
 Number.prototype.toString(...)
 Number.prototype.toExponential(...)
 
 构造器属性（静态属性）:
 >Number.MAX_VALUE    Number.MIN_VALUE
 Number.NaN   Number.NEGATIVE_INFINITY
 Number.POSITIVE_INFINITY
 
 **String**
 
 在 JavaScript 中，可以使用 String 类型存储字符;
 字符串中每个字符都有特定的位置，首字符从位置 0 开始;
 字符串变量是由双引号或单引号来声明
 
 属性:
 获得字符串的长度
 >通过字符串变量的 length 属性获得
 str.length
 
 获得指定位置的字符
 >通过字符串变量的 chartAt(n) 方法获得
 str.charAt(n)
 
 **方法:**
 获取指定子串首次出现的位置
 >indexOf() 方法
 返回值为首次出现的位置下标，下标从 0 开始
 若检索的字符串值没有出现，则返回 -1
 
 根据位置提取一段子串
 >通过字符串变量的 slice(start[,end]) 方法
 返回值为包含提取部分的新的字符串
 
 把字符串分割成数组
 >通过字符串变量的 split(separator[,howmany]) 方法
 
 关于 JavaScript 中的字符串：
① 字符串变量是由双引号或单引号来声明;
② 字符串是不可更改的，故字符串的方法返回的都是全新的字符串，没有改变原始字符串;
③ 字符串的方法书写符合小驼峰命名法

**String 包装对象**
 当访问 String 基本数据类型属性或方法时创建临时包装对象，访问的都是对象中的属性或方法
 访问对象属性时，首先访问自身属性，访问不到时，则会在原型链上寻找对应的属性和方法
 
**字符串构造器方法（静态方法）**
 >String.fromCharCode(97,98,99);
 
 **字符串原型方法**
 >String.prototype.trim( );
 String.prototype.concat(str1?,str2?);
 String.prototype.toLowerCase( ); String.prototype.toLocaleLowerCase( );
 String.prototype.toUpperCase( ); String.prototype.toLocaleUpperCase( );
 String.prototype.indexOf(searchingString,position?);
 String.prototype.lastIndexOf(searchingString,position?);
 
 **字符串原型方法**
 >String.prototype.search(regexp);
 String.prototype.match(regexp);
 String.prototype.replace(regexp); 

**Array**

**方法**

获取指定值出现的位置:
 indexOf() 方法
 
 数组元素排序:
 通过数组变量的 sort() 方法 
 默认从小到大
 
 颠倒数组中元素的顺序:
 通过数组变量的 reverse() 方法 

数组转换成字符串:
 通过数组变量的 join([separator]) 方法  
 参数：指定使用的分隔符。如果省略，则使用逗号作为分隔符。
 返回一个字符串。

向/从数组中添加/删除项目:
通过数组变量的 splice(index,howmany[,item1,.....,itemX]) 方法;
返回值为包含被删除项目的新数组

数组静态方法（构造器函数对象的方法）
 >Array.from(...) 、Array.isArray(...) 、Array.of(...)等
 
 数组原型方法（添加和删除元素——破坏性）
>Array.prototype.shift()    Array.prototype.unshift(elem1?,elem2?,...)
Array.prototype.pop()     Array.prototype.push(elem1?,elem2?,...)
Array.prototype.splice(start,deleteCount?,elem1?,elem2?)

数组原型方法（排序和颠倒元素顺序——破坏性）
 >Array.prototype.reverse()
 Array.prototype.sort(compareFunction？) 
 
 数组原型方法（合并、切分和连接——非破坏性）
 >Array.prototype.concat(arr1?,arr2?,...)
 Array.prototype.slice(begin?,end?) 
 Array.prototype.join(separator?) //注意返回的类型
 
 数组原型方法（值的查找——非破坏性）
 >Array.prototype.indexOf(searchValue,startIndex?)
 Array.prototype.lastIndexOf(searchElement,startIndex?)
 
 数组原型方法（迭代——非破坏性）
 >Array.prototype.forEach(callback,thisValue?) 
 Array.prototype.every(callback,thisValue?)
 Array.prototype.some(callback,thisValue?) 
 
 数组原型方法（迭代-转换方法——非破坏性）
 >Array.prototype.map(callback,thisValue?)
 Array.prototype.filter(callback,thisValue?)
 
 数组原型方法（迭代-归约方法——非破坏性）
 >Array.prototype.reduce(element,initialValue?)
 Array.prototype.reduceRight(callback,initialValue?)
 
 forEach  遍历所有元素;
 every 判断所有元素是否都符合条件;
 some 判断是否有至少一个元素符合条件;
 map 对元素重新组装，生成新的数组;
 filter 过滤符合条件的元素
 
 **类数组**
 
 不是数组（不能够继承 Array.prototype 对象上的属性和方法）
 有 length 属性，且属性值为非负 Number 类型即可
 例：argumengts对象
           document.getElementsByClassName()

 Array-Like to Array
 >Array.prototype.slice.call(arguments)
 
 **稀疏数组(sparse array)**
 
 稀疏数组是包含从 0 开始的不连续索引的数组;
 length 值大于实际定义的元素的个数;
 遍历稀疏数组时，跳过无元素项;
 读取稀疏数组值，返回 undefined;
 只有真正存储在数组中的元素才分配内存
 
 **关联数组（associative array）**
 
 用字符串作为数组元素的索引称为关联数组;
 数组的遍历和修改操作不能作用于这些命名属性
 
 **Date**
 
 Date 提供了解析、管理和展示时间的功能
 >通过调用 Date 构造函数来实例化日期对象
 以常规函数调用它（即不加 new 操作符）将会返回一个字符串，而不是一个日期对象。
 Date 对象没有字面量格式
 
 Date 对象包含了一系列的日期时间处理的功能
 >创建 Date 对象，例:  var now = new Date( );
 
 常用操作
 >获取当前日期时间:  toLocaleString( )
 获取年份、月份、日期:  getFullYear()、getMonth()、getDate()
 获取小时、分钟、秒钟:  getHours()、getMinutes()、getSeconds()
 
 **Date构造器方法（静态方法）**
 >Date.now()
 Date.parse()
 
 **原型方法**
 >Date.prototype.get<Unit>( )   
 Date.prototype.set<Unit>( )   
 Date.prototype.toLocalTimeString( )  
 Date.prototype.toString( )  
 Date.prototype.toLocalString( ) 
 
 **Boolean**
 
 所有对象都是真值
 
 **Function**
 
 函数定义
 
 通过函数声明的形式来定义;
 通过函数表达式的形式来定义;
 通过 Function 构造函数实例化的形式来定义
 
 函数调用
 
 作为函数直接调用;
 作为对象方法调用;
 作为构造函数调用;
 通过 call/apply 间接调用
 
 原型属性
 >Function.length
 Function.name
 
 原型方法
 >Function.prototype.apply()
 Function.prototype.bind()
 Function.prototype.call()
 Function.prototype.toString()
 
 **Object**
 
 静态方法
 >Object.create()
 Object.defineProperties()
 Object.defineProperty()
 Object.getOwnPropertyDescriptor()
 Object.getOwnPropertyDescriptors()
 Object.getOwnPropertyNames()
 Object.getPrototypeOf()
 Object.setPrototypeOf()
 
 原型方法
 >Object.prototype.hasOwnProperty()
 Object.prototype.isPrototypeOf()
 Object.prototype.propertyIsEnumerable()
 Object.prototype.toString()
 Object.prototype.valueOf()
 
 **Error**
 
异常--如果执行的语句中有一句产生错误，后面的语句不会继续执行
 
异常捕获（try catch finally)
try 是必选的，catch 和 finally 两者至少要有其一;
如果没有 catch 块，程序将会终止;
catch 块指定一个标识符，该标识符保存抛出异常信息;
标识符仅在catch块执行时存在；catch块执行完成后，标识符不再可用

对所有内置错误，catch 内的错误对象主要有两个属性：
 name ：错误名称
 message ：错误信息的文本描述
 stack(非标准)：当前调用栈：关于导致错误的嵌套调用序列，用于调试目的
 
 **throw <expression>**
 
 抛出一个用户自定义的异常;
 expression 指定了异常的内容，可以为任何的JavaScript值
 
 **try catch 同步执行**
 
 如果在预定的(scheduled)代码发生异常，如setTimeout，那么try...catch不捕获异常;
为了捕获预定执行函数内的异常，try...catch必须在函数内部

**Error 构造器**

 new Error( [message]);
 Error 对象也可用于用户自定义的异常的基础对象;
 通过 Error 的构造器可以创建一个错误对象。当运行时错误产生时，Error 的实例对象会被抛出
 
 **ECMAScript 定义了七种类型错误**
 
 Error
 ReferenceError: 引用错误
 TypeError: 类型错误
 RangeError: 范围错误
 SyntaxError: 语法错误
 EvalError: Eval错误   
 URIError: URI错误
 
 处理特定类型错误:
 通过判断异常的类型来特定处理某一类的异常
 判断 constructor 属性，或使用 instanceof 关键字
 
### 二 .正则表达式

**简介**

> "^[a-z]+$"
 
 >"^[A-Za-z0-9]+$"
 
 >"^[a-zA-Z]"w{5,17}$"
 
 >"^["u4e00-"u9fa5]{0,}$"
 
 >"^("("d{3,4}-)|"d{3.4}-)?"d{7,8}$"
 
 >"^http://(["w-]+".)+["w-]+(/["w-./?%&=]*)?$"
 
 >"^"w+([-+.]"w+)*@"w+([-.]"w+)*"."w+([-.]"w+)*$"
 
 **正则表达式用途**
 
 批量提取/替换有规律的字符串;
 验证客户端的输入数据;
 各类办公软件中使用;
 各种开发语言中使用（C# / Java /JS / Perl / PHP / Python等）;
 网络爬虫（抓取机器人）的开发
 
 **正则表达式是匹配模式，要么匹配字符，要么匹配位置**
 
 正则工具
 
 https://regex101.com/
 https://jex.im/regulex/
 
 **创建正则表达式**
 
 new 运算符---new RegExp(pattern, flags)
   >var box = new RegExp('box');         //第一个参数字符串
   var box = new RegExp('box','ig');   //第二个参数可选模式修饰符
   
 字面量方式---/pattern/ flags
   >var box = /box/;       //直接用两个反斜杠
   var box = /box/ig;    //在第二个斜杠后面加上模式修饰符
   
 **正则方法**

 String和RegExp都定义了使用正则表达式进行强大的模式匹配和文本检索与替换的函数;
 RegExp对象
 test（）
 exec（）
 String对象
 replace()
 match()
 search()
 split()
 
 **RegExp方法**
 
 regObject.test(str);
 regObject.exec(str);
 
 **模式匹配的String方法**
 
 replace()方法
 >strObject.replace(regexp,'replaceString'); 
 对字符串中特定格式的子串进行替换，返回替换后的结果
 第一个参数既可以是一个固定的子串，也可以是一个正则表达式对象
 
 match()方法
 >strObject.match(regexp); 
 一个或多个子串、正则表达式的匹配
 返回一个数组
 
 search()方法
 >strObject.search(regexp); 
 返回第一次出现匹配指定正则表达式子串的下标，若没有匹配则返回 -1
 indexOf() 作用类似，但 indexOf() 不支持正则表达式
 
 split()方法
 >strObject.split(regexp,[howmany]); 
 用一个指定的字符串或正则表达式，对原字符串进行拆分，返回拆得的子串数组。
 若指定了 howmany 属性，则只返回拆得的前 howmany 个子串
 
 **修饰符**
 
 每个正则表达式都可带一个或多个标志（flags）,标明正则表达式的行为
 
**正则静态属性**

 >RegExp.$1-$9
 
 >RegExp.input ($_)
 
 >RegExp.lastMatch ($&)
 
 >RegExp.lastParen ($+)
 
 >RegExp.leftContext ($`)
 
 >RegExp.lastIndex
 
 **正则实例属性**
 
 >patten.flags
 patten.global
 patten.ignoreCase
 patten.multiline
 patten.lastIndex 
 patten.source
 
 **常用正则表达式**
 
 >/\w+((-\w+)|(\.\w+))*\@[A-Za-z0-9]+((\.|-)[A-Za-z0-9]+)*\.[A-Za-z0-9]+/ （邮箱）
 
 >/^[A-Za-z0-9_-]+$/ （密码）
 
 >/((?:(?:25[0-5]|2[0-4]\d|[01]?\d?\d)\.){3}(?:25[0-5]|2[0-4]\d|[01]?\d?\d))/ （IP地址）
 
 >/(.*)\.(rar|zip|7zip|tgz)$/ （压缩格式）
 
>/(.*)\.(jpg|bmp|gif|ico|pcx|jpeg|tif|png|raw|tga)$/ （图片判断）

 >/^#[a-fA-F0-9]{6}$/ （颜色值）
 
 >/^[A-Za-z0-9_\-\u4e00-\u9fa5]+$/ （用户名）
 
 >/0?(13|14|15|18)[0-9]{9}/ （手机号）
 
 >/^[A-Za-z0-9_()（）\-\u4e00-\u9fa5]+$/ （公司名称）
