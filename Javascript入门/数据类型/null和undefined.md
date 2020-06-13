## null与undefined都可以表示“没有”，含义非常相似。
### 将一个变量赋值为undefined或null，老实说，语法效果几乎没区别。
```js
var a = undefined;
// 或者
var a = null;
```
	
**在if语句中，它们都会被自动转为false，相等运算符（ == ）甚至直接报告两者相等**



### 既然含义与用法都差不多，为什么要同时设置两个这样的值，这不是无端增加复杂度，令初学者困扰吗？这与历史原因有关


&#160; &#160; &#160; &#160;首先，第一版的 JavaScript 里面，null就像在 Java 里一样，
被当成一个对象，Brendan Eich 觉得表示“无”的值最好不是对象。
其次，那时的 JavaScript 不包括错误处理机制，Brendan Eich 觉得，如果null自动转为0，很不容易发现错误。

因此，他又设计了一个undefined。区别是这样的：null是一个表示“空”的对象，
转为数值时为0；undefined是一个表示"此处无定义"的原始值，转为数值时为NaN。

	
	
	
* 实践
```js
if  判断 undefined null 时 都转成 false

undefined null 用  == 比较时 是相等的

用 Number 函数   null 会转成  0  //Number(null)  == 0   
做运算时 null可以自动转为0。  5+null // 5  


用 Number 函数   undefined 会转成  NaN  //Number(undefined)  == NaN
做运算时 5 + undefined // NaN
```
	
	
	
	
### 用法和含义

		
	
null表示空值，即该处的值现在为空。调用函数时，某个参数未设置任何值，
这时就可以传入null，表示该参数为空。比如，某个函数接受引擎抛出的错误作为参数，
如果运行过程中未出错，那么这个参数就会传入null，表示未发生错误。

	
* undefined表示“未定义”，下面是返回undefined的典型场景。
```js
// 变量声明了，但没有赋值
var i;
i // undefined

// 调用函数时，应该提供的参数没有提供，该参数等于 undefined
function f(x) {
  return x;
}
f() // undefined

// 对象没有赋值的属性
var  o = new Object();
o.p // undefined

// 函数没有返回值时，默认返回 undefined
function f() {}
f() // undefined
```
	
###	布尔值

如果 JavaScript 预期某个位置应该是布尔值，会将该位置上现有的值自动转为布尔值。
转换规则是除了下面六个值被转为false，其他值都视为true
	
```js
undefined
null
false
0
NaN
""或''（空字符串）
```
**注意**
* **空数组（[]）和空对象（{}）对应的布尔值，都是true**
