1.阻止事件冒泡和默认事件

```javascript
function stopBubble(e){ 
  if (e && e.stopPropagation)
    e.stopPropagation()    
    else       
      window.event.cancelBubble=true
  }
return false
```

2.改变this指向

- call（空参绑定window,多个参数啊a,b,c）
- apply（空参绑定window，多个参数[a,b,c]）
- bind（空参不执行）

3.gulp流程控制

- cb回调
- return流
- gulp-sequence插件

4.document.write和innerHTML区别

- document.write会触发浏览器重绘重排，性能问题。
- innerHTML是DOM页面元素的一个属性。可以精确的定位元素来修改。

5.js如何对一个对象进行深度克隆

```javascript
function deepClone(obj){
        var str = JSON.sringify(obj);
        var newobj = JSON.parse(str);
        return newobj;
    }
```

