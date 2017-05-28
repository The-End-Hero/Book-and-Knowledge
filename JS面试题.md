### 一道容易被人轻视的面试题

```javascript
function Foo() {
    getName = function () { alert (1); };
    return this;
}
Foo.getName = function () { alert (2);};
Foo.prototype.getName = function () { alert (3);};
var getName = function () { alert (4);};
function getName() { alert (5);}

//请写出以下输出结果：
Foo.getName();
getName();
Foo().getName();
getName();
new Foo.getName();
new Foo().getName();
new new Foo().getName();
```

### 闭包小题

```javascript
for(var i = 0; i < 5; i++) {
    console.log(i);
}

for(var i = 0; i < 5; i++) {
    setTimeout(function() {
        console.log(i);
    }, 1000 * i);
}

for(var i = 0; i < 5; i++) {
    (function(i) {
        setTimeout(function() {
            console.log(i);
        }, i * 1000);
    })(i);
}

for(var i = 0; i < 5; i++) {
    (function() {
        setTimeout(function() {
            console.log(i);
        }, i * 1000);
    })(i);
}

for(var i = 0; i < 5; i++) {
    setTimeout((function(i) {
        console.log(i);
    })(i), i * 1000);
}

setTimeout(function() {
  console.log(1)
}, 0);
new Promise(function executor(resolve) {
  console.log(2);
  for( var i=0 ; i<10000 ; i++ ) {
    i == 9999 && resolve();
  }
  console.log(3);
}).then(function() {
  console.log(4);
});
console.log(5);
```

### 函数的隐式转换

```javascript
function fn() {
    return 20;
}
console.log(fn + 10); // 输出结果是多少

function fn() {
    return 20;
}

fn.toString = function() {
    return 10;
}

console.log(fn + 10);  // 输出结果是多少？

function fn() {
    return 20;
}

fn.toString = function() {
    return 10;
}

fn.valueOf = function() {
    return 5;
}

console.log(fn + 10); // 输出结果是多少？
```

### 函数防抖和函数节流(ES6)

```javascript
//函数节流
const throttle = (fun, delay) => {
    let last = null;
    return () => {
        const now = + new Date();
        if (now - last > delay) {
            fun();
            last = now;
        }
    }
}
//实例
const throttleExample  = throttle(() => console.log(1), 1000);
//调用
throttleExample();
throttleExample();
throttleExample();
//函数防抖
cosnt debouce = (fun, delay) => {
    let timer = null;
    return () => {
        clearTimeout(timer);
        timer = setTimeout(() => {
            fun();
        }, delay);
    }
}
//实例
const debouceExample = debouce(() => console.log(1), 1000);
//调用
debouceExample();
debouceExample();
debouceExample();
```

闭包

```javascript
var a = 0;
var b = 0;
function A(a) {
    A = function(b) {
        console.log('a+b=' + (a + b++));
    }
    console.log('a=' + a++);
}
// 第一次调用A时，执行到console.log('a=' + a++)时，a已经完成自加，此时a的值为2，a++的值为1。
A(1);
// 第二次调用A时，A已经被重新赋值，指向了一个新的函数引用；
// 由于标识符A是在全局作用域定义的，所以在函数内部被重新赋值，在全局作用域也可以访问到重新赋值后的函数。此时，也创建了一个闭包，该闭包保存了创建环境的活动对象。
// 此时活动对象：{ a: 2 }，同时，根据传入的数值2,确定 b = 2，b++值为3。
// 执行到 console.log('a+b=' + (a + b++))，故而输出4
A(2);


var a = 0;
    var b = 0;

    function A(a) {
        B = function(b) {
            console.log('a+b=' + (a + b++));
        }
        console.log('a=' + a++);
    }
    A(1);
    B(2);//这样你应该可以看得明白点

```

js实现：一个数组，把奇数放到右边，偶数放到左边，不许使用额外空间。

```javascript
let A = arr=>arr.sort(x=>x % 2 == 0)
```
# 闭包相关

以下皆为**es5的情况**下:

```javascript
function A(){
  var C = 1
  return function B(){
    console.log(C)
  }
}
A()()
```

1. 只有函数才能创建作用域
2. 函数调用完成,即被销毁
3. 当函数A中另一个函数B对A函数作用域 变量C进行引用时,即形成闭.
   1. 所谓闭包就是在函数A被调用完成以后,函数A中的C因为函数B的引用,所以继续保存在内存中.