# 跨域	

## 1.什么是跨域(三种)

- 协议不同
- 域名不同
- 端口不同

## 2.jsonp

**jsonp为非标准属性,且只能支持get请求**

## 3.XMLHttpRequest Level 2

html5中新出现的

> 　	* 可以设置HTTP请求的时限。
>
> 　　* 可以使用FormData对象管理表单数据。
>
> 　　* 可以上传文件。
>
> 　　* 可以请求不同域名下的数据（跨域请求）。
>
> 　　* 可以获取服务器端的二进制数据。
>
> 　　* 可以获得数据传输的进度信息。

新版本的XMLHttpRequest对象，可以向不同域名的服务器发出HTTP请求。这叫做["跨域资源共享"](http://en.wikipedia.org/wiki/Cross-Origin_Resource_Sharing)（Cross-origin resource sharing，简称CORS）。

使用"跨域资源共享"的前提，是浏览器必须支持这个功能，而且服务器端必须同意这种"跨域"。如果能够满足上面的条件，则代码的写法与不跨域的请求完全一样。

> 　　xhr.open('GET', 'http://other.server/and/path/to/script');

目前，除了IE 8和IE 9，主流浏览器都支持CORS，IE 10也将支持这个功能。服务器端的设置，请参考[《Server-Side Access Control》](https://developer.mozilla.org/en-US/docs/Server-Side_Access_Control)。