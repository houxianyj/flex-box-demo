parseInt
===

基本用法
--
parseInt方法用于将字符串转为整数

    parseInt('123') // 123

如果字符串头部有空格，空格会被自动去除。

    parseInt('   81') // 81
    
如果parseInt的参数不是字符串，则会先转为字符串再转换。

    parseInt(1.23) // 1
    // 等同于
    parseInt('1.23') // 1
    
    
字符串转为整数的时候，是一个个字符依次转换，如果遇到不能转为数字的字符，就不再进行下去，返回已经转好的部分。

    parseInt('8a') // 8
    parseInt('12**') // 12
    parseInt('12.34') // 12
    parseInt('15e2') // 15
    parseInt('15px') // 15
    
上面代码中，parseInt的参数都是字符串，结果只返回字符串头部可以转为数字的部分。

如果字符串的第一个字符不能转化为数字（后面跟着数字的正负号除外），返回NaN。

    parseInt('abc') // NaN
    parseInt('.3') // NaN
    parseInt('') // NaN
    parseInt('+') // NaN
    parseInt('+1') // 1
    
所以，parseInt的返回值只有两种可能，要么是一个十进制整数，要么是NaN 

如果字符串以0x或0X开头，parseInt会将其按照十六进制数解析

    parseInt('0x10') // 16
    
如果字符串以0开头，将其按照10进制解析。

    parseInt('011') // 11
    
对于那些会自动转为科学计数法的数字，parseInt会将科学计数法的表示方法视为字符串，因此导致一些奇怪的结果。

    parseInt(1000000000000000000000.5) // 1
    // 等同于
    parseInt('1e+21') // 1
    
    parseInt(0.0000008) // 8
    // 等同于
    parseInt('8e-7') // 8
    
    
进制转换
-

parseInt方法还可以接受第二个参数（2到36之间），表示被解析的值的进制，返回该值对应的十进制数。默认情况下，parseInt的第二个参数为10，即默认是十进制转十进制。

    parseInt('1000') // 1000
    // 等同于
    parseInt('1000', 10) // 1000
    
    
下面是转换指定进制的数的例子。

    parseInt('1000', 2) // 8
    parseInt('1000', 6) // 216
    parseInt('1000', 8) // 512
    
如果第二个参数不是数值，会被自动转为一个整数。这个整数只有在2到36之间，才能得到有意义的结果，超出这个范围，则返回NaN。如果第二个参数是0、undefined和null，则直接忽略。

    parseInt('10', 37) // NaN
    parseInt('10', 1) // NaN
    parseInt('10', 0) // 10
    parseInt('10', null) // 10
    parseInt('10', undefined) // 10
    
如果字符串包含对于指定进制无意义的字符，则从最高位开始，只返回可以转换的数值。如果最高位无法转换，则直接返回NaN。

    parseInt('1546', 2) // 1
    parseInt('546', 2) // NaN
    
上面代码中，对于二进制来说，1是有意义的字符，5、4、6都是无意义的字符，所以第一行返回1，第二行返回NaN。

前面说过，如果parseInt的第一个参数不是字符串，会被先转为字符串。这会导致一些令人意外的结果。

    parseInt(0x11, 36) // 43
    parseInt(0x11, 2) // 1
    
    // 等同于
    parseInt(String(0x11), 36)
    parseInt(String(0x11), 2)
    
    // 等同于
    parseInt('17', 36)
    parseInt('17', 2)
    
上面代码中，十六进制的0x11会被先转为十进制的17，再转为字符串。然后，再用36进制或二进制解读字符串17，最后返回结果43和1。

这种处理方式，对于八进制的前缀0，尤其需要注意。

    parseInt(011, 2) // NaN
    
    // 等同于
    parseInt(String(011), 2)
    
    // 等同于
    parseInt(String(9), 2)
    
上面代码中，第一行的011会被先转为字符串9，因为9不是二进制的有效字符，所以返回NaN。如果直接计算parseInt('011', 2)，011则是会被当作二进制处理，返回3。

JavaScript 不再允许将带有前缀0的数字视为八进制数，而是要求忽略这个0。但是，为了保证兼容性，大部分浏览器并没有部署这一条规定。
