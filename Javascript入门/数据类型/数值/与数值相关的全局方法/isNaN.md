isNaN
=

isNaN方法可以用来判断一个值是否为NaN。

    isNaN(NaN) // true
    isNaN(123) // false
    

**但是，isNaN只对数值有效，如果传入其他值，会被先转成数值。比如，传入字符串的时候，字符串会被先转成NaN，所以最后返回true，这一点要特别引起注意。也就是说，isNaN为true的值，有可能不是NaN，而是一个字符串。**

    isNaN('Hello') // true
    // 相当于
    isNaN(Number('Hello')) // true
    
出于同样的原因，对于对象和数组，isNaN也返回true。

    isNaN({}) // true
    // 等同于
    isNaN(Number({})) // true
    
    isNaN(['xzy']) // true
    // 等同于
    isNaN(Number(['xzy'])) // true


但是，对于空数组和只有一个数值成员的数组，isNaN返回false。

    isNaN([]) // false
    isNaN([123]) // false
    isNaN(['123']) // false
    
上面代码之所以返回false，原因是这些数组能被Number函数转成数值，请参见《数据类型转换》一章。

因此，使用isNaN之前，最好判断一下数据类型。

    function myIsNaN(value) {
      return typeof value === 'number' && isNaN(value);
    }

判断NaN更可靠的方法是，利用NaN为唯一不等于自身的值的这个特点，进行判断。


