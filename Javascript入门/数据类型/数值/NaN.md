NaN
=

含义
---

NaN是 JavaScript 的特殊值，表示“非数字”（Not a Number），
主要出现在将字符串解析成数字出错的场合。
		

    5 - 'x' // NaN
    
上面代码运行时，会自动将字符串x转为数值，但是由于x不是数值，
所以最后得到结果为NaN，表示它是“非数字”（NaN）

另外，一些数学函数的运算结果会出现NaN。	
    
    Math.acos(2) // NaN
    Math.log(-1) // NaN
    Math.sqrt(-1) // NaN
        
        
0除以0也会得到NaN。
    
    0 / 0 // NaN
		
需要注意的是，NaN不是独立的数据类型，而是一个特殊数值，
它的数据类型依然属于Number，使用typeof运算符可以看得很清楚。

    typeof NaN // 'number'	
		
		
运算
--

NaN不等于任何值，包括它本身。

    NaN === NaN // false
	
NaN在布尔运算时被当作false
	
    Boolean(NaN) // false

NaN与任何数（包括它自己）的运算，得到的都是NaN。
	
    NaN + 32 // NaN
    NaN - 32 // NaN
    NaN * 32 // NaN
    NaN / 32 // NaN






