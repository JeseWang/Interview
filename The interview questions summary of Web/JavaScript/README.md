- **介绍一下JS的基本数据类型。**
    
    ```
    简单的基本数据类型：Undefined、Null、Boolean、Number、String
    还有一个复杂的数据类型： object
    ```
- **介绍一下JavaScript原型，原型链，他们有何特点？**
    ```
    每个对象都会在其内部初始化一个属性，就是prototype（原型），当我们访问一个对象的属性时，如果这个对象内部不存在这个属性，那么他就会去prototype里找这个属性，这个prototype又会有自己的prototype，于是就这样一直找下去，也就是我们平时所说的原型链的概念。
    关系：instance.constructor.prototype = instance.__proto__
    
    特点：JavaScript对象是通过引用来传递的，我们创建的每个对象实体中并没有一份属于自己的原型副本，当我们修改原型时，与之相关的对象也会继承这一改变。
    
    当我们需要一个属性时，JavaScript引擎会先看当前对象中是否有这个属性，如果没有的话，它就会查找它的prototype对象是否有这个属性，如此递推下去，一直检索到object内建对象
    
    function Func(){}
    Func.prototype.name = "Jesse";
    Func.prototype.getInfo = function(){
        return this.name;
    }
    var person = new Func();
    console.log(person.getInfo());//'Jesse'
    
    console.log(Func.prototype);
    //Func{name = "Jesse",getInfo = function()}

    ```
- **Javascript如何实现继承？**
    ```
    1. 构造继承
    2. 原型继承
    3. 实例继承
    4. 拷贝继承
    
    原型prototype机制或apply和call方法去实现较简单，建议使用构造函数与原型混合方式。
    
    function Parent(){
        this.name = 'Jesse';
    }
    
    funciton Child(){
        this.age = 28;
    }
    
    Child.prototype = new Parent();
    
    var child = new Child();
    child.name == 'Jesse';//true
    ```
- **JavaScript有哪几种创建对象的方式**
    ```
    1. 对象字面量的方式
        person = {
            firstname : 'Jesse',
            lastname : 'Wang',
            age:'25',
        }
        
    2. 用function来模拟无参的构造函数
        function Person(){}
        var person = new Person();
        person.name = 'Jesse';
        person.age = '25';
        person.work = function(){
            alert(person.name);
        }
        person.work();
    
    3. 用function来模拟有参的构造函数
        function Person(name,age,score){
            this.name = name;
            this.age = age;
            this.foo = function(){
                alert(this.name + this.age + this.score);
            }
        }
        var p1 = new Person('Jesse',25,100);
        p1.foo();
        
    4. 用工厂方法创建（内置对象）
        var jsCreater = new Object();
        jsCreater.name = 'Jesse';
        jsCreater.work = 'JavaScript';
        jsCreater.info = function(){
            alert(this.work + this.name);
        }
        jsCreater.info();
        
    5. 用原型方法创建
        function Standard(){}
        Standard.prototype.name = 'Jesse';
        Standard.prototype.event = function(){
            alert(this.name);
        }
        var stan = new Standard();
        stan.name;
        stan.event();
        
    6. 混合方法创建
        functino iPhone(name,event){
            this.name = name;
            this.event = event;
        }
        iPhone.prototype.sell = function(){
            alert(this.name + this.event);
        }
        
        var SE = new iPhone('iPhone SE','在售');
        SE.sell();
    ```
- **什么是闭包(closure)，为什么要使用？**
    ```
    闭包指有权访问另一个函数作用域中变量的函数，创建闭包的最常见的方式就是在一个函数内创建另一个函数，通过另一个函数访问这个函数的局部变量，利用闭包可以突破作用于链，将函数内部的变量和方法传递到外部。
    
    闭包特性：
    1. 将函数内再嵌套函数
    2. 内部函数可以引用外层的参数和变量
    3. 参数和变量不会被垃圾回收机制回收
    
    ```
- **new操作符具体干了什么呢？**
    
    ```
    1. 创建一个空对象，并且 this 变量引用该对象，同时还继承了该函数的原型。
    2. 属性和方法被加入到 this 引用的对象中。
    3. 新创建的对象由 this 所引用，并且最后隐式的返回 this 。
    ```
- **JavaScript中有一个函数，执行对象查找时，永远不会去查找原型，这个函数是什么？**
    ```
    hasOwnProperty
    
    JavaScript中hasOwnProperty函数方法是返回一个布尔值，指出一个对象是否具有指定名称的属性。此方法无法检查该对象的原型链中是否具有该属性；该属性必须是对象本身的一个成员。
    
    使用方法：
    object.hasOwnProperty(proName)
    其中参数 object 是必选项，一个对象实例。
    proName 是必选项，一个属性名称的字符串值。
    
    如果 object 具有指定名称的属性，那么JavaScript中hasOwnProperty函数方法返回 true，反之 false。
    ```

    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
