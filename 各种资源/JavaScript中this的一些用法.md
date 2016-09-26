---
title: JavaScript中的this的一些用法
date: 2016-09-20 20:09:43
tags: JavaScript
categories: Front-End
---


#### 一、global this
---
- 总结起来就是：在浏览器里面`this`是老大，它等价于`window`对象，如果你声明一些全局变量(不管在任何地方)，这些变量都会作为`this`的属性。
- 在node里面，有两种执行`JavaScript`代码的方式，一种是直接执行写好的`JavaScript`文件，另外一种是直接在里面执行一行行代码。
- 对于直接运行一行行`JavaScript`代码的方式，`global`才是老大，`this`和它是等价的。在这种情况下，和浏览器比较相似
- 也就是声明一些全局变量会自动添加给老大`global`，顺带也会添加给`this`。
- 但是在`node`里面直接脚本文件就不一样了，你声明的全局变量不会自动添加到`this`，但是会添加到`global`对象。所以相同点是，在全局范围内，全局变量终究是属于老大的
<!--more-->

#### 二、function this
---
- 如果不是用`new`调用，在函数里面使用`this`都是指代全局范围的`this`
- 函数里面的`this`其实相对比较好理解，如果我们在一个函数里面使用`this`，需要注意的就是我们调用函数的方式，如果是正常的方式调用函数，this指代全局的this
- 如果我们加一个`new`，这个函数就变成了一个构造函数，我们就创建了一个实例，`this`指代这个实例，这个和其他面向对象的语言很像
- 另外，写`JavaScript`很常做的一件事就是绑定事件处理程序，也就是诸如`button.addEventListener(‘click’, fn, false)`之类的，如果在`fn`里面需要使用`this`，`this`指代事件处理程序对应的对象，也就是`button`

#### 三、prototype this
---

- 你创建的每一个函数都是函数对象。它们会自动获得一个特殊的属性`prototype`，你可以给这个属性赋值。当你用`new`的方式调用一个函数的时候，你就能通过`this`访问你给`prototype`赋的值了

```javascript
function Thing() {
      console.log(this.foo);
 }
 
 Thing.prototype.foo = "bar";

 var thing = new Thing(); //logs "bar"
 console.log(thing.foo);  //logs "bar"
```

- 当你使用`new`为你的函数创建多个实例的时候，这些实例会共享你给`prototype`设定的值。当你调用`this.foo`的时候，都会返回相同的值，除非你在某个实例里面重写了自己的`this.foo`

- 实例里面的`this`是一个特殊的对象。你可以把`this`想成一种获取`prototype`的值的一种方式。当你在一个实例里面直接给`this`添加属性的时候，会隐藏`prototype`中与之同名的属性。如果你想访问`prototype`中的这个属性值而不是你自己设定的属性值，你可以通过在实例里面删除你自己添加的属性的方式来实现

- 通过一个函数创建的实例会共享这个函数的`prototype`属性的值，如果你给这个函数的`prototype`赋值一个`Array`，那么所有的实例都会共享这个`Array`，除非你在实例里面重写了这个`Array`，这种情况下，函数的`prototype`的`Array`就会被隐藏掉
- 给一个函数的`prototype`赋值一个`Array`通常是一个错误的做法。如果你想每一个实例有他们专属的`Array`，你应该在函数里面创建而不是在`prototype`里面创建
- 实际上你可以通过把多个函数的`prototype`链接起来的从而形成一个原型链，因此`this`就会魔法般地沿着这条原型链往上查找直到找你你需要引用的值

```javascript
function Thing1() {
 
    Thing1.prototype.foo = "bar";

}
function Thing2() {

}
    Thing2.prototype = new Thing1();

    var thing = new Thing2();
    console.log(thing.foo); //logs "bar"
```

#### 四、object this
---

- 在一个对象的一个函数里，你可以通过`this`来引用这个对象的其他属性。这个用`new`来新建一个实例是不一样的

```javascript
var obj = {
     foo: "bar",
     logFoo: function () {
         console.log(this.foo);
     }
 };
 
 obj.logFoo(); //logs "bar"
```

- **注意**，没有使用`new`，没有使用`Object.create`，也没有使用函数调用创建一个对象。你也可以将对象当作一个实例将函数绑定到上面

```javascript
 var obj = {
     foo: "bar"
 };
 
 function logFoo() {
     console.log(this.foo);
 }
 
 logFoo.apply(obj); //logs "bar"
```

#### 五、DOM event this
---

- 在一个`HTML DOM`事件处理程序里面，`this`始终指向这个处理程序被所绑定到的`HTML DOM`节点

```javascript
function Listener() {
      document.getElementById("foo").addEventListener("click",
         this.handleClick);
  }
  Listener.prototype.handleClick = function (event) {
      console.log(this); //logs "<div id="foo"></div>"
  }
  
  var listener = new Listener();
  document.getElementById("foo").click();
```
- 除非你自己通过`bind`切换了上下文

```javascript
 function Listener() {
      document.getElementById("foo").addEventListener("click", 
          this.handleClick.bind(this));
  }
  Listener.prototype.handleClick = function (event) {
      console.log(this); //logs Listener {handleClick: function}
  }
  
  var listener = new Listener();
  document.getElementById("foo").click();
```

#### 六、HTML this
---

- 在`HTML`节点的属性里面，你可以放置`JavaScript`代码，`this`指向了这个元素

```javascript
<div id="foo" onclick="console.log(this);"></div>
 <script type="text/javascript">
 document.getElementById("foo").click(); //logs <div id="foo"...
 </script>
```

#### 七、override this
---

- 你不能重写`this`，因为它是保留字

```javascript
function test () {
     var this = {};  // Uncaught SyntaxError: Unexpected token this 
 }
eval this
```

- 你可以通过`eval`来访问`this`

```javascript
function Thing () {

}
Thing.prototype.foo = "bar";

Thing.prototype.logFoo = function () {
    eval("console.log(this.foo)"); //logs "bar"
}

var thing = new Thing();

thing.logFoo();
```
- 这会造成一个安全问题，除非不用`eval`，没有其他方式来避免这个问题

#### 八、with this
---

- 你可以通过`with`来将`this`添加到当前的执行环境，并且读写`this`的属性的时候不需要通过`this`

```javascript
 function Thing () {
  }
  Thing.prototype.foo = "bar";
  Thing.prototype.logFoo = function () {
      with (this) {
          console.log(foo);
          foo = "foo";
      }
  }
 
 var thing = new Thing();
 thing.logFoo(); // logs "bar"
 console.log(thing.foo); // logs "foo"
```
- 许多人认为这样使用是不好的因为`with`本身就饱受争议

#### 九、jQuery this
---

- 和`HTML DOM`元素节点的事件处理程序一样，在许多情况下`JQuery`的`this`都指向`HTML`元素节点。这在事件处理程序和一些方便的方法中都是管用的，比如`$.each`

```javascript

 <div class="foo bar1"></div>
 
 <div class="foo bar2"></div>
  
 <script type="text/javascript">
      $(".foo").each(function () {
          console.log(this); //logs <div class="foo...
      });
      $(".foo").on("click", function () {
          console.log(this); //logs <div class="foo...
      });
     $(".foo").each(function () {
         this.click();
     });
 </script>
```
