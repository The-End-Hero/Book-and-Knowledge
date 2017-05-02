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