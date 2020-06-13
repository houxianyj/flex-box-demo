parseFloat
==

parseFloat方法用于将一个字符串转为浮点数

    parseFloat('3.14') // 3.14

如果字符串符合科学计数法，则会进行相应的转换。

    parseFloat('314e-2') // 3.14
    parseFloat('0.0314E+2') // 3.14
    
如果字符串包含不能转为浮点数的字符，则不再进行往后转换，返回已经转好的部分。

    parseFloat('3.14more non-digit characters') // 3.14
    
    
parseFloat方法会自动过滤字符串前导的空格。

    parseFloat('\t\v\r12.34\n ') // 12.34
    
    
如果参数不是字符串，或者字符串的第一个字符不能转化为浮点数，则返回NaN。

    parseFloat([]) // NaN
    parseFloat('FF2') // NaN
    parseFloat('') // NaN
    
    
上面代码中，尤其值得注意，parseFloat会将空字符串转为NaN。

这些特点使得parseFloat的转换结果不同于Number函数。

    parseFloat(true)  // NaN
    Number(true) // 1
    
    parseFloat(null) // NaN
    Number(null) // 0
    
    parseFloat('') // NaN
    Number('') // 0
    
    parseFloat('123.45#') // 123.45
    Number('123.45#') // NaN
    
    
    
