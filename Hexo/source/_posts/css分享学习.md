---
title: 《CSS基础》
date: 2019-04-01 18:56:00
tags: 
- HTML 
- CSS
categories: CSS
- 前端CSS
---
## CSS简介
## CSS 指层叠样式表 (Cascading Style Sheets)
    *选择器
    *盒模型
    *背景和边框
    *文字特效
    *2D/3D转换
    *动画
    *多列布局
    *用户界面
## CSS分类
### 外部样式表
当样式需要应用于很多页面时，外部样式表将是理想的选择。在使用外部样式表的情况你可以通过改变一个文件来改变整个站点的外观。每个页面使用 <link> 标签链接到样式表


```
<link rel="stylesheet"type="text/css"href="xxx.css">
```


### 内部样式表（位于标签内部）
当单个文档需要特殊的样式时，就应该使用内部样式表。你可以使用` <style> `标签在文档头部定义内部样式表，就像这样:
```
<head> 
    <style type="text/css"> 
        h1 {color: sienna;} 
        body{background-color:black} 
    </style> 
</head>
```



### 内联样式表（在 HTML 元素内部）
由于要将表现和内容混杂在一起，内联样式会损失掉样式表的许多优势。例如当样式仅需要在一个元素上应用一次时。要使用内联样式，你需要在相关的标签内使用样式（style）属性。
请慎用这种方法


```
<h1 style="color:red">helloworld></h1>
```


## CSS语法
### 基础语法
CSS 规则由两个主要的部分构成：选择器，以及一条或多条声明。


```
selector {declaration1; declaration2; ... declarationN }

```

selector: 选择器通常是你需要改变元素的HTML元素
declaration：声明：有一个属性和一个值组成（property: value）
例：


```
body {
  color: #000;
  background: #fff;
  margin: 0;
  padding: 0;
  font-family: Georgia, Palatino, serif;
  }
```


### 高级语法
选择器分组
可以对选择器进行分组，这样，被分组的选择器就可以分享相同的声明


```
h1,h2,h3,h4,h5,h6 {
  color: green;
  font-size: 14px;
  }
```


### 继承及其问题
子元素从父元素继承属性,通过 CSS 继承，子元素将继承最高级元素（在本例中是 body）所拥有的属性（这些子元素诸如 p, td, ul, ol, ul, li, dl, dt,和 dd）。不需要另外的规则，所有 body 的子元素都应该显示 Verdana 字体，子元素的子元素也一样。并且在大部分的现代浏览器中，也确实是这样的。
html结构


```
<html>
    <head></head>
    <body>
        <p>share<p>
    </body>
</html>
```


css样式


```
body {
     font-family: Verdana, sans-serif;
     font-size: 14px;
     }
```


如果重写里面属性，将不会使用父元素的属性


```
p, td, ul, ol, li, dl, dt, dd  {
     font-size: 12px;
     }
```


## CSS选择器
### 派生选择器
派生选择器允许你根据文档的上下文关系来确定某个标签的样式。通过合理地使用派生选择器，我们可以使 HTML 代码变得更加整洁
html结构


```
<p>
    <strong>我是粗体字，不是斜体字，因为我不在列表当中，所以这个规则对我不起作用</strong>
</p>
<ol>
    <li>
        <strong>我是斜体字。这是因为 strong 元素位于 li 元素内。</strong>
    </li>
    <li>我是正常的字体。</li>
</ol>
```


css样式


```
li strong {
    font-style: italic;
    color:red;
    font-weight: normal;
  }
```
### id选择器(#id)
id 选择器可以为标有特定 id 的 HTML 元素指定特定的样式
html代码


```
<p id="red">这个段落是红色。</p>
<p id="green">这个段落是绿色。</p>
```


css代码


```
#red {color:red;}
#green {color:green;}
```


 id属性只能在每个 HTML 文档中出现一次
id 选择器和派生选择器
id被标注为 sidebar 的元素只能在文档中出现一次，这个 id 选择器作为派生选择器也可以被使用很多次


```
#sidebar p {
	font-style: italic;
	text-align: right;
	margin-top: 0.5em;
	}

#sidebar h2 {
	font-size: 1em;
	font-weight: normal;
	font-style: italic;
	margin: 0;
	line-height: 1.5;
	text-align: right;
	}
	
div#sidebar{
	border: 1px dotted #000;
	padding: 10px;	
}
```


### 类(class)选择器(.class)
类选择器允许以一种独立于文档元素的方式来指定样式
只有适当地标记文档后，才能使用这些选择器


```
html代码
<h1 class="important">
This heading is very important.
</h1>

<p class="important">
This paragraph is very important.
</p>

<p class="important warning">
    <p>share</p>
This paragraph is very important.
</p>

css代码
*.important {color:red;}
h1.important {color:red;}
p.important {color:red;}
.important p{font-size: 16px;}//跟id选择器一样 也可以和派生选择器结合使用
```


### 属性选择器
属性选择器可以根据元素的属性及属性值来选择元素

```
html代码
<h1>可以应用样式：</h1>
<p class="important warning">This is a paragraph.</a>
<h1>无法应用样式：</h1>
<p class="important">This is a paragraph.</a>
<input type="text"></input>
css代码
<style type="text/css">
    p[class="important warning"]{
        color: red;
    }
    input[type="text"]{
    }
</style>
```

### 后代选择器（跟派生选择器类似）
后代选择器（descendant selector）又称为包含选择器。后代选择器可以选择作为某元素后代的元素。

```
html代码
<h1>This is a <em>important</em> heading</h1>
<p>This is a <em>important</em> paragraph.</p>
css代码
h1 em {color:red;}
```

### 子元素选择器
与后代选择器相比，子元素选择器（Child selectors）只能选择作为某元素子元素的元素，语法：p > strong{color: red}

```
html代码
<h1>This is 
	<strong>very</strong>
	<strong>very</strong>important.
</h1>
<h1>This is 
	<em>really 
		<strong>very</strong>
	</em> 
	important.
</h1>
css代码
h1 > strong {color:red;}
h1.important div > p 跟后代选择器结合使用
```

### 相邻兄弟选择器
相邻兄弟选择器（Adjacent sibling selector）可选择紧接在另一元素后的元素，且二者有相同父元素
相邻兄弟选择器使用了加号（+），即相邻兄弟结合符（Adjacent sibling combinator）。注释：与子结合符一样，相邻兄弟结合符旁边可以有空白符。

```
html代码
<div>
  <ul>
    <li>List item 1</li>
    <li>List item 2</li>
    <li>List item 3</li>
  </ul>
  <ol>
    <li>List item 1</li>
    <li>List item 2</li>
    <li>List item 3</li>
  </ol>
</div>
css代码
li + li {font-weight:bold;}
```

### 伪类
CSS 伪类用于向某些选择器添加特殊的效果，最常见的是超链接使用
#### 语法：

```
selector : pseudo-class {property: value}
selector.class : pseudo-class {property: value}//与class类结合使用
a:link {color: #FF0000}		/* 未访问的链接 */
a:visited {color: #00FF00}	/* 已访问的链接 */
a:hover {color: #FF00FF}	/* 鼠标移动到链接上 */
a:active {color: #0000FF}	/* 选定的链接 */

<a class="red" href="css_syntax.asp">CSS Syntax</a>//与class结合使用
a.red : visited {color: #FF0000}
S
<ul>
    <li>Intert Key</li>
    <li>Turn key <strong>clockwise</strong></li>
    <li>Push accelerator</li>
</ul>
li:first-child {text-transform:uppercase;}//
获取元素中的第一个
```

#### 常见属性

	*:active 向被激活的元素添加样式
	*:focus 向拥有键盘输入焦点的元素添加样式
	*:hover 当鼠标悬浮在元素上方时，向元素添加样式
	*:link 向未被访问的链接添加样式
	*:visited 向已被访问的链接添加样式
	*:first-child 向元素的第一个子元素添加样式
	*:lang 向带有指定 lang 属性的元素添加样式
	
	*提示：在 CSS 定义中，a:hover 必须被置于 a:link 和 a:visited 之后，才是有效的。
	*提示：在 CSS 定义中，a:active 必须被置于 a:hover 之后，才是有效的。
	*提示：伪类名称对大小写不敏感。
	
### 伪元素
CSS 伪元素用于向某些选择器设置特殊效果
#### 语法：

```
selector:pseudo-element {property:value;}
selector.class:pseudo-element {property:value;}

实例代码
p:first-line{
    color:#ff0000;
    font-variant:small-caps;
    }
    
h1:before{
  content:url(logo.gif);
  }
h1:after{
  content:url(logo.gif);
  }
```

#### 常见属性
	:first-letter 向文本的第一个字母添加特殊样式
	:first-line 向文本的首行添加特殊样式
	:before 在元素之前添加内容
	:after 	在元素之后添加内容
	:before 和:after比较常见 常用于前后添加图片等

## CSS框架模型（盒子模型）
### 概述
CSS 框模型 (Box Model) 规定了元素框处理元素内容、内边距、边框 和 外边距 的方式。


```
* {
  margin: 0;
  padding: 0;
}
```


背景应用于由内容和内边距、边框组成的区域。

	*内边距、边框和外边距可以应用于一个元素的所有边，也可以应用于单独的边。
	*外边距可以是负值，而且在很多情况下都要使用负值的外边距。
	内边距(padding)
	*元素的内边距在边框和内容区之间。控制该区域最简单的属性是 padding 属性。CSS padding 属性定义元素边框与元素内容之间的空白区域。

```
body{padding: top right bottom left}
h1 {
  padding-top: 10px;
  padding-right: 0.25em;
  padding-bottom: 2ex;
  padding-left: 20%;
  }
  
  h1 {
    padding: 10px 20px 10px 20px
  }
  
  p {padding: 10% 10%;}
  
  p {padding: 10%;}
```


#### 属性

  padding 简写属性。作用是在一个声明中设置元素的所内边距属性
  padding—left	设置元素的左内边距
  padding-right 设置元素的右内边距
  padding-top 设置元素的上内边距
  padding-bottom 设置元素的下内边距
  分别设置上、右、下、左内边距

### 边框(boder)
元素的边框 (border) 是围绕元素内容和内边距的一条或多条线。CSS border 属性允许你规定元素边框的样式、宽度和颜色。

```
p.aside {border-style: solid dotted dashed double;}
```

上面这条规则为类名为 aside 的段落定义了四种边框样式：实线上边框、点线右边框、虚线下边框和一个双线左边框。

```
div {
    border: 1px solid #000;
    border-radius: 10px
    }
```
    

### 属性分类
	border 简写属性，用于把针对四个边的属性设置在一个声明
	border-style dotted solid double dashed  点状 实线 双线  虚线 用于设置元素所有边框的样式，或者单独地为各边设置边框样式。
	border-width 简写属性，用于为元素的所有边框设置宽度，或者单独地为各边边框设置宽度
	border-color 简写属性，设置元素的所有边框中可见部分的颜色，或为 4 个边分别设置颜色
	border-[bottom|top|left|right] 简写属性，用于把上下左右边框的所有属性设置到一个声明中
	border-[bottom|top|left|right]-color 设置元素的上下左右边框的颜色
	border-[bottom|top|left|right]-style 设置元素的上下左右边框的样式
	border-[bottom|top|left|right]-width 设置元素的上下左右边框的宽度
	border-radius 设置元素边框圆角属性
### 外边距(margin)
围绕在元素边框的空白区域是外边距。设置外边距会在元素外创建额外的“空白”。设置外边距的最简单的方法就是使用 margin 属性，这个属性接受任何长度单位、百分数值甚至负值

```
body{margin: top right bottom left}

h1{margin: 10px 20px 10px 20px}
h1{margin: 10px 20px}
h1{margin: 10px}
```

	属性
	margin 	简写属性。在一个声明中设置所有外边距属性
	margin-top 设置元素的上外边距
	margin-right 设置元素的右外边距
	margin-bottom 设置元素的下外边距
	margin-left 设置元素的左外边距
## CSS样式
### CSS 尺寸 (Dimension)
CSS 尺寸 (Dimension) 属性允许你控制元素的高度和宽度。同样，它允许你增加行间距。
所有CSS 尺寸 (Dimension)属性
#### 属性

	描述
	height
	设置元素的高度。
	line-height
	设置行高。
	max-height
	设置元素的最大高度。
	max-width
	设置元素的最大宽度。
	min-height
	设置元素的最小高度。
	min-width
	设置元素的最小宽度。
	width
	设置元素的宽度。
	
### CSS背景(background)
 CSS 允许应用纯色作为背景，也允许使用背景图像创建相当复杂的效果。
 
```
body
{ 
    background: #00ff00 url('smiley.gif') no-repeat fixed center; 
}
```

	background-color 指定要使用的背景颜色
	background-position 指定背景图像的位置
	background-size 指定背景图片的大小
	background-repeat 指定如何重复背景图像
	background-attachment 设置背景图像是否固定或者随着页面的其余部分滚动
	background-image 指定要使用的一个或多个背景图像
	background-position 属性取值
	
#### 值
	描述
	left top
	left center
	left bottom
	right top
	right center
	right bottom
	center top
	center center
	center bottom
	如果仅指定一个关键字，其他值将会是"center"
	x% y%
	第一个值是水平位置，第二个值是垂直。左上角是0％0％。右下角是100％100％。如果仅指定了一个值，其他值将是50％。 。默认值为：0％0％
	xpos ypos
	第一个值是水平位置，第二个值是垂直。左上角是0。单位可以是像素（0px0px）或任何其他 CSS单位。如果仅指定了一个值，其他值将是50％。你可以混合使用％和positions
	inherit
	指定background-position属性设置应该从父元素继承
	background-attachment属性取值
	
#### 值
	说明
	scroll
	背景图片随页面的其余部分滚动。这是默认
	fixed
	背景图像是固定的
	inherit
	指定background-attachment的设置应该从父元素继承
	background-repeat属性取值
	
#### 值
	说明
	repeat
	背景图像将向垂直和水平方向重复。这是默认
	repeat-x
	只有水平位置会重复背景图像
	repeat-y
	只有垂直位置会重复背景图像
	no-repeat
	background-image不会重复
	inherit
	指定background-repea属性设置应该从父元素继承
	
### CSS文本(Text)
CSS 文本属性可定义文本的外观。通过文本属性，您可以改变文本的颜色、字符间距，对齐文本，装饰文本，对文本进行缩进，等等
#### 属性
	描述
	color
	设置文本颜色
	direction
	设置文本方向。
	line-height
	设置行高。
	letter-spacing
	设置字符间距。
	text-align
	对齐元素中的文本。
	text-indent
	缩进元素中文本的首行。
	text-shadow
	设置文本阴影。CSS2 包含该属性，但是 CSS2.1 没有保留该属性。
	text-transform
	控制元素中的字母。
	white-space
	设置元素中空白的处理方式。
	word-spacing
	设置字间距。
	
```
div {
    text-indent: 10px;
    color: red;
    line-height: 1.5;
    text-align: center;
    white-space: nowrap;//不折行
    }
    ```
    
### CSS字体(fonts)
 CSS 字体属性定义文本的字体系列、大小、加粗、风格（如斜体）和变形（如小型大写字母）。
 
```
body {
    font-family: sans-serif;
    font-style:normal;
    font-weight:normal;
    font-size:60px;
    }
```
    
	font-style 属性最常用于规定斜体文本。
	该属性有三个值：
	normal - 文本正常显示
	italic - 文本斜体显示
	oblique - 文本倾斜显示
	
	使用 bold 关键字可以将文本设置为粗体。
	关键字 100 ~ 900 为字体指定了 9 级加粗度。如果一个字体内置了这些
	加粗级别，那么这些数字就直接映射到预定义的级别，100 对应最细的字体
	变形，900 对应最粗的字体变形。数字 400 等价于 normal，而 700 等
	价于 bold。
	
#### 属性

	描述
	font
	简写属性。作用是把所有针对字体的属性设置在一个声明中。
	font-family
	设置字体系列。
	font-size
	设置字体的尺寸。
	font-style
	设置字体风格。
	font-weight
	设置字体的粗细。
	
###CSS链接(link)
为链接设置样式

```
a:link {color:#FF0000;}		/* 未被访问的链接 */
a:visited {color:#00FF00;}	/* 已被访问的链接 */
a:hover {color:#FF00FF;}	/* 鼠标指针移动到链接上 */
a:active {color:#0000FF;}	/* 正在被点击的链接 */

a:link {text-decoration:none;}
a:visited {text-decoration:none;}
a:hover {text-decoration:underline;}
a:active {text-decoration:underline;}
```

### CSS列表(ul)
CSS 列表属性允许你放置、改变列表项标志，或者将图像作为列表项标志

`li {list-style : url(example.gif) square inside}`

#### 属性
	描述
	list-style
	简写属性。用于把所有用于列表的属性设置于一个声明中。
	list-style-image
	将图象设置为列表项标志。
	list-style-position
	设置列表中列表项标志的位置。
	list-style-type
	设置列表项标志的类型。
	 list-style-type属性值
	 
####值
	描述
	none
	无标记。
	disc
	默认。标记是实心圆。
	circle
	标记是空心圆。
	square
	标记是实心方块。
	decimal
	标记是数字。
	decimal-leading-zero
	0开头的数字标记。(01, 02, 03, 等。)
	Demo
	
### CSS表格(Table)
```
table, th, td{
  border: 1px solid blue;
  }
td{
  height:50px;
  vertical-align:bottom;
  text-align:right;
  }
th{
  background-color:green;
  color:white;
  } 
```

#### 属性
	描述
	border-collapse
	设置是否把表格边框合并为单一的边框。
	border-spacing
	设置分隔单元格边框的距离。
	caption-side
	设置表格标题的位置。
	empty-cells
	设置是否显示表格中的空单元格。
	table-layout
	设置显示单元、行和列的算法。
	
### CSS 轮廓(outline)
轮廓（outline）是绘制于元素周围的一条线，位于边框边缘的外围，可起到突出元素的作用。CSS outline 属性规定元素轮廓的样式、颜色和宽度。
#### 属性
	描述
	CSS
	outline
	在一个声明中设置所有的轮廓属性。
	outline-color
	设置轮廓的颜色。
	outline-style
	设置轮廓的样式。
	outline-width
	设置轮廓的宽度。
	
```
p {
border:red solid thin;
outline:#00ff00 dotted thick;
}
```

## CSS定位(position)

CSS 定位 (Positioning) 属性允许你对元素进行定位，CSS 为定位和浮动提供了一些属性，利用这些属性，可以建立列式布局，将布局的一部分与另一部分重叠，定位的基本思想很简单，它允许你定义元素框相对于其正常位置应该出现的位置，或者相对于父元素、另一个元素甚至浏览器窗口本身的位置。

### static 定位
HTML 元素的默认值，即没有定位，遵循正常的文档流对象。静态定位的元素不会受到 top, bottom, left, right影响。

```
div.static {
    position: static;
    border: 3px solid #73AD21;
}
```

### 绝对定位(absolute)
设置为绝对定位的元素框从文档流完全删除，并相对于其包含块定位，包含块可能是文档中的另一个元素或者是初始包含块。元素原先在正常文档流中所占的空间会关闭，就好像该元素原来不存在一样。元素定位后生成一个块级框，而不论原来它在正常流中生成何种类型的框。

```
#box_relative {
  position: absolute;
  left: 30px;
  top: 20px;
}
```

### 相对定位(relative)
设置为相对定位的元素框会偏移某个距离。元素仍然保持其未定位前的形状，它原本所占的空间仍保留

```
#box_relative {
  position: relative;
  left: 30px;
  top: 20px;
}
```

### 相对定位和绝对定位关系

在没有父级元素定位时，以浏览器的左上角为基准
有父级的情况下，父级设置相对定位，子级设置绝对定位 是以父盒子进行定位的

```
html代码
<div class="parent">
    <div class="child"></div>
</div>
css代码
.parent{
    position: relative;
    top: 10px;
    left: 10px;
}
.child{
    position: absolute;
    top: 10px;
    left: 10px;
}
```

### fixed 定位
元素的位置相对于浏览器窗口是固定位置,即使窗口是滚动的它也不会移动：

```
p.pos_fixed
{
    position:fixed;
    top:30px;
    right:5px;
}
```

### CSS 浮动
浮动的框可以向左或向右移动，直到它的外边缘碰到包含框或另一个浮动框的边框为止。由于浮动框不在文档的普通流中，所以文档的普通流中的块框表现得就像浮动框不存在一样。

```
html代码
<div>
    <span></span>
    <span></span>
    <span></span>
</div>
css代码
span{
    float:left;
    width:50px;
    height: 50px;
    }
    ```
    
 ### clear 属性
 阻止行框围绕浮动框，需要对该框应用 clear 属性。clear 属性的值可以是 left、right、both 或 none，它表示框的哪些边不应该挨着浮动框。
```
.news {
  background-color: gray;
  border: solid 1px black;
  }

.news img {
  float: left;
  }

.news p {
  float: right;
  }

.clear {
  clear: both;
  }
<div class="news">
  <img src="news-pic.jpg" />
  <p>some text</p>
<div class="clear"></div>
</div>
```

#### 属性

	说明|值
	
	bottom|定义了定位元素下外边距边界与其包含块下边界之间的偏移。
	auto
	length
	%
	inherit
	clip
	剪辑一个绝对定位的元素
	shape
	auto
	inherit
	cursor
	显示光标移动到指定的类型
	url
	auto
	crosshair
	default
	pointer
	move
	e-resize
	ne-resize
	nw-resize
	n-resize
	se-resize
	sw-resize
	s-resize
	w-resize
	text
	wait
	help
	left
	定义了定位元素左外边距边界与其包含块左边界之间的偏移。
	auto
	length
	%
	inherit
	overflow
	
	设置当元素的内容溢出其区域时发生的事情。
	auto
	hidden
	scroll
	visible
	inherit
	overflow-y
	
	指定如何处理顶部/底部边缘的内容溢出元素的内容区域
	auto
	hidden
	scroll
	visible
	no-display
	no-content
	overflow-x
	
	指定如何处理右边/左边边缘的内容溢出元素的内容区域
	auto
	hidden
	scroll
	visible
	no-display
	no-content
	position
	指定元素的定位类型
	absolute
	fixed
	relative
	static
	inherit
	right
	定义了定位元素右外边距边界与其包含块右边界之间的偏移。
	auto
	length
	%
	inherit
	top
	定义了一个定位元素的上外边距边界与其包含块上边界之间的偏移。
	auto
	length
	%
	inherit
	z-index
	设置元素的堆叠顺序
	number
	auto
	inherit
### Display(显示) 与 Visibility（可见性）
隐藏元素 - display:none或visibility:hidden
隐藏一个元素可以通过把display属性设置为"none"，或把visibility属性设置为"hidden"。但是请注意，这两种方法会产生不同的结果。visibility:hidden可以隐藏某个元素，但隐藏的元素仍需占用与未隐藏之前一样的空间。也就是说，该元素虽然被隐藏了，但仍然会影响布局。
```
h1.hidden {visibility:hidden;}
h1.hidden {display:none;}
```
## CSS Display - 块和内联元素
### 块级元素(block)特性：
总是独占一行，表现为另起一行开始，而且其后的元素也必须另起一行显示;
宽度(width)、高度(height)、内边距(padding)和外边距(margin)都可控制;
### 内联元素(inline)特性：
和相邻的内联元素在同一行;
宽度(width)、高度(height)、内边距的top/bottom(padding-top/padding-bottom)和外边距的top/bottom(margin-top/margin-bottom)都不可改变，就是里面文字或图片的大小;

	块级元素主要有：
	 address , blockquote , center , dir , div , dl , fieldset , form , h1 , h2 , h3 , h4 , h5 , h6 , hr , isindex , menu , noframes , noscript , ol , p , pre , table , ul , li
	内联元素主要有：
	a , abbr , acronym , b , bdo , big , br , cite , code , dfn , em , font , i , img , input , kbd , label , q , s , samp , select , small , span , strike , strong , sub , sup ,textarea , tt , u , var
	可变元素(根据上下文关系确定该元素是块元素还是内联元素)：
	applet ,button ,del ,iframe , ins ,map ,object , script
#### CSS中块级、内联元素的应用：
利用CSS我们可以摆脱上面表格里HTML标签归类的限制，自由地在不同标签/元素上应用我们需要的属性。
主要用的CSS样式有以下三个：
	display:block  -- 显示为块级元素
	display:inline  -- 显示为内联元素
	display:inline-block -- 显示为内联块元素，表现为同行显示并可修改宽高内外边距等属性
	我们常将元素加上display:inline-block样式，原本垂直的列表就可以水平显示了。
### CSS3 弹性盒子(Flex Box)
弹性盒子是 CSS3 的一种新的布局模式。CSS3 弹性盒（ Flexible Box 或 flexbox），是一种当页面需要适应不同的屏幕大小以及设备类型时确保元素拥有恰当的行为的布局方式。引入弹性盒布局模型的目的是提供一种更加有效的方式来对一个容器中的子元素进行排列、对齐和分配空白空间。
#### 弹性盒子内容
弹性盒子由弹性容器(Flex container)和弹性子元素(Flex item)组成。弹性容器通过设置 display 属性的值为 flex 或 inline-flex将其定义为弹性容器。弹性容器内包含了一个或多个弹性子元素。

```
<!DOCTYPE html>
<html>
<head>
<style>
.flex-container {
    display: -webkit-flex;
    display: flex;
    width: 400px;
    height: 250px;
    background-color: lightgrey;
}
 
.flex-item {
    background-color: cornflowerblue;
    width: 100px;
    height: 100px;
    margin: 10px;
}
</style>
</head>
<body>
 
<div class="flex-container">
  <div class="flex-item">flex item 1</div>
  <div class="flex-item">flex item 2</div>
  <div class="flex-item">flex item 3</div> 
</div>
 
</body>
</html>
```

flex-direction
flex-direction 属性指定了弹性子元素在父容器中的位置。

#### 语法
	flex-direction: row | row-reverse | column | column-reverse
	flex-direction的值有:
	row：横向从左到右排列（左对齐），默认的排列方式。
	row-reverse：反转横向排列（右对齐，从后往前排，最后一项排在最前面。
	column：纵向排列。
	column-reverse：反转纵向排列，从后往前排，最后一项排在最上面。
	.flex-container {
	    display: -webkit-flex;
	    display: flex;
	    -webkit-flex-direction: row-reverse;
	    flex-direction: row-reverse;
	    width: 400px;
	    height: 250px;
	    background-color: lightgrey;
	}
	justify-content 属性
	内容对齐（justify-content）属性应用在弹性容器上，把弹性项沿着弹性容器的主轴线（main axis）对齐。
	justify-content 语法如下：
	justify-content: flex-start | flex-end | center | space-between | space-around
	各个值解析:
	flex-start：弹性项目向行头紧挨着填充。这个是默认值。第一个弹性项的main-start外边距边线被放置在该行的main-start边线，而后续弹性项依次平齐摆放。
	flex-end：弹性项目向行尾紧挨着填充。第一个弹性项的main-end外边距边线被放置在该行的main-end边线，而后续弹性项依次平齐摆放。
	center：弹性项目居中紧挨着填充。（如果剩余的自由空间是负的，则弹性项目将在两个方向上同时溢出）。
	space-between：弹性项目平均分布在该行上。如果剩余空间为负或者只有一个弹性项，则该值等同于flex-start。否则，第1个弹性项的外边距和行的main-start边线对齐，而最后1个弹性项的外边距和行的main-end边线对齐，然后剩余的弹性项分布在该行上，相邻项目的间隔相等。
	space-around：弹性项目平均分布在该行上，两边留有一半的间隔空间。如果剩余空间为负或者只有一个弹性项，则该值等同于center。否则，弹性项目沿该行分布，且彼此间隔相等（比如是20px），同时首尾两边和弹性容器之间留有一半的间隔（1/2*20px=10px）。

```
.flex-container {
    display: -webkit-flex;
    display: flex;
    -webkit-justify-content: flex-end;
    justify-content: flex-end;
    width: 400px;
    height: 250px;
    background-color: lightgrey;
}
```

	align-items 属性
	align-items 设置或检索弹性盒子元素在侧轴（纵轴）方向上的对齐方式。
	语法
	align-items: flex-start | flex-end | center | baseline | stretch
	各个值解析:
	flex-start：弹性盒子元素的侧轴（纵轴）起始位置的边界紧靠住该行的侧轴起始边界。
	flex-end：弹性盒子元素的侧轴（纵轴）起始位置的边界紧靠住该行的侧轴结束边界。
	center：弹性盒子元素在该行的侧轴（纵轴）上居中放置。（如果该行的尺寸小于弹性盒子元素的尺寸，则会向两个方向溢出相同的长度）。
	baseline：如弹性盒子元素的行内轴与侧轴为同一条，则该值与'flex-start'等效。其它情况下，该值将参与基线对齐。
	stretch：如果指定侧轴大小的属性值为'auto'，则其值会使项目的边距盒的尺寸尽可能接近所在行的尺寸，但同时会遵照'min/max-width/height'属性的限制。
	.flex-container {
	    display: -webkit-flex;
	    display: flex;
	    -webkit-align-items: stretch;
	    align-items: stretch;
	    width: 400px;
	    height: 250px;
	    background-color: lightgrey;
	}
	flex-wrap 属性
	flex-wrap 属性用于指定弹性盒子的子元素换行方式。
	语法
	flex-wrap: nowrap|wrap|wrap-reverse|initial|inherit;
	各个值解析:
	nowrap - 默认， 弹性容器为单行。该情况下弹性子项可能会溢出容器。
	wrap - 弹性容器为多行。该情况下弹性子项溢出的部分会被放置到新行，子项内部会发生断行
	wrap-reverse -反转 wrap 排列。
```
.flex-container {
    display: -webkit-flex;
    display: flex;
    -webkit-flex-wrap: nowrap;
    flex-wrap: nowrap;
    width: 300px;
    height: 250px;
    background-color: lightgrey;
}
```

### 弹性子元素属性
#### 排序
	语法
	order: 
	各个值解析:
	<integer>：用整数值来定义排列顺序，数值小的排在前面。可以为负值。
	order 属性设置弹性容器内弹性子元素的属性:
	对齐
	设置"margin"值为"auto"值，自动获取弹性容器中剩余的空间。所以设置垂直方向margin值为"auto"，可以使弹性子元素在弹性容器的两上轴方向都完全居中。
	以下实例在第一个弹性子元素上设置了 margin-right: auto; 。 它将剩余的空间放置在元素的右侧：
	完美的居中
	以下实例将完美解决我们平时碰到的居中问题。
	使用弹性盒子，居中变的很简单，只想要设置 margin: auto; 可以使得弹性子元素在两上轴方向上完全居中:
	align-self
	align-self 属性用于设置弹性元素自身在侧轴（纵轴）方向上的对齐方式。
	语法
	align-self: auto | flex-start | flex-end | center | baseline | stretch
	各个值解析:
	auto：如果'align-self'的值为'auto'，则其计算值为元素的父元素的'align-items'值，如果其没有父元素，则计算值为'stretch'。
	flex-start：弹性盒子元素的侧轴（纵轴）起始位置的边界紧靠住该行的侧轴起始边界。
	flex-end：弹性盒子元素的侧轴（纵轴）起始位置的边界紧靠住该行的侧轴结束边界。
	center：弹性盒子元素在该行的侧轴（纵轴）上居中放置。（如果该行的尺寸小于弹性盒子元素的尺寸，则会向两个方向溢出相同的长度）。
	baseline：如弹性盒子元素的行内轴与侧轴为同一条，则该值与'flex-start'等效。其它情况下，该值将参与基线对齐。
	stretch：如果指定侧轴大小的属性值为'auto'，则其值会使项目的边距盒的尺寸尽可能接近所在行的尺寸，但同时会遵照'min/max-width/height'属性的限制。
	flex
	flex 属性用于指定弹性子元素如何分配空间。
#### 语法
	flex: auto | initial | none | inherit |  [ flex-grow ] || [ flex-shrink ] || [ flex-basis ]
	各个值解析:
	auto: 计算值为 1 1 auto
	initial: 计算值为 0 1 auto
	none：计算值为 0 0 auto
	inherit：从父元素继承
	[ flex-grow ]：定义弹性盒子元素的扩展比率。
	[ flex-shrink ]：定义弹性盒子元素的收缩比率。
	[ flex-basis ]：定义弹性盒子元素的默认基准值。
	CSS3 弹性盒子属性
#### 属性
	描述
	display
	指定 HTML 元素盒子类型。
	flex-direction
	指定了弹性容器中子元素的排列方式
	justify-content
	设置弹性盒子元素在主轴（横轴）方向上的对齐方式。
	align-items
	设置弹性盒子元素在侧轴（纵轴）方向上的对齐方式。
	flex-wrap
	设置弹性盒子的子元素超出父容器时是否换行。
	align-content
	修改 flex-wrap 属性的行为，类似 align-items, 但不是设置子元素对齐，而是设置行对齐
	flex-flow
	flex-direction 和 flex-wrap 的简写
	order
	设置弹性盒子的子元素排列顺序。
	align-self
	在弹性子元素上使用。覆盖容器的 align-items 属性。
	flex
	设置弹性盒子的子元素如何分配空间。

### 垂直居中方案
方法1：table-cell

```
html结构：
<div class="box box1"><span>垂直居中</span></div>
css
.box1{
    display: table-cell;
    vertical-align: middle;
    text-align: center;
    }
```

方法2：display:flex

```
.box2{
    display: flex;
    justify-content:center;
    align-items:Center;
    }
    ```
    
方法3：绝对定位和负边

```
.box3{position:relative;}
.box3 span{
            position: absolute;
            width:100px;
            height: 50px;
            top:50%;
            left:50%;
            margin-left:-50px;
            margin-top:-25px;
            text-align: center;
        }
```

方法4：绝对定位和0

```
.box4 span{
    width: 50%; 
    height: 50%; 
    background: #000;
    overflow: auto; 
    margin: auto; 
    position: absolute; 
    top: 0;
    left: 0; 
    bottom: 0; 
    right: 0;
    }
 ```
 
这种方法跟上面的有些类似，但是这里是通过margin:auto和top,left,right,bottom都设置为0实现居中，很神奇吧。不过这里得确定内部元素的高度，可以用百分比，比较适合移动端。
方法5：translate
这实际上是方法3的变形，移位是通过translate来实现的。

```
.box6 span{
    position: absolute; 
    top:50%;
    left:50%;  
    width:100%;
    transform:translate(-50%,-50%);  
    text-align: center;
    }
   ```
   
方法6：display:inline-block

```
.box7{
    text-align:center;
    font-size:0;
}
.box7 span{ 
    vertical-align:middle; 
    display:inline-block;  
    font-size:16px;
}
.box7:after{
    content:'';
    width:0;
    height:100%;
    display:inline-block;
    vertical-align:middle;
}
```

这种方法确实巧妙...通过:after来占位。

```
方法7：display:flex和margin:auto
.box8{    
  display: flex;
  text-align: center;
}
.box8 span{margin: auto;
```