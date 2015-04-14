# CSS盒模型
## 1. display
### 1.1 block
div 是一个标准的块级元素。一个块级元素会新开始一行并且尽可能撑满容器。其他常用的块级元素包括 p 、 form 和HTML5中的新元素： header 、 footer 、 section 等等。<br>
页面居中:

	#main {
		width: 600px; //改进版max-width: 600px (IE7+兼容)
		margin: 0 auto;
	}  

width 一般设置content-box的大小，新属性box-sizing (IE8+兼容)
	
	-webkit-box-sizing: border-box;
       -moz-box-sizing: border-box;
            box-sizing: border-box;


### 1.2 inline
span 是一个标准的行内元素。一个行内元素可以在段落中 <span> 像这样 </span> 包裹一些文字而不会打乱段落的布局。 a元素是最常用的行内元素，它可以被用作链接。

### 1.3 none
它和 visibility 属性不一样。把 display 设置成 none 不会保留元素本该显示的空间，但是 visibility: hidden; 还会保留。

### 1.4 inline-block
你得做些额外工作来让IE6和IE7支持 inline-block 。有些时候人们谈到 inline-block 会触发叫做 hasLayout 的东西，你只需要知道那是用来支持旧浏览器的。

### 1.5 flex

## 2. position

### 2.1 static
static 是默认值。任意 position: static; 的元素不会被特殊的定位。

### 2.2 relative
在一个相对定位（position属性的值为relative）的元素上设置 top 、 right 、 bottom 和 left 属性会使其偏离其正常位置。其他的元素则不会调整位置来弥补它偏离后剩下的空隙。

### 2.3 fixed

+ 一个固定定位（position属性的值为fixed）元素会相对于视窗来定位，这意味着即便页面滚动，它还是会停留在相同的位置。和 relative 一样， top 、 right 、 bottom 和 left 属性都可用。
+ 一个固定定位元素不会保留它原本在页面应有的空隙。
+ 令人惊讶地是移动浏览器对 fixed 的支持很差。

### 2.4 absolute
absolute 是最棘手的position值。 absolute 与 fixed 的表现类似，除了它不是相对于视窗而是相对于最近的“positioned”祖先元素。如果绝对定位（position属性的值为absolute）的元素没有“positioned”祖先元素，那么它是相对于文档的 body 元素，并且它会随着页面滚动而移动。记住一个“positioned”元素是指p osition 值不是 static 的元素。

## 3. float
Float 可用于实现文字环绕图片。<br>
<b>clear:</b>
使用 clear 我们就可以将这个段落移动到浮动元素div下面。你需要用left值才能清除元素的向左浮动。你还可以用right或both来清除向右浮动或同时清除向左向右浮动。<br>
<b>overflow:</b>

	.clearfix {
		overflow: auto;
		zoom: 1;//IE6 hack
	}

## 4. 布局方案
### 4.1 position
### 4.2 float
### 4.3 width百分比
你可以用百分比做布局，但是这需要更多的工作。当窗口宽度很窄时nav的内容会以一种不太友好的方式被包裹起来。
### 4.4 inline-block布局

+ vertical-align 属性会影响到 inline-block 元素，你可能会把它的值设置为 top 。
+ 你需要设置每一列的宽度。
+ 如果HTML源代码中元素之间有空格，那么列与列之间会产生空隙。

### 4.5 column布局
### 4.6 flex布局

+ 支持 px+百分比
+ 支持CSS居中
+ 兼容性较差

## 5. 响应式设计

	@media screen and (min-width:600px) {
	  nav {
	    float: left;
	    width: 25%;
	  }
	  section {
	    margin-left: 25%;
	  }
	}
	@media screen and (max-width:599px) {
	  nav li {
	    display: inline;
	  }
	}

## 6. column

+ 轻松的实现文字的多列布局。
+ 它不被IE9及以下和Opera Mini支持。

三列布局

	.three-column {
	  padding: 1em;
	  -moz-column-count: 3;
	  -moz-column-gap: 1em;
	  -webkit-column-count: 3;
	  -webkit-column-gap: 1em;
	  column-count: 3;
	  column-gap: 1em;
	}

[Learn CSS Layout](http://learnlayout.com)

## 7. 其他
<b>margin合并：</b>
只有普通文档流中块框的垂直外边距才会发生外边距合并。行内框、浮动框或绝对定位之间的外边距不会合并。
