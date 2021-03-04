---
title: JavaScript实现继承的几种方式
date: 2019-06-09 13:39:07
toc: true
categories: JavaScript
# thumbnail: img/shell.jpg
---
<p>继承：是<a href="https://en.wikipedia.org/wiki/Object-oriented_programming">面向对象（to:wiki）</a>Object-oriented_programming软件技术当中的一个概念，与多态、封装共为面向对象的三个基本特征。 继承可以使得子类具有父类的属性和方法或者重新定义、追加属性和方法等。</p>

<!-- more -->

以下内容出自《JavaScript高级程序设计》，此部分看过多遍，此处总结归纳一下。

<h4>原型链</h4>
<p style="text-indent:30px">实现继承的基本思想：利用原型让一个引用类型继承另一个引用类型的属性和方法。</p>
<p style="text-indent:30px">类中构造函数、原型和实例的关系：每个构造函数都有一个原型对象，原型对象都包含一个指向构造函数的指针，而实例都包含一个指向原型对象的内部指针。<span style="color:red;">让原型对象等于另一个类型的实例。则原型对象将包含一个指向另一个原型的指针。同时包含一个指向另一个构造函数的指针。</span>层层递进，就构成了实例和原型的链条。</p>

```
    function Animal() {
        this.home = "earth"
    }

    Animal.prototype.say = function () {
        return "hello"
    }

    function Cat(color) {
        this.color = color
    }

    // 原型对象等于另一个类型的实例
    Cat.prototype = new Animal()

    // 添加新方法
    Cat.prototype.eat = function () {
        return "fish"
    }

    var whiteCat = new Cat()
    
    alert(whiteCat.home) // "earth"
    alert(whiteCat.say()) // "hello"
    alert(whiteCat.eat()) // "fish"
```

<注>
    <ol>
        <li>给原型添加方法的代码一定要放在替换原型的语句之后；</li>
        <li>不能使用对象字面量创建原型方法；</li>
        <li>原型中包含引用类型值(如数组)，多个子类改变父类属性及方法会相互干扰；</li>
        <li>没办法在不影响所有对象实例的情况下，给超类型的构造函数传递参数；</li>
    </ol>
    <p>则<span style="color:red;">很少单独使用</span></p>


<h4>借用构造函数</h4>
<p style="text-indent:30px">实现继承的基本思想：在子类型构造函数的内部调用超类型构造函数。借助apply()和call()方法。</p>

```
    function Animal() {
        this.colors = ["red","blue","yellow"]
    }

    function Cat() {
        Animal.call(this)
    }

    var calico = new Cat()

    calico.colors.push("white")

    var blackCat = new Cat()

    blackCat.colors = "black"

    console.log(calico.colors) // ["red", "blue", "yellow", "white"]
    console.log(blackCat.colors) // "black"
```

<注>
    <p style="text-indent:30px">采用此方法，方法都在构造函数中定义，函数复用无从谈起。在父原型中定义的方法，对子类型而言不可见，则所有类型都只能使用构造函数模式。则<span style="color:red;">很少单独使用</span></p>

<h4>组合继承</h4>
<p style="text-indent:30px">实现继承的基本思想：使用原型链实现对原型属性和方法的继承，而通过借用构造函数来实现对实例属性的继承。既通过在原型上定义方法实现了函数复用，又能保证每个实例都有它自己的属性。</p>

```
    function Animal(age) {
        this.age = age
        this.colors = ["red","blue","yellow"]
    }

    Animal.prototype.say = function () {
        return "hello"
    }

    function Cat(age) {
        // 继承属性
        Animal.call(this, age)
    }

    // 继承方法
    Cat.prototype = new Animal();

    Cat.prototype.constructor = Cat;

    var calico = new Cat()

    calico.colors.push("white")

    var blackCat = new Cat()

    blackCat.colors.push("black")

    calico.say() // "hello"
    blackCat.say() // "hello"
    console.log(calico.colors) // ["red", "blue", "yellow", "white"]
    console.log(blackCat.colors) // ["red", "blue", "yellow", "black"]

```

<p>则为<span style="color:red;">最常用的继承模式</span></p>


<h4>原型式继承</h4>
<p style="text-indent:30px">实现继承的基本思想：借助原型可以基于已有的对象创建新对象，同时还不必因此创建自定义类型。此处借助ECMAScript 5的Object.create()方法实现。</p>
<p style="text-indent:30px">Object.create()接收两个参数：一个用作新对象原型的对象和（可选的）一个为新对象定义额外属性的对象。</p>
<p style="text-indent:30px">原型式继承可以在不必预先定义构造函数的情况下实现继承，其本质是执行对给定对象的浅复制。而复制得到的副本还可以得到进一步改造。</p>

<注>
    <p style="text-indent:30px">采用此方法兼容Ie9+、Firefox 4+、Safari 5+、Opera 12+、Chrome</p>

<h4>寄生式继承</h4>

<p style="text-indent:30px">实现继承的基本思想：创建一个仅用于封装继承过程的函数，该函数在内部以某种方式来增强对象，最后再像真地是它做了所有工作一样返回对象。</p>

<p style="text-indent:30px">为了解决组合模式由于多次调用超类型构造函数而导致的低效率问题，可以将这个模式与组合模式一起使用</p>

<注>
    <p style="text-indent:30px">基本不考虑自定义类型和构造函数的情况下可使用。但也不能够做到函数复用。</p>

<h4>寄生组合式继承</h4>
<p style="text-indent:30px">实现继承的基本思想：通过借用构造函数来继承属性，通过原型链的混成形势来继承方法。避免组合模式调用两次超类型构造函数</p>

```
    function inheritPrototype(subType, superType){
        var prototype = Object.create(superType.prototype); //创建父类原型的一个副本 等同于使用Object.create(superType.prototype)
        prototype.constructor = subType;   //为副本添加constructor属性,弥补重写原型而失去的constructor属性
        subType.prototype = prototype; //将创建的对象(副本)赋值给子类的原型
    }
    function Animal(name) {
        this.name = name;
    }
    Animal.prototype.sayName = function () {
        alert(this.name);
    };
    function Cat(name, age) {
        Animal.call(this,name);  //继承SuperType
        this.age = age;       //扩展出age属性
    }
    inheritPrototype(Cat, Animal);
    Cat.prototype.sayAge = function () {
        alert(this.age);
    };//扩展出sayAge方法

    var calico=new Cat("linda",2);
    calico.sayName();
    calico.sayAge();
```

<p>普遍认寄生组合式继承为<span style="color:red;">引用类型最理想的继承范式。</span></p>

<h4 style="color:blue;">ES6实现继承</h4>
<p style="text-indent:30px"></p>
```
class Animal {
    //构造函数
    constructor(props) {
      this.name = props.name || '未知';
    }

    eat() {
      alert(this.name + "在吃东西...");
    }
  }

  //class继承
  class Bird extends Animal {
    //构造函数
    constructor(props) {
      //调用实现父类的构造函数
      super(props);
      this.type = props.type || "未知";
    }

    fly() {
      alert(this.name + "在飞...");
    }
  }
  var myBird = new Bird({
    name: '鹦鹉'
  })
  myBird.eat()
  myBird.fly()
```

<h4 style="margin-top:50px;"><附></h4>
<ol>
    <li>什么是引用类型？
        <p>基本类型(number,string,boolean,null,undefined)之外就是引用类型</p>
    </li>
    <li>存储上的区别？
        <p>基本类型的变量是存放在栈区的（栈区指内存里的栈内存）</p>
        <p>引用类型的存储需要内存的栈区和堆区（堆区是指内存里的堆内存）共同完成，栈区内存保存变量标识符和指向堆内存中该对象的指针，也可以说是该对象在堆内存的地址</p>
    </li>
</ol>

