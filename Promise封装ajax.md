```
function ajax(url) {
  return new Promise(function(resolve, reject){
    var xml = new XMLHttpRequest();
    xml.open('get',url,true);
    xml.onload = resolve;
    xml.onerror = reject;
    xml.send();
  } )
}
```

```
ajax(url).then(function(response)).catch(function(err))
```
从上面的解释中可以知道：`ajax`是一种技术方案，但并不是一种**新技术**。它依赖的是现有的`CSS`/`HTML`/`Javascript`，而其中最核心的依赖是浏览器提供的`XMLHttpRequest`对象，是这个对象使得浏览器可以发出`HTTP`请求与接收`HTTP`响应。

所以我用一句话来总结两者的关系：我们使用`XMLHttpRequest`对象来发送一个`Ajax`请求。

## `XMLHttpRequest`的发展历程

`XMLHttpRequest`一开始只是微软浏览器提供的一个接口，后来各大浏览器纷纷效仿也提供了这个接口，再后来W3C对它进行了标准化，提出了[`XMLHttpRequest`标准](https://www.w3.org/TR/XMLHttpRequest/)。`XMLHttpRequest`标准又分为`Level 1`和`Level 2`。
`XMLHttpRequest Level 1`主要存在以下缺点：

- 受同源策略的限制，不能发送跨域请求；
- 不能发送二进制文件（如图片、视频、音频等），只能发送纯文本数据；
- 在发送和获取数据的过程中，无法实时获取进度信息，只能判断是否完成；

那么`Level 2`对`Level 1` 进行了改进，`XMLHttpRequest Level 2`中新增了以下功能：

- 可以发送跨域请求，在服务端允许的情况下；
- 支持发送和接收二进制数据；
- 新增formData对象，支持发送表单数据；
- 发送和获取数据时，可以获取进度信息；
- 可以设置请求的超时时间；

当然更详细的对比介绍，可以参考[阮老师的这篇文章](http://www.ruanyifeng.com/blog/2012/09/xmlhttprequest_level_2.html)，文章中对新增的功能都有具体代码示例。

- IE8/IE9、Opera Mini 完全不支持`xhr`对象
- IE10/IE11部分支持，不支持 `xhr.responseType`为`json`
- 部分浏览器不支持设置请求超时，即无法使用`xhr.timeout`
- 部分浏览器不支持`xhr.responseType`为`blob`