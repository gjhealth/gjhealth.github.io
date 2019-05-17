---
title: Flex布局
date: 2019-05-17 17:11:34
tags:
  - HTML
  - 布局
categories:
  - 前端
author: 毕帅
---

# 1. 基本概念

> 采用Flex布局的元素，称为Flex容器（flex container），简称”容器”。它的所有子元素自动成为容器成员，称为Flex项目（flex item）。

![5cdccefa0e34271570](https://i.loli.net/2019/05/16/5cdccefa0e34271570.png)容器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis）。主轴的开始位置（与边框的交叉点）叫做main start，结束位置叫做main end；交叉轴的开始位置叫做cross start，结束位置叫做cross end。

项目默认沿主轴排列。单个项目占据的主轴空间叫做main size，占据的交叉轴空间叫做cross size。

# 2. 容器属性

| 属性名             | 含义                                                    |
|:--------------- | ----------------------------------------------------- |
| flex-direction  | 决定主轴的方向（即项目的排列方向）。                                    |
| flex-wrap       | 默认情况下，项目都排在一条线（又称”轴线”）上。flex-wrap属性定义，如果一条轴线排不下，如何换行。 |
| flex-flow       | flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap。     |
| justify-content | 项目在主轴上的对齐方式。                                          |
| align-items     | 项目在交叉轴上如何对齐。                                          |
| align-content   | 多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。                         |

1. **flex-direction属性** *决定主轴的方向（即项目的排列方向）。*
   
   > 1. row(默认值)：主轴为水平方向，起点在左端。
   > 
   > 2. row-reverse：主轴为水平方向，起点在右端。
   > 
   > 3. column：主轴为垂直方向，起点在上沿。
   > 
   > 4. column-reverse：主轴为垂直方向，起点在下沿。
   
   ![5cdd0510abd7954686](https://i.loli.net/2019/05/16/5cdd0510abd7954686.jpg)

2. **flex-wrap属性** *默认情况下，项目都排在一条线（又称”轴线”）上。flex-wrap属性定义，如果一条轴线排不下，如何换行。*
   
   > 1. nowrap（默认）：不换行。
   > 
   > 2. wrap：换行，第一行在上方。
   > 
   > 3. wrap-reverse：换行，第一行在下方。
   
   ![5cdd067d6d77a72591](https://i.loli.net/2019/05/16/5cdd067d6d77a72591.jpg)

3. **flex-flow属性** *flex-direction属性和flex-wrap属性的简写形式。*

4. **justify-content属性** *定义项目在主轴上的对齐方式。*
   
   > 1. flex-start（默认值）：左对齐
   > 
   > 2. flex-end：右对齐
   > 
   > 3. center： 居中
   > 
   > 4. space-between：两端对齐，项目之间的间隔都相等。
   > 
   > 5. space-around：每个项目两侧的间隔相等。
   
   ![5cdd0c8803dab54238](https://i.loli.net/2019/05/16/5cdd0c8803dab54238.jpg)

5. **align-items属性** *定义项目在交叉轴上如何对齐。*
   
   > 1. flex-start：交叉轴的起点对齐。
   > 
   > 2. flex-end：交叉轴的终点对齐。
   > 
   > 3. center：交叉轴的中点对齐。
   > 
   > 4. baseline: 项目的第一行文字的基线对齐。
   > 
   > 5. stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。
   
   ![5cdd0c9eadfbd78483](https://i.loli.net/2019/05/16/5cdd0c9eadfbd78483.jpg)

6. **align-content属性** *定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。*
   
   > 1. flex-start：与交叉轴的起点对齐。
   > 
   > 2. flex-end：与交叉轴的终点对齐。
   > 
   > 3. center：与交叉轴的中点对齐。
   > 
   > 4. space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。
   > 
   > 5. space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
   > 
   > 6. stretch（默认值）：轴线占满整个交叉轴。
   
   ![5cdd0cbef2b0666644](https://i.loli.net/2019/05/16/5cdd0cbef2b0666644.jpg)

# 3. 项目属性

| 属性          | 含义                                                                                                    |
| ----------- | ----------------------------------------------------------------------------------------------------- |
| order       | order属性定义项目的排列顺序。数值越小，排列越靠前，默认为0。                                                                     |
| flex-grow   | flex-grow属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。                                                             |
| flex-shrink | flex-shrink属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。                                                          |
| flex-basis  | flexflex-basis属性定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。          |
| flex        | flex属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。                                   |
| align-self  | align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。 |

# 4. 参考

1. [简易布局图解](http://weibo.com/1712131295/CoRnElNkZ?ref=collection&type=comment)

2. [30分钟彻底弄懂flex布局](https://www.cnblogs.com/qcloud1001/p/9848619.html)

3. [Flex 布局教程：语法篇](https://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)
