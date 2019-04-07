# 第六周学习总结

### 一 .Json

**数据**

从结构上看，所有的数据最终都可以分解成三种类型:
 1.第一种类型是标量（scalar），也就是一个单独的字符串（string）或数字（numbers）
 
 2.第二种类型是序列（sequence），也就是若干个相关的数据按照一定顺序并列在一起，又叫做数组（array）或列表（List）
 
 3.第三种类型是映射（mapping），也就是一个键/值对（Name/value），即数据有一个名称，还有一个与之相对应的值，这又称作散列（hash）或字典（dictionary）
 
 **数据交换格式**
 
在日常生活中，人与人之间的交流需要彼此都听得懂得语言。同理，在计算机的不同程序之间，或者不同的编程语言之间进行交换数据，也需要一种大家都能听得懂得‘语言’，这就是数据交换格式，它通过文本以特定的形式来进行描述数据。
 
 **XML**
 
 XML 指可扩展标记语言（EXtensible Markup Language）;
 XML 是一种标记语言，很类似 HTML;
 XML 的设计宗旨是传输数据，而非显示数据;
 XML 标签没有被预定义。您需要自行定义标签;
 XML 被设计为具有自我描述性;
 XML 被设计用来传输和存储数据;
 HTML 被设计用来显示数据
 
 **XML书写准则**
 
 xml文件的第一行必须是声明该文件是xml文件以及它所使用的xml规范版本。在文件的前面不能够有其它元素或者注释;
 在xml文件中有且只能够有一个根元素;
 xml文件中，用的大多都是自定义的标记;
 在xml文件中的标记必须正确地关闭标记之间不得交叉;
 属性值必须要用“ ”号括起来;
 控制标记、指令和属性名称等英文要区分大小写
 
 **JSON（JavaScript Object Notation）**
 
 >JavaScript 对象表示法
 是轻量级的文本数据交换格式
 更小、更快，更易解析
 是一种数据格式，不是编程语言
 虽然具有相同的语法形式，但 JSON 并不从属于 JavaScript
 并不是只有 JavaScript 才使用 JSON，JSON 只是一种数据格式
 很多编程语言都有针对 JSON 的解析器和序列化器
 
 >JavaScript Object Notation，JS对象标记
 JSON 是 JavaScript 对象的字符串形式的表示法，使用文本表示 JavaScript  对象的信息，本质是一个字符串
 
 **JSON语法**
 
 并列的数据之间用逗号（", "）分隔;
 并列数据的集合（数组）用方括号("[]")表示;
 映射用冒号（": "）表示;
 映射的集合（对象）用大括号（"{}"）表示;
 字符串必须加双引号
 
 JSON 语法可以表示以下三种类型的值
 
 1.简单值 
 与 JavaScript 语法相同，可以在 JSON 中表示字符串、数值、布尔值和 null。
 JSON 不支持 JavaScript 中的特殊值 undefined。 
 
 2.对象 
一种复杂数据类型，表示一组无序的键值对。
 键值对中的值可以是任意类型——简单值、对象或数组。
 
 3.数组 
一种复杂数据类型，表示一组有序的值的列表。
数组的值可以是任意类型——简单值、对象或数组。

**Table 对象**

 在 HTML 文档中 <table> 标签每出现一次，一个 Table 对象就会被创建
 var table = document.createElement( "table" )
 
 常用属性和方法
 
 >table.rows	 —— 返回包含表格中所有 tr 元素的集合
 table.createCaption() —— 为表格创建一个 caption 元素
 table.insertRow(index) —— 在表格中的指定位置插入一个空的 tr 元素
 table.deleteRow(index) —— 从表格删除指定位置的行
 
 **TableRow 对象**
 
 在 HTML 文档中出现一个 <tr> 标签，就会创建一个 TableRow 对象
 var tr = table.insertRow() 
 
 常用属性和方法
 
 >tr.cells —— 返回表格行中所有 td 或 th 元素的集合 
 tr.insertCell(index) —— 在一行的指定位置插入一个空的 td 元素
 tr.deleteCell(index) —— 删除表格行中的指定 td 元素
 
 **TableCell 对象**
 
 在 HTML 文档中出现一个"< td> "标签，就会创建一个 TableCell 对象
 var td = tr.insertCell() 
 
 **TableHeader 对象**
 
 在 HTML 文档中出现一个 <th> 标签，就会创建一个 TableHeader 对象 
 var th = document.createElement("th"); 
 
### 二 .Ajax

**HTTP协议**

Web 使用一种名为 HTTP（HyperText Transfer Protocol，超文本传输协议）的协议作为规范，完成从客户端到服务器端等一系列运作流程。而协议是指规则的约定。可以说，Web 是建立在 HTTP 协议上通信的

HTTP 是一种不保存状态，即无状态（stateless）协议。HTTP 协议自身不对请求和响应之间的通信状态进行保存。也就是说在 HTTP 这个级别，协议对于发送过的请求或响应都不做持久化处理

**URI**

统一资源标识符、格式

**请求报文**

请求报文是由请求方法、请求URI、协议版本、可选的请求首部字段和内容实体构成的

**响应报文**

响应报文基本上由协议版本、状态码（表示请求成功或失败的数字代码）、用以解释状态码的原因短语、可选的响应首部字段以及实体主体构成

方法（Method）—— 告知服务器意图的 HTTP 方法
 >GET ：获取资源
 POST：传输实体主体
 PUT：传输文件
 DELETE：删除文件
 HEAD：获得报文首部
 OPTIONS：询问支持的方法
 指定请求的资源按期望产生某种行为，使用方法下达命令
 
 **状态码**
 
 HTTP 状态码负责表示客户端HTTP请求的返回结果、标记服务器端的处理是否正常、通知出现的错误等工作
 
 **表单提交**
 
 enctype
 
 >当 method 属性值为 post 时, enctype 是将 form 的内容提交给服务器的 MIME 类型 。可能的取值有:
 application/x-www-form-urlencoded: 未指定属性时的默认值;
 multipart/form-data: 用于一个 type 属性设置为 "file" 的 <input> 元素;
 text/plain (HTML5)
 
 **URL转义**
 
 >encodeURI
 decodeURI
 encodeURIComponent
 decodeURIComponent
 
 **Ajax（Asynchronous Javascript And XML）**
 
 Ajax 可以使网页实现异步更新。这意味着可以在不重新加载整个网页的情况下，对网页的某部分进行更新;
 Ajax 技术与数据格式无关
 
 **XMLHttpRequest**
 
 Ajax 是一种用来改善用户体验的技术，其实质就是使用XMLHttpRequest 对象异步的向服务器发送请求
 
 步骤
 >创建 XMLHttpRequest 对象实例
 创建请求
 发送请求
 回调事件处理函数
 
 **创建请求open()**
 
 method —— 请求类型 get / post;
 url —— 请求地址;
 bool —— 异步/同步请求;
>true：表示发送异步请求(当 Ajax 发送请求的时候，用户仍然可以对当前页面做其他操作)；
false：表示发送同步请求(当 Ajax 发送请求的时候，浏览器会锁定当前页面,用户不能对当前页面做其他操作)

**指定请求的HTTP头**

setRequestHeader() 指定请求的 HTTP 头信息
 xhr.setRequestHeader("Content-Type","application/-www-form-urlencoded");
 POST 请求发送表单数据，把表单数据转换成一个字串
 
 **发送请求send()**
 
 send方法内传递提交参数(POST)，没有填写 null
>xhr.send('name=value&name=value');

 若要提交数据，也可在 open 方法的 "URL" 后面追加
>xhr.open('GET','xx.php?name=value&name=value',true)

 请求发送到服务器端，收到数据会自动填充 XHR 对象的属性
 >readyState：请求状态
 status：服务器返回的 http 请求响应值
 responseText：服务器返回的文本数据

readyState：请求状态
0 尚未初始化
1 正在发送请求
2 请求完成
3 请求成功，正在接受数据
4 接收数据成功

status：服务器返回的 http 请求响应值
200  表示请求成功
202  请求被接受但处理未完成
400  错误的请求
404  资源未找到
500  内部服务器错误

responseText：服务器返回的文本数据
 请求响应 json 数据时得到的结果为字符串类型;
 JSON.parse(xhr.responseText)解析为 JavaScript 对象
 
 **$.ajax()方法**
 
该方法是 jQuery 底层 AJAX 实现

>$.post( )---post 请求

>$.get( )---get 请求

>$.getJSON()---加载json 文件