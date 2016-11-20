回流(reflows)与重绘(repaints)

1.如何避免回流或者将它们对性能的影响降到最小

- 如果想设定元素的样式，**通过改变元素的 class 名 ** (尽可能在 DOM 树的最末端)（Change classes on the element you wish to style (as low in the dom tree as possible)）
- 避免设置多项内联样式（Avoid setting multiple inline styles）
- 应用元素的动画，使用 position 属性的**fixed 值或 absolute 值**（Apply animations to elements that are position fixed or absolute）
- 权衡平滑和速度（Trade smoothness for speed）
- 避免使用table布局（Avoid tables for layout）
- 避免使用CSS的JavaScript表达式 (仅 IE 浏览器)（Avoid JavaScript expressions in the CSS (IE only)）

2.直接使用CSS3动画库确实比用js特效要平顺许多,尤其是对于很大块级标签.

3.图片压缩---智图在线压缩（渐进式）

4.精灵图。

5.SVG图标。

6.base64（小图使用，避免大图，减少http请求，但是会变大）



- content方面
  1. 减少HTTP请求：合并文件、CSS精灵、inline Image
  2. 减少DNS查询：DNS查询完成之前浏览器不能从这个主机下载任何任何文件。方法：DNS缓存、将资源分布到恰当数量的主机名，平衡并行下载和DNS查询
  3. 避免重定向：多余的中间访问
  4. 使Ajax可缓存
  5. 非必须组件延迟加载
  6. 未来所需组件预加载
  7. 减少DOM元素数量
  8. 将资源放到不同的域下：浏览器同时从一个域下载资源的数目有限，增加域可以提高并行下载量
  9. 减少iframe数量
  10. 不要404
- Server方面
  1. 使用CDN
  2. 添加Expires或者Cache-Control响应头
  3. 对组件使用Gzip压缩
  4. 配置ETag
  5. Flush Buffer Early
  6. Ajax使用GET进行请求
  7. 避免空src的img标签
- Cookie方面
  1. 减小cookie大小
  2. 引入资源的域名不要包含cookie
- css方面
  1. 将样式表放到页面顶部
  2. 不使用CSS表达式
  3. 使用不使用@import
  4. 不使用IE的Filter
- Javascript方面
  1. 将脚本放到页面底部
  2. 将javascript和css从外部引入
  3. 压缩javascript和css
  4. 删除不需要的脚本
  5. 减少DOM访问
  6. 合理设计事件监听器
- 图片方面
  1. 优化图片：根据实际颜色需要选择色深、压缩
  2. 优化css精灵
  3. 不要在HTML中拉伸图片
  4. 保证favicon.ico小并且可缓存
- 移动方面
  1. 保证组件小于25k
  2. Pack Components into a Multipart Document

