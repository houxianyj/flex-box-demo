构造函数
=

面向对象编程的第一步，就是要生成对象。前面说过，对象是单个实物的抽象。通常需要一个模板，表示某一类实物的共同特征，然后对象根据这个模板生成。

典型的面向对象编程语言（比如 C++ 和 Java），都有“类”（class）这个概念。所谓“类”就是对象的模板，对象就是“类”的实例。但是，JavaScript 语言的对象体系，不是基于“类”的，而是基于构造函数（constructor）和原型链（prototype）。

JavaScript 语言使用构造函数（constructor）作为对象的模板。所谓”构造函数”，就是专门用来生成实例对象的函数。它就是对象的模板，描述实例对象的基本结构。一个构造函数，可以生成多个实例对象，这些实例对象都有相同的结构。

构造函数就是一个普通的函数，但是有自己的特征和用法。

    var Vehicle = function () {
      this.price = 1000;
    };
    
    
上面代码中，Vehicle就是构造函数。为了与普通函数区别，构造函数名字的第一个字母通常大写。

构造函数的特点有两个。

* 函数体内部使用了this关键字，代表了所要生成的对象实例。
* 生成对象的时候，必须使用new命令。


new 命令
-

#### 基本用法

new命令的作用，就是执行构造函数，返回一个实例对象。

    var Vehicle = function () {
      this.price = 1000;
    };
    
    var v = new Vehicle();
    v.price // 1000
    
    
上面代码通过new命令，让构造函数Vehicle生成一个实例对象，保存在变量v中。这个新生成的实例对象，从构造函数Vehicle得到了price属性。new命令执行时，构造函数内部的this，就代表了新生成的实例对象，this.price表示实例对象有一个price属性，值是1000。

使用new命令时，根据需要，构造函数也可以接受参数。

    var Vehicle = function (p) {
      this.price = p;
    };
    
    var v = new Vehicle(500);
    
new命令本身就可以执行构造函数，所以后面的构造函数可以带括号，也可以不带括号。下面两行代码是等价的，但是为了表示这里是函数调用，推荐使用括号。

    // 推荐的写法
    var v = new Vehicle();
    // 不推荐的写法
    var v = new Vehicle;
    
如果忘了使用new命令，直接调用构造函数会发生什么事？

这种情况下，构造函数就变成了普通函数，并不会生成实例对象。而且由于后面会说到的原因，this这时代表全局对象，将造成一些意想不到的结果。

    var Vehicle = function (){
      this.price = 1000;
    };
    
    var v = Vehicle();
    v // undefined
    price // 1000
    
    
上面代码中，调用Vehicle构造函数时，忘了加上new命令。结果，变量v变成了undefined，而price属性变成了全局变量。因此，应该非常小心，避免不使用new命令、直接调用构造函数。

为了保证构造函数必须与new命令一起使用，一个解决办法是，构造函数内部使用严格模式，即第一行加上use strict。这样的话，一旦忘了使用new命令，直接调用构造函数就会报错。

    function Fubar(foo, bar){
      'use strict';
      this._foo = foo;
      this._bar = bar;
    }
    
    Fubar()
    // TypeError: Cannot set property '_foo' of undefined
    
    
上面代码的Fubar为构造函数，use strict命令保证了该函数在严格模式下运行。由于严格模式中，函数内部的this不能指向全局对象，默认等于undefined，导致不加new调用会报错（JavaScript 不允许对undefined添加属性）。

另一个解决办法，构造函数内部判断是否使用new命令，如果发现没有使用，则直接返回一个实例对象。

    function Fubar(foo, bar) {
      if (!(this instanceof Fubar)) {
        return new Fubar(foo, bar);
      }
    
      this._foo = foo;
      this._bar = bar;
    }
    
    Fubar(1, 2)._foo // 1
    (new Fubar(1, 2))._foo // 1
    
上面代码中的构造函数，不管加不加new命令，都会得到同样的结果。
