isFinite
=

isFinite方法返回一个布尔值，表示某个值是否为正常的数值。

    isFinite(Infinity) // false
    isFinite(-Infinity) // false
    isFinite(NaN) // false
    isFinite(undefined) // false
    isFinite(null) // true
    isFinite(-1) // true\
    
    
除了Infinity、-Infinity、NaN和undefined这几个值会返回false，isFinite对于其他的数值都会返回true。

