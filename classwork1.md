# for循环、for in遍历、forEach  三者比较

### for循环

**解释：**

用于创建一个循环,它包含了三个可选的表达式,三个可选的表达式包围在圆括号中并由分号分隔,后面跟随一个语句或一组语句在循环中执行

**参数：**

initialization一个表达式 (包含赋值语句) 或者变量声明。典型地被用于初始化一个计数器。该表达式可以使用var关键字声明新的变量。初始化中的变量不是该循环的局部变量，而是与该循环处在同样的作用域中。该表达式的结果无意义。

condition一个条件表达式被用于确定每一次循环是否能被执行。如果该表达式的结果为true， 循环体内的语句将被执行。 这个表达式是可选的。如果被忽略，那么就被认为永远为true。如果计算结果为false，那么执行流程将被跳到for语句结构后面的第一条语句。

final-expression每次循环的最后都要执行的表达式。执行时机是在下一次condition的计算之前。通常被用于更新或者递增计数器变量。

statement只要condition的结果为true就会被执行的语句。 要在循环体内执行多条语句，使用一个 block 结构 ({ ... }) 来包含要执行的语句。没有任何语句要执行，使用一个 empty 语句 (;)

---

### for in遍历

**解释：**

以任意顺序遍历一个对象的可枚举属性。对于每个不同的属性，语句都会被执行

**参数：**

variable
在每次迭代时,将不同的属性名分配给变量。
object
被迭代其枚举属性的对象。
 

for..in 不应该被用来迭代一个下标顺序很重要的 Array .
数组索引仅是可枚举的整数名，其他方面和别的普通对象属性没有什么区别。for...in 并不能够保证返回的是按一定顺序的索引，但是它会返回所有可枚举属性，包括非整数名称的和继承的。

因为迭代的顺序是依赖于执行环境的，所以数组遍历不一定按次序访问元素。 因此当迭代那些访问次序重要的 arrays 时用整数索引去进行 for 循环 (或者使用 Array.prototype.forEach() 或 for...of 循环)

---

### forEach

**解释：**

用于调用数组的每个元素，并将元素传递给回调函数

**参数：**

callback为数组中每个元素执行的函数，该函数接收三个参数：

currentValue(当前值)
数组中正在处理的当前元素。
index(索引)
数组中正在处理的当前元素的索引。
array
forEach()方法正在操作的数组。
thisArg可选可选参数。当执行回调 函数时用作this的值(参考对象)

---

# 方法封装

**forEach（ ）**

```
 Array.prototype._forEach = function (callback,context){  
    context = context || window;  
    if('forEach' in Array.prototye) {  
        this.forEach(callback,context);  
        return;  
    } 
```


**map（ ）**

```
Array.prototype._Map = function(callback,context){  
    context = context || window;  
    if('map' in Array.prototye) {  
        return this.map(callback,context);  
    }  
```

**map（ ）**

```
Array.prototype._filter = function(callback,context){ 
    var temp = [];
    for (var k = 0;k < this.length;k++){
        callback.call(context,this[k],k,this)?temp.push(this[k]):"";
    }
    return temp;
}
```

**some（ ）**

```
Array.prototype._some = function(callback,context){ 
    for (var k = 0;k < this.length;k++){
        if (callback.call(context,this[k],k,this)){
            return true;
        }
    }
    return false;
}
```

**every（ ）**

```
Array.prototype._every = function(callback,context){ 
    for (var k = 0;k < this.length;k++){
        if (！callback.call(context,this[k],k,this)){
            return false;
        }
    }
    return true;
}
    
```
