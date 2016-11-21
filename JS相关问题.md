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