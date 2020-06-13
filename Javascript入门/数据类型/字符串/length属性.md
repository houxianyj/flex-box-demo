length 属性
=

length属性返回字符串的长度，该属性也是无法改变的。
    
    var s = 'hello';
    s.length // 5
    
    s.length = 3;
    s.length // 5
    
    s.length = 7;
    s.length // 5
    
上面代码表示字符串的length属性无法改变，但是不会报错。

