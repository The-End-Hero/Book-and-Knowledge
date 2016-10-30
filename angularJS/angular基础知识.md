# angular的特性

- 双向数据绑定
- 指令系统
- MVVM设计模式
- 多模块化开发
- 依赖注入

# 表达式

-什么是表达式

- 表达式的形式有很多种都是通过｛｛｝｝包裹起来，最后将运算结果返回出去
  - 字符串 {{string}}
    - 数字 {{number}}
    - 布尔 {{boolean}}
    - 三元表达式 {{?:}}
    - 数组 {{arrary}}
    - 对象 {{object}} 

# 指令

- 什么是指令
  指令就是Angular对原有HTML的拓展属性，并且以ng-开头
- ng-app: 表示Angular程序从这里开始，里面所有与Angular有关的代码将被执行
- ng-init：初始化参数
- ng-model：用来将参数绑定到value中
- ng-bind：相当于innerHTML绑定到标签中
- ng-click：相当于click事件

# JqLite使用

- Angular的dom操作
  - 在Angular对于宏观的dom处理非常不错但是对于细小的操作Angular就需要借助内置的JqLite进行操作
  - JqLite分两种情况
    - 有Jquery时，作为Angular检测到Jquery时候会将其引用过来
      - 无Jquery时，作为Angular就会启用自身的JqLite使用，使用方法基本一样

# angular的特性：

```
1.双向数据绑定
```

# 解决angular闪一闪的问题解决办法

```
+ 1.把angularjs的引用写在上面（不推荐）
+ 2.添加ng-cloak隐藏代码
+ 3.自己添加 
    [ng-cloak]{
        display:none
    }
	样式
+ 4.通过指令的方式写angular代码，不考虑使用表达式的形式
```

# 写angular代码的顺序

- 1.引用angularjs的包
- 2.创建模块和控制器
  - 3.暴露参数和暴露行为
  - 4.划定angular的管理范围需要配合指令ng-app加模块的名称，ng-controller加控制器的名称
  - 5.将暴露的行为或者参数绑定到对应的位置

# angular的执行顺序

- 1.如果没有模块，在angular内部会帮我们创建模块
- 2.如果由模块就加载模块中的内容和控制器中的内容
  - 3.将模块中的内容加载到angular中去
  - 4.angular就会去寻找ng-app(可以看作是angular的起点，同时也是angular的管理范围)
  - 5.这时候angular才回去解析ng-app中有关angular的代码

# 模块和控制器的注意：

- 1.如果在没有特殊的情况下angular处理模块只会处理第一个，后面的将不会被执行
- 2.控制器需要放在指定的模块范围内才会进行处理
  - 3.能够有多个控制器

# 依赖注入

- 没事你不要来找我，有事我会去找你。
- 原理
   框架在调用方法的过程中通过获取到传递的参数，然后框架内部将方法toString处理以后，
   再通过正则表达式将其获取到然后依次实例化。

# MVVM设计模式

- 什么是MVVM设计模式
  - Model（模型）
  - View （视图）
  - ViewModel （视图模型）
  - 由上面三个部分组成其中ViewModel就是$scope起到桥梁的作用将Model和View联系起来
  - MVVM模式是Model-View-ViewMode（模型-视图-视图模型）模式的简称，其最早出现在微软的WPF和Silverlight框架中，使用ViewModel（视图模型）来实现View和Model的粘合，同时让View和Model的进一步分离。方便美工和程序员职能分离。
- MVVM本质
  - 其本质就是为了代码模块化
    - 模块化的好处是逻辑清晰、维护方便但是同时也会增加代码量和开发成本

# 自定义指令

- 什么是自定义指令

  - 通过在module下创建**diretive**设置自定义指令
  - 自定义指令有可以将复杂的html代码封装成一个标签或者属性，方便程序员使用。

- 自定义指令的创建

  - 语法：app.directive('指令的名字',第二个参数是个数组，写法类似于controller第二个参数)  `app.directive('myBtn',[function(){}])`
  - 注意：指令的名字需要使用驼峰命名法来命名，我们在使用的时候，需要把所有的大小转换成小写，并且在原先大小之间加上- 。(类似jQurey中z-index写成zIndex)

- 自定义指令中属性

  - template:'指定一个html字符串，最终angular会把这个字符串渲染到页面上，我们书写自定义指令所在标签的innerHTML位置'
  - templateUrl:也是指定一个字符串，只是这个字符串是一个路径，最终angular会帮助我们去请求这个文件，然后把这个文件的内容当作模板字符串插入到页面中。
  - 可以用第二种用法：值可以是一个script标签的id,只需要把这个script标签的type属性设置为"text/ng-template",最终angular会把这个标签里的内容当作html字符渲染到自定义指令所在标签
  - angular优先会把对应的属性值当作script标签的id来识别，如果没有这个id,就会把这个属性值当作一个路径去请求.
  - restrict : 指定angualr自定义指令的使用方式
    - 'A' : 表示只能以属性的形式使用
    - 'E' : 表示只能以自定义标签的形式使用   <my-Btn></my-Btn>
    - 'C' : 表示只能以类样式的形式使用 ng-cloak 


  - replace: 需要一个布尔值：当为true时表示，angular会用tempate所指定的模板字符串替换自定义指令所在标签。

  - transclude: 转置，需要一个布尔值，为true时，会将自定义指令所在标签的innerHTML位置的字符串添加到模板字符串中拥有ng-trasclude指令的标签的innerHTML位置,

  - scope: 需要提供一个对象,用来获取自定义指令所在标签的属性值,

    ```JavaScript
    `{
        tmp:'@,获取自定义指令所在标签的名为tmp的的属性值 
    }`
    ```

  - link:需要提供一个function,这个function有三个参数

    - scope,可以暴露一些属性给模板字符串使用，与控制器里的$scope有点类似
      但是，它暴露的属性只能在模板字符串中使用，不能在整个视图使用。
    - element: 就是angular为我们获取的自定义指令所在标签的jqLite对象
    - attrriubtes: 这是一个object对象，里面包含了所有自定义指令所在标签的属性值。 

# 过滤器

- 什么是过滤器

  - 过滤器（filter）正如其名，作用就是接收一个输入，通过某个规则进行处理，然后返回处理后的结果。主要用在数据的格式化上，例如获取一个数组中的子集，对数组中的元素进行排序等。ng内置了一些过滤器，它们是：currency(货币)、date(日期)、filter(子串匹配)、json(格式化json对象)、limitTo(限制个数)、lowercase(小写)、uppercase(大写)、number(数字)、orderBy(排序)。

- Angular官方的过滤器

  - currency(货币)
    - {{1000 | currency:"USD$":0}} 
      +date(日期)
    - {{'1288323623006' | date:"MM/dd/yyyy 'at' h:mma"}}
      +json(格式化json对象)
    - ` <pre >{{ {'name':'value'} | json }}</pre>  `
      +limitTo(限制个数)
    - {{ numbers | limitTo:numLimit }}
      +lowercase(小写)
    - {{ lowercase_expression | lowercase}}
      +uppercase(大写)
    - {{ uppercase_expression | uppercase}}
      +number(数字)
    - {{1234 | number:0}}
      +orderBy(排序)
      +filter(子串匹配)


  - 自定义过滤器


  - ​

    ```JavaScript
    app.filter("myUpperCase",function () {
    	return function (data) {
        	return data.toUpperCase();
    	}
    }); 
    ```

### JSON

- 如何将JSON对象转换成字符串
  JSON.parse(JSON字符串)
- 如何将字符串转换成JSON对象
- JSON.stringify(JSON对象)

# 如何保存数据

- localStorage进行存储数据
  - localStorage中一般浏览器支持的是5M大小，这个在不同的浏览器中localStorage会有所不同。
    localStorage 方法存储的数据没有时间限制。第二天、第二周或下一年之后，数据依然可用。
- localStorage的用法
  - localStorage 通过不同的key来管理每一条的数据，存储的数据只能用来用存储字符串的数据
  - localStorage['key']  获取对应的key中的数据
  - localStorage.getItem('key') 也能获取到key中的数据
  - localStorage.setItem('key','value') key是每条数据的表示， value是每条字符串的数据

# 单页面应用程序

- 什么是单页面应用程序
  单页Web应用（single page web application，SPA），就是只有一张Web页面的应用。单页应用程序 (SPA) 是加载单个HTML 页面并在用户与应用程序交互时动态更新该页面的Web应用程序。[1]  浏览器一开始会加载必需的HTML、CSS和JavaScript，所有的操作都在这张页面上完成，都由JavaScript来控制。因此，对单页应用来说模块化的开发和设计显得相当重要。**(比如阿里云的控制台)**
- 好处与坏处
  - 好处：
    - 对于用户而言，更好的用户体验，特别体现在可移动端和可触摸设备上
    - 结构清晰、易于维护
  - 坏处：
    - 不利于SEO优化
    - 代码量增加
    - 单页面应用程序原理
      通过监视页面的锚点值变化的不同进行判断以后，然后进行处理通常是发送AJAX异步请求，拿到数据以后再将数据渲染到页面中。
      window.addEventListener('hashchange',function () { console.log(location.hash)}
- Angular中单页面应用程序的实现
  在Angular中通过使用**angular-route模块**实现单页面应用程序
  路由初步使用
  - 引入了一个路由模块ngRoute
    - npm安装 `npm install angular-route --save`
  - 通过 app.config方法来进行路由的配置
    - config,只需要一个参数，就是一个数组，类似开controller方法的第二个参数，也是使用了注入了方式传入参数，
    - redirectTo 用来重新定向跳转到之前的规则中。
      - $routeProvider 来书写一些具体的规则
      - $routeProvider.when(url中锚点值不包含#号,第二个参数是一个object对象) 
        - templateUrl : 指定一个文件路径或者script标签的id,类似于自定义指令中的templateUrl
        - controller :指定一个控制器名，表示这里的模板字符串由这个控制器来管理，注意：这里所指定的控制器里通过$scope暴露出来的数据，只能够在这个模板字符串中使用。
  - templateUrl指定的模板字符串会插入到页面上拥有ng-view指定所在标签的innerHTML位置
  - ng-view只需要使用一次

# Api和WebApi

- Api:  
  - Application Programming Interface, 应用程序编程接口
  - 通常是指方法的集合
- WebApi: 
  - Web Application Programming Interface, 网络应用程序编程接口
  - 通常是指通过发送get、post数据请求不同路径获取数据
- 常用Api和WebApi
  - 百度地图：http://lbsyun.baidu.com/
  - 百度api：http://apistore.baidu.com/
  - 豆瓣api：https://developers.douban.com/wiki/?title=api_v2
- 常用检测工具PostMan

# Angular的数据请求

- Angular是一个前端框架，实现了可交互式的页面，但是对于一个web应用，页面上进行展示的数据从哪里来，肯定需要服务端进行支持，那么Angular是如何同服务端进行交互的呢？
  Angular提供了\$$http服务来同服务端进行通信，$http服务队浏览器的XMLHttpRequest对象进行了封装，让我们可以以ajax的方式来从服务器请求数据。
  $http服务是一个接受一个参数的函数，参数的类型是对象，用来配置生成的http的请求，该函数返回一个promise对象
  （关于promise规范，可以看看[这篇文章](http://www.cnblogs.com/fsjohnhuang/p/4139172.html)）