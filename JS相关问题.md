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

6.一般需判断浏览器类型，需通过userAgent中获取浏览器内核

```
-moz代表firefox浏览器私有属性
-ms代表IE浏览器私有属性
-webkit代表chrome、safari私有属性 IE使用的是Trident内核，Firefox 使用的是Gecko内核。目前使用IE内核的浏览器还有搜狗，遨游，360等等。
```

7.cookie相关

客户端保存了不同服务器的cookie，每个服务器只能获取对应的cookie，而不能获取全部的

Cookie就是[服务器](http://www.zzbaike.com/wiki/%E6%9C%8D%E5%8A%A1%E5%99%A8)暂存放在你的电脑里的资料（.txt格式的文本文件），通过在[HTTP](http://www.zzbaike.com/wiki/HTTP)传输中的状态好让服务器用来辨认你的计算机。当你在浏览网站的时候，[Web](http://www.zzbaike.com/wiki/Web)服务器会先送一小小资料放在你的计算机上，Cookie 会帮你在网站上所打的文字或是一些选择都记录下来。当下次你再访问同一个网站，Web服务器会先看看有没有它上次留下的Cookie资料，有的话，就会依据Cookie里的内容来判断使用者，送出特定的[网页](http://www.zzbaike.com/wiki/%E7%BD%91%E9%A1%B5)内容给你。

    http请求是指从客户端到[服务器](http://baike.baidu.com/view/899.htm)端的请求消息。包括：消息首行中，对资源的请求方法、资源的标识符及使用的协议。

```
1.cookie是保存在客户端的
2.cookie是通过http请求报头传到服务器端
```