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
- componentDidMount()   只会执行一次,不会反复
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

Link标签(to,query,hash,然后内部实现组成a标签的href)--->a标签    需要传递多值的时候,可以考虑使localstorage

多页面路由之间可以使用localStorge进行传值.



### 事件

直接console.log出来并没有什么卵用

onClick  

- target----事件触发目标的dom元素,已经能点击了,必然不是虚拟DOM

onTouchXXX

- touch-----pageX,Y   clientX,Y


性能上,绑定this,写在constructor里面





# React服务端渲染

React 提供了两个方法(react-dom核心包) `renderToString` 和 `renderToStaticMarkup` 用来将组件（Virtual DOM）输出成 HTML 字符串，这是 React 服务器端渲染的基础，它移除了服务器端对于浏览器环境的依赖，所以让服务器端渲染变成了一件有吸引力的事情。

服务器端渲染除了要解决对浏览器环境的依赖，还要解决两个问题：

- 前后端可以共享代码
- 前后端路由可以统一处理

React 生态提供了很多选择方案，这里我们选用 [Redux](http://rackt.org/redux/docs/introduction/index.html) 和 [react-router](https://github.com/rackt/react-router) 来做说明。

## Redux

[Redux](http://rackt.org/redux/docs/introduction/index.html) 提供了一套类似 Flux 的单向数据流，整个应用只维护一个 Store，以及面向函数式的特性让它对服务器端渲染支持很友好。

### 2 分钟了解 Redux 是如何运作的

关于 Store：

- 整个应用只有一个唯一的 Store
- Store 对应的状态树（State），由调用一个 reducer 函数（root reducer）生成
- 状态树上的每个字段都可以进一步由不同的 reducer 函数生成
- Store 包含了几个方法比如 `dispatch`, `getState` 来处理数据流
- Store 的状态树只能由 `dispatch(action)` 来触发更改 !!!!!!!!!非常重要

Redux 的数据流：

- action 是一个包含 `{ type, payload }` 的对象
- reducer 函数通过 `store.dispatch(action)` 触发    !!!!!!!!!非常重要
- reducer 函数接受 `(state, action)` 两个参数，返回一个新的 state
- reducer 函数判断 `action.type` 然后处理对应的 `action.payload` 数据来更新状态树

所以对于整个应用来说，一个 Store 就对应一个 UI 快照，服务器端渲染就简化成了在服务器端初始化 Store，将 Store 传入应用的根组件，针对根组件调用 `renderToString` 就将整个应用输出成包含了初始化数据的 HTML。

## react-router

[react-router](https://github.com/rackt/react-router) 通过一种声明式的方式匹配不同路由决定在页面上展示不同的组件，并且通过 props 将路由信息传递给组件使用，所以只要路由变更，props 就会变化，触发组件 re-render。

假设有一个很简单的应用，只有两个页面，一个列表页 `/list` 和一个详情页 `/item/:id`，点击列表上的条目进入详情页。

可以这样定义路由，`./routes.js`

```
import React from 'react';
import { Route } from 'react-router';
import { List, Item } from './components';

// 无状态（stateless）组件，一个简单的容器，react-router 会根据 route
// 规则匹配到的组件作为 `props.children` 传入
const Container = (props) => {
  return (
    <div>{props.children}</div>
  );
};

// route 规则：
// - `/list` 显示 `List` 组件
// - `/item/:id` 显示 `Item` 组件
const routes = (
  <Route path="/" component={Container} >
    <Route path="list" component={List} />
    <Route path="item/:id" component={Item} />
  </Route>
);

export default routes;
```

从这里开始，我们通过这个非常简单的应用来解释实现服务器端渲染前后端涉及的一些细节问题。

## Reducer

Store 是由 reducer 产生的，所以 reducer 实际上反映了 Store 的状态树结构

`./reducers/index.js`

```
import listReducer from './list';
import itemReducer from './item';

export default function rootReducer(state = {}, action) {
  return {
    list: listReducer(state.list, action),
	item: itemReducer(state.item, action)
  };
}
```

`rootReducer` 的 `state` 参数就是整个 Store 的状态树，状态树下的每个字段对应也可以有自己的reducer，所以这里引入了 `listReducer` 和 `itemReducer`，可以看到这两个 reducer的 state 参数就只是整个状态树上对应的 `list` 和 `item` 字段。

具体到 `./reducers/list.js`

```
const initialState = [];

export default function listReducer(state = initialState, action) {
  switch(action.type) {
  case 'FETCH_LIST_SUCCESS': return [...action.payload];
  default: return state;
  }
}
```

list 就是一个包含 items 的简单数组，可能类似这种结构：`[{ id: 0, name: 'first item'}, {id: 1, name: 'second item'}]`，从 `'FETCH_LIST_SUCCESS'` 的 `action.payload` 获得。

然后是 `./reducers/item.js`，处理获取到的 item 数据

```
const initialState = {};

export default function listReducer(state = initialState, action) {
  switch(action.type) {
  case 'FETCH_ITEM_SUCCESS': return [...action.payload];
  default: return state;
  }
}
```

## Action

对应的应该要有两个 action 来获取 list 和 item，触发 reducer 更改 Store，这里我们定义 `fetchList` 和 `fetchItem` 两个 action。

`./actions/index.js`

```
import fetch from 'isomorphic-fetch';

export function fetchList() {
  return (dispatch) => {
    return fetch('/api/list')
		.then(res => res.json())
		.then(json => dispatch({ type: 'FETCH_LIST_SUCCESS', payload: json }));
  }
}

export function fetchItem(id) {
  return (dispatch) => {
    if (!id) return Promise.resolve();
    return fetch(`/api/item/${id}`)
		.then(res => res.json())
		.then(json => dispatch({ type: 'FETCH_ITEM_SUCCESS', payload: json }));
  }
}
```

[isomorphic-fetch](https://github.com/matthew-andrews/isomorphic-fetch) 是一个前后端通用的 Ajax 实现，前后端要共享代码这点很重要。

另外因为涉及到异步请求，这里的 action 用到了 thunk，也就是函数，redux 通过 `thunk-middleware` 来处理这类 action，把函数当作普通的 action dispatch 就好了，比如 `dispatch(fetchList())`

## Store

我们用一个独立的 `./store.js`，配置（比如 Apply Middleware）生成 Store

```
import { createStore } from 'redux';
import rootReducer from './reducers';

// Apply middleware here
// ...

export default function configureStore(initialState) {
  const store = createStore(rootReducer, initialState);
  return store;
}
```

## react-redux

接下来实现 `<List>`，`<Item>` 组件，然后把 redux 和 react 组件关联起来，具体细节参见 [react-redux](https://github.com/rackt/react-redux)

`./app.js`

```
import React from 'react';
import { render } from 'react-dom';
import { Router } from 'react-router';
import createBrowserHistory from 'history/lib/createBrowserHistory';
import { Provider } from 'react-redux';
import routes from './routes';
import configureStore from './store';

// `__INITIAL_STATE__` 来自服务器端渲染，下一部分细说
const initialState = window.__INITIAL_STATE__;
const store = configureStore(initialState);
const Root = (props) => {
  return (
    <div>
      <Provider store={store}>
        <Router history={createBrowserHistory()}>
          {routes}
        </Router>
      </Provider>
    </div>
  );
}

render(<Root />, document.getElementById('root'));
```

至此，客户端部分结束。

## Server Rendering

接下来的服务器端就比较简单了，获取数据可以调用 action，routes 在服务器端的处理参考 [react-router server rendering](https://github.com/rackt/react-router/blob/master/docs/guides/advanced/ServerRendering.md)，在服务器端用一个 `match` 方法将拿到的 request url 匹配到我们之前定义的 routes，解析成和客户端一致的 props 对象传递给组件。

`./server.js`

```
import express from 'express';
import React from 'react';
import { renderToString } from 'react-dom/server';
import { RoutingContext, match } from 'react-router';
import { Provider } from 'react-redux';
import routes from './routes';
import configureStore from './store';

const app = express();

function renderFullPage(html, initialState) {
  return `
    <!DOCTYPE html>
    <html lang="en">
    <head>
      <meta charset="UTF-8">
    </head>
    <body>
      <div id="root">
        <div>
          ${html}
        </div>
      </div>
      <script>
        window.__INITIAL_STATE__ = ${JSON.stringify(initialState)};
      </script>
      <script src="/static/bundle.js"></script>
    </body>
    </html>
  `;
}

app.use((req, res) => {
  match({ routes, location: req.url }, (err, redirectLocation, renderProps) => {
    if (err) {
      res.status(500).end(`Internal Server Error ${err}`);
    } else if (redirectLocation) {
      res.redirect(redirectLocation.pathname + redirectLocation.search);
    } else if (renderProps) {
      const store = configureStore();
      const state = store.getState();

      Promise.all([
        store.dispatch(fetchList()),
        store.dispatch(fetchItem(renderProps.params.id))
	  ])
      .then(() => {
        const html = renderToString(
          <Provider store={store}>
            <RoutingContext {...renderProps} />
          </Provider>
        );
        res.end(renderFullPage(html, store.getState()));
      });
    } else {
      res.status(404).end('Not found');
    }
  });
});
```

服务器端渲染部分可以直接通过共用客户端 `store.dispatch(action)` 来统一获取 Store 数据。另外注意 `renderFullPage` 生成的页面 HTML 在 React 组件 mount 的部分(`<div id="root">`)，前后端的 HTML 结构应该是一致的。然后要把 `store` 的状态树写入一个全局变量（`__INITIAL_STATE__`），这样客户端初始化 render 的时候能够校验服务器生成的 HTML 结构，并且同步到初始化状态，然后整个页面被客户端接管。

### 最后关于页面内链接跳转如何处理？

react-router 提供了一个 `<Link>` 组件用来替代 `<a>` 标签，它负责管理浏览器 history，从而不是每次点击链接都去请求服务器，然后可以通过绑定 `onClick` 事件来作其他处理。

比如在 `/list` 页面，对于每一个 item 都会用 `<Link>` 绑定一个 route url：`/item/:id`，并且绑定 `onClick` 去触发 `dispatch(fetchItem(id))` 获取数据，显示详情页内容。