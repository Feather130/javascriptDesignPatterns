### 创建函数的方法

如果使用这种方法创建函数会创建很多全局变量，在合作开发中可能会被他人定义同样的方法就会覆盖原有的功能

```javascript
function checkName(){}
function checkEmail(){}
function checkPassword(){}
```
可以使用对象收编变量，这样就只会创建一个全局变量，并且可以通过点语法使用对象
```javascript
var CheckObject = {
  checkName : function(){},
  checkEmail : function(){},
  checkPassword : function(){}
}
CheckObject.checkName()
```
也可以使用另一种方式声明，这两种声明方式不能结合使用，

```javascript
var CheckObject = function(){};
CheckObject.checkName = function(){}
CheckObject.checkEmail = function(){}
CheckObject.checkPassword = function(){}
```
但是这样写并没有办法做到复用，所以可以写成这样：

```javascript
var CheckObject = {
  return {
    checkName : function(){},
    checkEmail : function(){},
    checkPassword : function(){}
  }
}
var a = CheckObject();
a.checkName();
```

这样相当于每次调用都会返回一个新的对象，且不会互相影响

### 创建一个类的方法

```javascript
var CheckObject = function(){
  this.checkName = function(){}
  this.checkEmail = function(){}
  this.checkPassword = function(){}
}
var a =new CheckObject();
a.checkName();
```

这样创建的类就可以进行实例化了，新创建的对象都会对类的this上的属性进行复制。

```javascript
var checkObject = function(){};
checkObject.prototype = {
  checkName : function(){},
  checkEmail : function(){},
  checkPassword : function(){}
}
var a = new checkObject();
a.checkEmail();
```

这样创建对象实例的时候，创建出来的对象所拥有的方法就只有一个，他们都需要以来prototype原型依次查找

### 链式调用

```javascript
var CheckObject = function (){
  checkName : function(){
    return this;
  },
  checkEmail : function(){
    return this;
  },
  checkPassword : function(){
    return this;
  }
}
CheckObject.
```

