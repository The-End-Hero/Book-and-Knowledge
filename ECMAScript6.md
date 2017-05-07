# ES6

### let/const

- 块级作用域{},更加像静态语言java作用域的概念
- 顶层对象属性(浏览器大部分情况下是window,以后会统一起来用global)
- 相对于var来说,没有变量提升, 都需要先声明,再使用,
- 注意在函数中的隐藏的声明(比如console.log).

### 箭头函数 

- this的问题,应当理解为继承外层this(比如事件中一个ajax请求,利用箭头函数,可以直接使用外层this)
- 不要过度使用,最外层应该使用常规的function

### promise 

- 三种状态(Pending进行中,Resolved已完成,Rejected已失败)
- Promise代表一个异步操作
- ES6标准内置了,原先是CommendJS推荐的 
- 未来有async/await替代----->抄的C#的
- 使用频次最高的 .then()   .catch()
- setTimeout(()=>{},0)代表等队列执行完,立即执行.

```javascript
var fn = function(){
  setTimeout(()=>{
    console.log('set--0')
  },0)
  console.log('1')
  console.log('2')
  console.log('3')
  console.log('4')
}
fn() // 输出 1 2 3 4 set--0
```

###Array.from

- 让伪数组变成数组,类似类选择器 选的元素列表


### 模块化

- import极大的方便模块化
- export暴露接口

### class

react目前已经推荐使用class写法,比如 class Pop extend Component{//你的代码}



### 结构数据

##### 1.   ...   --->展开数组/对象