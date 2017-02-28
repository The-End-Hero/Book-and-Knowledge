###  JSX

JSX是第三方标准,但是这套标准适合任何一套框架

JSTransform(react官方,不再维护),全部采用babel的JSX编译器

JSX的官方定义是类XML语法的ECMAScript扩展(然而在webpack等强大的工具下，className／for非必要。)

- 定义标签是只允许被一个标签包裹
- 标签一定要闭合,**只能有一个顶层标签**.
- 小写首字母对应DOM元素,而**组件**元素对应**大写**首字母
- 在一个组件的子元素位置使用注释要用{}包起来.
- 条件注释(例如IE兼容),JavaScript判断浏览器版本来替代
- DOCTYPE-->保存变量,渲染后**串**起来.
- class-->className    for-->htmlFor    JS的 关键字
- 些自定义属性的时候由标准写法改为小驼峰写法(data-id-->dataId)
- Boolean值,如果**不写默认false**,写了**未定义,默认true**
- 展开属性-->ES6rest/spread特性
- JSX是HTML和JavaScript混写的语法，当遇到**<**，JSX就当HTML解析，遇到**{**就当JavaScript解析.
- 自定义属性,data-xxx,aria-xxx
- 防止XSS攻击,html被转义,如果实在是需要的话,可以使用dangerouslySetInnerHTML属性.
- `this.props.children` 的值有三种可能：如果当前组件没有子节点，它就是 `undefined` ;如果有一个子节点，数据类型是 `object` ；如果有多个子节点，数据类型就是 `array` 。所以，处理 `this.props.children` 的时候要小心.
- React 提供一个工具方法 [`React.Children`](https://facebook.github.io/react/docs/top-level-api.html#react.children) 来处理 `this.props.children` 。我们可以用 `React.Children.map` 来遍历子节点，而不用担心 `this.props.children` 的数据类型是 `undefined` 还是 `object`。更多的 `React.Children` 的方法，请参考[官方文档](https://facebook.github.io/react/docs/top-level-api.html#react.children).
- 真实DOM节点  虚拟DOM节点,DOM diff算法,目前大量使用,减少重排重绘.在很多时候需要获取DOM的真实节点,得到类似用户输入信息.我们需要用到ref属性,this.ref.[xxx]是获取的真实DOM,需要等虚拟DOM插入后才能使用,否则会报错.  所以可以利用事件回调函数.
- React 组件支持很多事件，除了 `Click` 事件以外，还有 `KeyDown` 、`Copy`、`Scroll` 等，完整的事件清单请查看[官方文档](http://facebook.github.io/react/docs/events.html#supported-events)。
- 由于 `this.props` 和 `this.state` 都用于描述组件的特性，可能会产生混淆。一个简单的区分方法是，`this.props` 表示那些一旦定义，就不再改变的特性，而 `this.state` 是会随着用户互动而产生变化的特性。
- 组件的数据来源，通常是通过 Ajax 请求从服务器获取，可以使用 `componentDidMount` 方法设置 Ajax 请求，等到请求成功，再用 `this.setState` 方法重新渲染 UI 




### 组件生命周期

#### 三种状态

- Mounting：已插入真实DOM
- Updating：正在被重新渲染
- Unmouting：已移出真实DOM

每种状态下有两种处理函数will和did

- componentWillMount()
- componentDidMount()
- componentWillUpdate(object nextProps, object nextState)
- componentDidUpdate(object prevProps, object prevState)
- componentWillUnmount()




### redux

进行状态管理

组件之间的通信-->父子/兄弟

- 只有两层的情况,父组件全部使用state数据源(方便维护),在子组件中可以使用props,这样父组件setState,子组件全部改变.
- 子组件利用回调改变父组件的state值,再进行setState
- setState本身是异步的,直接console.log  未改变值

基于flux

整个react都是所谓的状态驱动UI改变

react-redux是核心文件

### node中间件

express服务  

转发api-->json

ssr服务器渲染(Server Side Render)

![SSR](C:\GitHub\BOOK-and-knowledge-point\images\SSR.png)

### route

react-route---->(maybe)react-keep

单页面应用(SPA)

基于History

按需加载

Link标签(to,query,hash,然后内部实现组成a标签的href)--->a标签



### 事件

直接console.log出来并没有什么卵用

onClick  

- target----事件触发目标的dom元素,已经能点击了,必然不是虚拟DOM

onTouchXXX

- touch-----pageX,Y   clientX,Y

