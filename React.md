### JSX

JSX是第三方标准,但是这套标准适合任何一套框架

JSTransform(react官方,不再维护),全部采用babel的JSX编译器

JSX的官方定义是类XML语法的ECMAScript扩展

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
- ​



















