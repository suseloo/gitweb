# 网页笔记
## HTML
### 标签
#### img属性:
* src:设置一个外部图片的路径 
* alt:可以用来设置在图片不能显示时，对图片的描述，不写搜素引擎不收录 
* width:修改图片宽度，一般px作为单位 
* height:修改图片高度，一般px作为单位 
* 一般不是自适应不建议设置width和height 

#### meta标签
* 搜素引擎在检索页面时，会同时检索页面中的关键词和描述，这2个值不会对页面有影响。
* 使用meta标签还可以用来设置网页的关键字
```html
<meta name="keywords" content="HTML5,JavaScript,前端,Python">
```
> 还可以用来指定网页的描述
```html
<meta name="description" content="发布h5、JS等前端相关的信息。">
```
> 使用meta来做请求重定向 5表示等待时间秒
```html
<meta http-equiv="refresh" content="5;url=http://www.baidu.com">
```
[meta全部配置](https://www.w3school.com.cn/tags/tag_meta.asp)

***
# CSS
### 选择器
**元素选择器**

* 作用：通过元素选择器可以选择页面中的所有指定元素
```html
<style>
p{
	color:red;
}
</style>
<p>测试文本</p>
<p>测试文本</p>
<p>测试文本</p>
```

#### **id选择器**
*  通过元素的id属性值选中唯一的一个元素
	- 语法：
 	- #id属性值{}

#### **id选择器不能选择组，因为id是唯一的**
```html
<style>
#p1{
	font-size:20px;
}
</style>
<p>测试文本</p>
<p id="p1">测试文本</p>
<p>测试文本</p>
```

#### **类选择器**
* 通过元素的class属性值选中一组元素
	- 语法：
	- .class属性值{}
```html
<style>
.p1{
	font-size:20px;
}
.p2{
	color:blue;
}
</style>
<p id="p1">测试文本</p>
<p class="p1">测试文本</p>
<p class="p1 p2">测试文本</p>
```

#### **选择器分组**
* 通过选择器分组可以同时选中多个选择器对应的元素
	- 语法：
	- 选择器1，选择器2，选择器N{}
* 也叫并集选择器
```html
<style>
#p1,.p1{
	color:yellow;
}

</style>
<p id="p1">测试文本</p>
<p class="p1">测试文本</p>
<p class="p1 p2">测试文本</p>
```
#### **复合选择器**
* 作用：可以选中同时满足多个选择器的元素
	- 语法：
	- 选择器1选择器2选择器N{}
* 为拥有class p3 的span元素设置一个背景，即其他元素的class p3不被改变

```html
<style>
span.p3{
	color:yellow;
}

</style>
<p id="p1">测试文本</p>
<p class="p1">测试文本</p>
<p class="p1 p2 p3">测试文本</p>
<span class="p3">测试文本</span>
```
#### **后代元素选择器**
* 作用：
	- 选中指定元素的指定后代元素
* 语法：
	- 祖先元素 后代元素{}
```html
<style>
	div span{
		color:green;
	}
</style>

<div>
	<span>div下的span</span>
	<p><span>div下的p下的span</span></p>
</div>
<span>body下的span</span>
```
#### **子元素选择器**
* 作用：
	- 选中指定父元素的指定子元素
* 语法：
	- 父元素 > 子元素
```html
<style>
	div>span{
		color:green;
	}
</style>

<div>
	<span>div下的span</span>
	<p><span>div下的p下的span</span></p>
</div>
<span>body下的span</span>
```
#### **伪类选择器**
* 伪类专门用来表示元素的一种特殊的状态
* 比如：访问过的超链接，比如普通的超链接，比如获取焦点的文本框
*  当我们需要为处在这些特殊状态的元素设置样式时，就可以使用伪类
* 正常链接	a:link
* 访问过的链接	a:visited(只能定义字体颜色)
* 鼠标滑过的链接		a:hover
* 正在点击的链接		a:active
*  获取焦点		:focus
*  指定元素前	:before
*  指定元素后	:after
*  选中的元素	::selection  火狐浏览器需要写::-moz-selection
*  -由于涉及到用户的隐私问题，所以visited伪类只能设置字体颜色
* hover和active也可以绑定其他暗元素
	- 首字母：:first-letter
	- 首行：:first-line
	- 开始标签尖括号之后：:before  
	- 一般before都需要结合content样式一起使用
	- 通过content可以向before或after的位置添加一些
```html
<style>
	p:first-letter{
		color: red;
	}
	p:first-line{
		background-color: yellow;
	}
	p::before{
		content: "中国";
		color:red;
	}
	p::after{
		content: "<font>结尾<font>";
		color: red;
	}
	
</style>
```
#### **属性选择器**
* 假设设置所有具有title属性得p元素，设置一个背景颜色
* 语法：
	- [属性名] 选取含有指定属性得元素
	- [属性名="属性值"] 选取含有**指定属性值**的元素
	- [属性名^="属性值"] 选取属性值以指定内容**开头**的元素
	- [属性名$="属性值"] 选取属性值以指定内容**结尾**的元素
	- [属性名*="属性值"] 选取属性值以指定内容**包含**的元素
```html
<style>
	p[title]{
		background-color: yellow;
	}
	p[title="abc"]{
		background-color: red;
	}
	p[title^=ab]{
		background-color: green;
	}
	p[title$=c]{
		background-color:red;
	}
	p[title*=b]{
		background-color: aqua;
	}
</style>

<p title="hello c">一个段落</p>
<p title="abd">一个段落</p>
<p title="abc">一个段落</p>
```
#### **其他子元素选择器**
* :first-child	选择第一个子标签
* :last-child		选择最后一个子标签
* :nth-child(参数)		选择指定位置的子元素(指定数值或者even偶数和add奇数)
* :first-of-type	:last-of-type	:nth-of-type	选择指定类型的子元素
```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
		<style>
			/* 会选中第一个p标签和div中的第一个p标签 */
			/* p:first-child{
				background-color: yellow;
			} */
			
			/* 会选中最后一个p标签 div中的最后一个 */
			/* p:last-child{
				background-color: yellow;
			} */
			
			/* even选中偶数，add选中单数，也可以用阿拉伯数值指定 */
			/* p:nth-child(even){
				background-color: yellow;
			} */
			
			/* 选中第一个 包括div中的第一个p元素 */
			/* p:first-of-type{
				background-color: yellow;
			} */
			
			/* 选中最后一个 包括div中的最后一个 */
			/* p:last-of-type{
				background-color: yellow;
			} */
			
			/* 选中偶数  包括div中的偶数 add基数  或阿拉伯数值*/
			p:nth-of-type(even){
				background-color: yellow;
			}
			
		</style>
	</head>
	<body>
		
		<p>p标签</p>
		<p>p标签</p>
		<p>p标签</p>
		<p>p标签</p>
		<p>p标签</p>
		<div>
			<p>div中p标签</p>
			<p>div中p标签</p>
			<p>div中p标签</p>
		</div>
	</body>
</html>

```
#### **兄弟元素选择器**
```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
		<style>
			/* 选中span标签后一个p元素 */
			/* span + p{
				background-color: yellow;
			} */
			
			/* 选中span后所有p标签 */
			span ~ p{
				background-color: yellow;
			}
		</style>
	</head>
	<body>
		
		<p>p标签</p>
		<p>p标签</p>
		<span>span标签</span>
		<p>p标签</p>
		<p>p标签</p>
	</body>
</html>
```
#### **否定选择器**
```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
		<style>
			/* 除了.hello的p标签外 */
			p:not(.hello){
				background-color: yellow;
			}
		</style>
	</head>
	<body>
		
		<p>p标签</p>
		<p class="hello">p标签</p>
		<p>p标签</p>
		<p>p标签</p>
	</body>
</html>
```
#### **集成样式**
* 像儿子可以继承父亲的遗产一样，在CSS中，祖先元素上的样式，也会被后代元素继承
* 但是并不是所有的样式都会被子元素继承，比如：背景相关的样式，在CSS手册中搜素background-color查看是否继承，因为其标签属性是透明的transparent所以表面上看还是有背景色

#### **选择器的优先级
* 优先级的规则
	- 内联样式，优先级	1000
	- ID选择器，优先级	100
	- 类和伪类，优先级	10
	- 元素选择器，优先级	1
	- 通配*，优先级		0
	- 继承样式，没有优先级
* 当包含多种选择器时 会将优先级相加获得新的优先级，并集选择器是单独计算
* 当一个样式后面加上 !important优先级会被提升 

#### **字体**
* 一般指定为font-family的最后一个字体
* 字体分为五大类
* serif(衬线字体)
* sans-serif(非衬线字体)
* monospace(等宽字体)
* cursive(草书字体)
* fantasy(虚幻字体)
```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
		
	</head>
	<body>
		<style>
			p[title]{
				font-family:arial,微软雅黑,serif;
			}
		</style>
		
		<p style="font-size:40px;font-family:serif">衬线字体ABCDEFabcdef</p>
		<p style="font-size:40px;font-family:sans-serif">非衬线字体ABCDEFabcdef</p>
		<p style="font-size:40px;font-family:monospace">等宽字体ABCDEFabcdef</p>
		<p style="font-size:40px;font-family:cursive">草书字体ABCDEFabcdef</p>
		<p style="font-size:40px;font-family:fantasy">虚幻字体ABCDEFabcdef</p>
	</body>
</html>
```

#### **行高**
* 行间距line-height = 行高 - 字体大小

```CSS

.x1{
	font-size: 20px;
	/* 1.数值 行间距等于40px-20px=20px */
	line-height: 40px;
	/* 2.字体大小的倍数  常用*/
	line-height: 1;
	/* 3.字体大小的百分比 */
	line-height: 200%;
	
	/* 30px字体大小 50pxline-height 行高=50-30 不指定行高则使用默认值 */
	font:30px/50px "微软雅黑"
}
```
### **盒模型**
#### **边框样式**
* 为元素设置边框
* 要为一个元素设置边框必须指定三个样式
* border-width:边框的宽度
* border-color:边框的演示
* border-style:边框的样式
[边框的其他所有属性](https://www.runoob.com/css/css-border.html)

|属性				|描述		|	
| ----| ----|
|border				|简写属性，用于把针对四个边的属性设置在一个声明。						|
|border-style		|用于设置元素所有边框的样式，或者单独地为各边设置边框样式。				|
|border-width		|简写属性，用于为元素的所有边框设置宽度，或者单独地为各边边框设置宽度。	|
|border-color		|简写属性，设置元素的所有边框中可见部分的颜色，或为 4 个边分别设置颜色。|
|border-bottom		|简写属性，用于把下边框的所有属性设置到一个声明中。						|
|border-bottom-color|设置元素的下边框的颜色。												|
|border-bottom-style|设置元素的下边框的样式。												|
|border-bottom-width|设置元素的下边框的宽度。												|
|border-left		|简写属性，用于把左边框的所有属性设置到一个声明中。						|
|border-left-color	|设置元素的左边框的颜色。												|
|border-left-style	|设置元素的左边框的样式。												|
|border-left-width	|设置元素的左边框的宽度。												|
|border-right		|简写属性，用于把右边框的所有属性设置到一个声明中。						|
|border-right-color	|设置元素的右边框的颜色。												|
|border-right-style	|设置元素的右边框的样式。												|
|border-right-width	|设置元素的右边框的宽度。												|
|border-top			|简写属性，用于把上边框的所有属性设置到一个声明中。						|
|border-top-color	|设置元素的上边框的颜色。												|
|border-top-style	|设置元素的上边框的样式。												|
|border-top-width	|设置元素的上边框的宽度。												|
|border-radius		|设置圆角的边框。														|

```html
		<style>
	.box1{
		/* width 和 height 设置的大小是内容区的大小 不包括boerder的 边框则x2计算 */
		width: 100px;
		height: 100px;
		background-color: aqua;
		
		border: 10px red solid;
		/*             上   右	下	 左 */
		border-width: 10px 20px 40px 80px;
		/* 			   上  左右  下 */
		border-width: 10px 20px 40px;
		/* 			 上下	左右 */
		border-width: 10px 50px; 
		
		/* 同上多种设置*/
		border-color:red;
		border-style:none;
	}
</style>
<div class="box1"></div>
```

#### **内边距**
* padding 内边距会影响盒子的大小，背景会衍生到内边距
```html
<body>
	<style>
		.box1{
			/* width 和 height 设置的大小是内容区的大小 不包括boerder的 边框则x2计算 */
			width: 200px;
			height: 200px;
			background-color: aqua;
			border: 10px solid red;
			
			padding-top: 100px;
			
		}
		.box2{
			width: 100%;
			height: 100%;
			background-color: yellow;
		}
	</style>
	<div class="box1">
		<div class="box2"></div>
	</div>
</body>
```
#### 外边距
* 超过父元素会被撑出去
* 以父元素内容区域为准，不管父元素的border边框数值
* 设置上和左的外边距会改变自身的位置，而右和下会改变其他盒子的位置
* margin也可以是负值，也可以是auto一般给左右水平方向使用，auto为最大值
* 如果将左和右同时设置成auto，那将各占一般，也就达到居中效果
```html
<body>
	<style>
		.box1{
			/* width 和 height 设置的大小是内容区的大小 不包括boerder的 边框则x2计算 */
			width: 200px;
			height: 200px;
			background-color: aqua;
			border: 10px solid red;
			
			padding-top: 10px;
			
		}
		.box2{
			width: 90px;
			height: 90px;
			background-color: yellow;
			border: 10px green solid;
			/* margin-left: 10px; */
			/* 按最小值来 大于现有的值将不做改变 */
			margin-right: 10px;
			/* bottom和right会把自身以外的盒子挤走 */
			margin-bottom: 10px;
			
		}
		.box3{
			width: 100px;
			height: 100px;
			background-color: blue;
			/* 根据auto左右各占一半特性 可以设置成居中效果 */
			margin: 0 auto;
		}
	</style>
	<div class="box1">
		<div class="box2"></div>
		<div class="box3"></div>
	</div>
</body>
```

* 在相邻的兄弟元素垂直方向的外边距，会产生外边距重叠，会取最大值  
* 只要时相邻的垂直方向 哪怕是父元素也会一同向下或向上
	- 方法一：解决父元素外边距与子元素重叠问题可以通过对子元素设置border-top或者padding-top来解决，但是要减掉对于的px
	- 方法二：可以通过对父元素设置padding-top对子元素进行下移，但是padding会撑大本身的尺寸，所以在设置padding时减掉对于的宽高
	- 方法三：后续有更好的方法
```html
<body>
	<style>
		.box1{
			/* width 和 height 设置的大小是内容区的大小 不包括boerder的 边框则x2计算 */
			background-color:green;
		}
		.box2{
			/* 只要时相邻的垂直方向 哪怕时父元素也会一同向下或向上 */
			margin-top: 100px;
			
			width: 100px;
			height: 100px;
			background-color: yellow;
			margin-bottom: 100px;
			
		}
		.box3{
			width: 100px;
			height: 100px;
			background-color: blue;
			/* 当上面兄弟元素设置margin-bottom100px 再设置本元素margin-top时出发重叠 数值一样或小于兄弟元素的情况保持不变 */
			margin-top: 90px;
		}
	</style>
	<div class="box1">
		<div class="box2"></div>
		<div class="box3"></div>
	</div>
</body>
```
#### 内联盒子模型
* 内联元素a、span等无法直接使用width和height设置尺寸
* 内边距、边框水平方向的设置会影响页面布局、垂直方向不会影响其他元素布局(会覆盖掉其他元素)
* 外边距水平方向不会重叠，而是求和，内联元素不支持垂直方向的设置
* 垂直方向的内边距可以设置但是不会改变内部布局

#### display与visibility
* display可以修改一个元素的类型
* none值可以隐藏元素，位置也会不在 inline-block值设置为行内块  不独占一行
* visibility 默认显示值visible，hidden隐藏元素，但是位置还在

|值	|描述|
| ----| ------|
|none			|此元素不会被显示。|
|block			|此元素将显示为块级元素，此元素前后会带有换行符。|
|inline			|默认。此元素会被显示为内联元素，元素前后没有换行符。|
|inline-block	|行内块元素。（CSS2.1 新增的值）|
|list-item		|此元素会作为列表显示。|
|run-in			|此元素会根据上下文作为块级元素或内联元素显示。|
|compact		|CSS 中有值 compact，不过由于缺乏广泛支持，已经从 CSS2.1 中删除。|
|marker			|CSS 中有值 marker，不过由于缺乏广泛支持，已经从 CSS2.1 中删除。|
|table			|此元素会作为块级表格来显示（类似 &lt;table&gt;），表格前后带有换行符。|
|inline-table	|此元素会作为内联表格来显示（类似 &lt;table&gt;），表格前后没有换行符。|
|table-row-group	|此元素会作为一个或多个行的分组来显示（类似 &lt;table&gt;）。|
|table-header-group	|此元素会作为一个或多个行的分组来显示（类似 &lt;thead&gt;）。|
|table-footer-group	|此元素会作为一个或多个行的分组来显示（类似 &lt;tfoot&gt;）。|
|table-row		|此元素会作为一个表格行显示（类似 &lt;tr&gt;）。|
|table-column-group	|此元素会作为一个或多个列的分组来显示（类似 &lt;colgroup&gt;）。|
|table-column	|此元素会作为一个单元格列显示（类似 &lt;col&gt;）|
|table-cell		|此元素会作为一个表格单元格显示（类似 &lt;td&gt; 和 &lt;th&gt;）|
|table-caption	|此元素会作为一个表格标题显示（类似 &lt;caption&gt;）|
|inherit		|规定应该从父元素继承 display 属性的值。|

#### overflow
* 如果子元素的尺寸大于父元素的尺寸，会导致子元素溢出，overflow就可以处理溢出的内容

|值		|描述														|
| ----|----|
|visible|默认值。内容不会被修剪，会呈现在元素框之外。				|
|hidden	|内容会被修剪，并且其余内容是不可见的。						|
|scroll	|内容会被修剪，但是浏览器会显示滚动条以便查看其余的内容。	|
|auto	|如果内容被修剪，则浏览器会显示滚动条以便查看其余的内容。	|
|inherit|规定应该从父元素继承 overflow 属性的值。					|
```html
<body>
	<style>
		.box1{
			width: 200px;
			height: 200px;
			background-color: yellow;
			
			overflow: scroll;
		}
		.box2{
			width: 100px;
			height: 500px;
			background-color: green;
		}
	</style>
	<div class="box1">
		<div class="box2"></div>
	</div>
</body>
```
#### 文档流
* 文档流处于网页的最底层，属于地基层，所有创建的元素都在这层上面，默认都在文档流里
* `在文档流中，块元素的子元素在不设置宽度的情况下默认占父元素的100%,如果设置了float就不生效，只被内容撑开`
* `内联元素如果开启float则与块元素相反，设置的宽高将会被生效`
* 元素在文档流中的特点
* 块元素
	- 块元素在文档流中会独占一行，块元素会自上而下排列
	- 块元素在文档流中默认宽度是父元素的100%
	- 当元素的高度或宽度的值为auto时，此时指定内边距不是影响可见宽的大小，而是会自动修改宽度,高度只被内容撑开，以适应内边距
	- 块元素在文档流中的高度默认被内容或子元素撑开，
* 内联元素
	- 内联元素在文档流中只占自身的大小，会默认从左向右排列，如果一行中不足以容纳会换到下一行继续自左向右
	- 在文档流中，内联元素的宽度和高度默认都被内容撑开
#### 浮动
* 让3个盒子并排显示  会产生缝隙 块元素与块元素之间写法只能挨着才不会右缝隙
* 想要脱离文档流 可以使用浮动,遇到父元素或者其他浮动元素就停止浮动
* `浮动的元素不会盖住兄弟元素P标签里面的文字`
* `在文档流中，块元素的子元素在不设置宽度的情况下默认占父元素的100%,如果设置了float就不生效，只被内容撑开`
* `内联元素如果开启float脱离文档流则与块元素相反，设置的宽高将会被生效`
* 一旦脱离文档流，都详单与是快元素
```html
<body>
	<style>
		.box1{
			/* 让3个盒子并排显示  会产生缝隙 块元素与块元素之间写法只能挨着才不会右缝隙
				目前处于文档流里面
				想要脱离文档流 可以使用浮动
				遇到父元素或者其他浮动元素就停止浮动
			 */
			/* display:inline-block; */
			
			width: 100px;
			height: 100px;
			background-color:green;
			
			float: left;
		}
		.box2{
			/* display:inline-block; */
			
			width: 100px;
			height: 100px;
			background-color: yellow;
			
			float: left;
		}
		.box3{
			/* display:inline-block; */
			
			width: 100px;
			height: 100px;
			background-color: blue;
			
			float: left;
		}
	</style>
	<div class="box1"></div>
	<div class="box2"></div>
	<div class="box3"></div>
</body>
```
#### 简单布局案例
* 遵循大盒套小盒、小盒套小小盒，一层层往里面套
```html
<body>
	<style>
		*{
			margin: 0;
			padding: 0;
		}
		.header{
			width: 1000px;
			height: 120px;
			background-color: #baf;
			margin: 0 auto;
		}
		.center{
			width: 1000px;
			height: 680px;
			background-color: pink;
			margin: 10px auto;
		}
		.center .left{
			width: 300px;
			height: 100%;
			background-color: yellow;
			float: left;
		}
		.center .cent{
			width: 380px;
			height: 100%;
			background-color: green;
			float: left;
			margin: 0 10px;
		}
		.center .right{
			width: 300px;
			height: 100%;
			background-color: red;
			float: left;
		}
		.footer{
			width: 1000px;
			height: 100px;
			background-color: black;
			margin: 0 auto;
			clear:none
		}
	</style>
	<!-- header头部 -->
	<div class="header"></div>
	
	<!-- center中间内容区域 -->
	<div class="center">
		<div class="left"></div>
		<div class="cent"></div>
		<div class="right"></div>
	</div>
	
	<!-- footer底部区域 -->
	<div class="footer"></div>
</body>
```
#### 高度塌陷问题
* 父元素的宽度不设置默认100%，高度不设置由子元素高度决定
* 但是如果给子元素设置了float浮动，父元素将出现塌陷，不会被子元素所撑起
* 由于父元素出现了高度塌陷，其父元素以下的所有兄弟元素都会跟着往上移，就会导致页面混乱
* **`解决办法：`**
	- 可以将父元素高度写死，不建议使用此方法，因为写死后，父元素将不会根据子元素的高度自适应，且如果子元素高度高出父元素会出现溢出
	- **`元素开启BFC功能，BFC的特性`**
	- **`父元素的外边距不会和子元素重叠`**
	- **`开启BFC的元素不会被浮动元素覆盖`**
	- **`开启BFC的元素可以包含浮动的子元素`**
* **`如何开启BFC`**
	- 设置元素浮动：但是随之宽度也没有了,而且父元素的兄弟元素也会跟着上移
	- 设置元素绝对定位
	- 设置元素为display:inlineblock，会导致宽度丢失
	- **`推荐：将元素的overflow设置为非visible的值 overflow:auto或hidden;IE7以下用zoom:1`**
> * **`解决高度塌陷的最终方案`**
> * **`如果自身浮动后，给自己的兄弟元素设置clear属性可以不受影响`**
> * **`子元素浮动后，父元素塌陷问题，可以给子元素的最后加上一个兄弟元素并设置clear`**
> * **`通过.clearfix:after选择器来设置子元素浮动父元素塌陷问题，里面设置centent:"";display:block;clear:both;`**

|值|说明|
| ----| -----|
|none|元素不会被向下移动以清除浮动。|
|left|元素被向下移动以清除左浮动。|
|right|元素被向下移动以清除右浮动。|
|both|元素被向下移动以清除左右浮动。|
|inline-start|元素被向下移动以清除其包含块的起始侧浮动，即 ltr 时清除左浮动，rtl 时清除右浮动。|
|inline-end|元素被向下移动以清除其包含块的结束侧浮动，即 ltr 时清除右浮动，rtl 时清除左浮动|
#### 导航条

```html
<body>
	<style>
		*{
			margin: 0;
			padding: 0;
		}
		.nav{
			background-color: aquamarine;
			width: 800px;
			margin: 50px auto;
			list-style: none;
			overflow: auto;
		}
		.nav li{
			background-color: blue;
			float: left;
			font-size: 16px;
			line-height: 32px;
			text-align: center;
			
		}
		.nav li a{
			text-decoration: none;
			color: white;
			display: block;
			width: 200px;
			font-weight: bold;
			clear
		}
		.nav li:hover{
			background-color: red;
		}
		
	</style>
	<ul class="nav">
		<li><a href="">首页</a></li>
		<li><a href="">新闻</a></li>
		<li><a href="">资讯</a></li>
		<li><a href="">留言</a></li>
	</ul>
</body>
```
#### 相对定位
* `定位：`
* 定位指的就是将指定的元素摆放到页面的任意位置
* 通过定位可以任意的摆放元素
* 通过position属性来设置元素的定位
* `relative:相对于元素在文档流中原来的位置进行定位`
* 当元素position属性设置为relative时，则元素开启了相对定位
* 1.当开启了元素的相对定位后，而不设置偏移量时，元素不会有任何变化。
* 2.可以通过left right 通配bottom四个属性来设置元素的偏移量
* 3.相对定位的元素不会脱离文档流
* 4.相对定位会使元素提升一个层级
* 5.相对定位不会改变元素的性质，块元素还是块元素，内联还是内联 

|值|描述|
| ----| ------|
|absolute	|生成绝对定位的元素，相对于 static 定位以外的第一个父元素进行定位。元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。|																							|
|fixed|生成固定定位(绝对定位)的元素，相对于浏览器窗口进行定位。元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。							|
|relative|生成相对定位的元素，相对于其正常位置进行定位。因此，"left:20" 会向元素的 LEFT 位置添加 20 像素。											|
|static	|默认值。没有定位，元素出现在正常的流中（忽略 top, bottom, left, right 或者 z-index 声明）。|
|inherit|规定应该从父元素继承 position 属性的值。													|

```html
<style>
	*{
		padding: 0;
		margin: 0;
	}
	.box1{
		width: 200px;
		height: 200px;
		background-color: red;
	}
	.box2{
		width: 200px;
		height: 200px;
		background-color: yellow;
		position: relative;
		left: 200px;
		top: 200px;
	}
	.box3{
		width: 200px;
		height: 200px;
		background-color: yellowgreen;
	}
	
</style>
<div class="box1"></div>
<div class="box2"></div>
<div class="box3"></div>
```

