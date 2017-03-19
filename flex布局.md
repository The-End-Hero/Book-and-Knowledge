# 使用flex-----优雅降级  flex-->flex-box-->box

###容器有6个属性可以设置

1. #### flex-direction 主轴的方向(即项目的排列方向)

- row（默认值）：主轴为水平方向，起点在左端。
- row-reverse：主轴为水平方向，起点在右端。
- column：主轴为垂直方向，起点在上沿。
- column-reverse：主轴为垂直方向，起点在下沿。



2. ####  flex-wrap 定义在轴线上换行相关
- nowrap(默认):不换行
- wrap: 换行
- wrap-reverse: 换行,并且第一行在下方



3. ####  flex-flow 是flex-direction和flex-wrap的简写形式,默认值为row nowrap
- flex-flow: flex-direction || flex-wrap;



4. ####  justify-content 定义了主轴方向的对齐方式 
- flex-start（默认值）：左对齐
- flex-end：右对齐
- center： 居中
- space-between：两端对齐，项目之间的间隔都相等。
- space-around：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。



5. ####  align-items  定义项目在交叉轴上如何对齐。
- flex-start：交叉轴的起点对齐。
- flex-end：交叉轴的终点对齐。
- center：交叉轴的中点对齐。
- baseline: 项目的第一行文字的基线对齐。
- stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。



6. ####  align-content  定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。
- flex-start：与交叉轴的起点对齐。
- flex-end：与交叉轴的终点对齐。
- center：与交叉轴的中点对齐。
- space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。
- space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
- stretch（默认值）：轴线占满整个交叉轴。



###容器内的项目有6个属性可以设置
1.  order 规定项目的排列顺序,值越小,排列越靠前,值默认为0
2.  flex-grow  定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。
3.  flex-shrink  定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。
4.  flex-basis  定义了在分配多余空间之前，项目占据的主轴空间（main size）。
5.  flex  flex属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。
6.  align-self  align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。