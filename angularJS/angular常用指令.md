# 指令

- ng-bind
- ng-bind-html
- ng-repeat
- ng-class
- ng-if
- ng-hide
- ng-show
- ng-switch
- ng-src
- ng-href
- ng-focus
- ng-blur
- ng-dblclick

app.config

$loction相当于window.loction,能监视url地址栏

$location服务解析地址栏中的URL（基于window.location），让你在应用代码中能获取到。改变地址栏中的URL会反应$location服务中，反之亦然。

**$location服务**:

- 暴露当前地址栏的URL，这样你就能
  - 获取并监听URL。
  - 改变URL。
- 当出现以下情况时同步URL
  - 改变地址栏
  - 点击了后退按钮（或者点击了历史链接）
  - 点击了一个链接
- 一系列方法来获取URL对象的具体内容用（protocol, host, port, path, search, hash）.formatDate







$route:angular中最重要的路由,利用a标签锚点实现spa.

[AngularJS](https://docs.angularjs.org/)的[ng-route](http://docs.angularjs.cn/api/ngRoute/service/$route)模块为控制器和视图提供了[Deep-Linking]URL。 通俗来讲，[ng-route](http://docs.angularjs.cn/api/ngRoute/service/$route)模块中的`$route`Service监测`$location.url()`的变化，并将它映射到预先定义的控制器。也就是在客户端进行URL的路由。 下面首先给出`$route`的使用示例，然后引入一个更加强大的客户端路由框架[ui-router](https://github.com/angular-ui/ui-router)。

ng-view:注意到模板文件中有一个`div[ng-view]`，子页面将会载入到这里。



```JavaScript
$apply和$watch和$digest
在JavaScript中 有scope(作用域)和 context(上下文),angular中也是这样$scope和angular context
$watch是一个list,在
$disgest可以理解为一个轮询对$watch进行不停的查询,如果更改就局部动态刷新
$apply:如果当事件触发时，你调用$apply，它会进入angular context，如果没有调用就不会进入。(angular在事件中封装了这一步)

执行$apply-->执行$disgest-->查询$watch list
dirty-checking脏检查
angular使用的就是脏检查：
1不会脏检查所有的对象。当对象被绑定到html中后，这个对象才会添加为检查对象（watcher）
2不会脏检查所有的属性，同样当属性被绑定后，这个属性才会被列为检查的属性
在angular程序初始化时，会将绑定的对象的属性添加为监听对象（watcher），也就是说一个对象绑定了N个属性，就会添加N个watcher。
angular什么时候去脏检查呢？angular所系统的方法中都会触发比较事件，比如：controller初始化的时候，所有以ng-开头的事件爱你执行后，都会出发脏检查
必要的时候我们要手动的触发脏检查：$apply仅仅只是进入angular context，然后通过$digest触发脏检查
$apply如果不给参数的话，会检查该$scope里的所有监听的属性，推荐给上参数
```



```$/apply/+ ------- $watch```

- $      apply会使ng进入     ` $  digest cycle`, 并从$rootScope开始遍历(深度优先)检查数据变更。

```
$routeProvider
    //.when('/main',{
    //    template:'<h1>hhhhhh</h1>'
    //})
    .otherwise({
        redirectTo:'/in_theaters'
    })
```