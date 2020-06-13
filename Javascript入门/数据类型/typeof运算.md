##JavaScript 有三种方法，可以确定一个值到底是什么类型。

```
typeof运算符
instanceof运算符
Object.prototype.toString方法
```
**现在只说 typeof 后面两个以后说**	
	
	
### typeof 运算符可以返回一个值的数据类型。	
	
* 数值、字符串、布尔值分别返回number、string、boolean。
	
```js
typeof 123 // "number"
typeof '123' // "string"
typeof false // "boolean"
```
	
* 函数返回function。
```js
function f() {}
typeof f
// "function"
```
		
* undefined返回undefined
```js
typeof undefined
// "undefined"
```
		
* 对象返回object
```js
typeof window // "object"
typeof {} // "object"
typeof [] // "object
```
		
**空数组（[]）的类型也是object，这表示在 JavaScript 内部，数组本质上只是一种特殊的对象**	
			
**这里顺便提一下，instanceof运算符可以区分数组和对象**	
		
		
* null返回object
```js
typeof null // "object"
```
**null的类型是object，这是由于历史原因造成的。
1995年的 JavaScript 语言第一版，只设计了五种数据类型（对象、整数、浮点数、字符串和布尔值），
没考虑null，只把它当作object的一种特殊值。后来null独立出来，作为一种单独的数据类型，
为了兼容以前的代码，typeof null返回object就没法改变了**	
		

