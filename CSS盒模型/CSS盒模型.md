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
absolute 是最棘手的position值。 absolute 与 fixed 的表现类似，除了它不是相对于视窗而是相对于最近的“positioned”祖先元素。如果绝对定位（position属性的值为absolute）的元素没有“positioned”祖先元素，那么它是相对于文档的 body 元素，并且它会随着页面滚动而移动。记住一个“positioned”元素是指position 值不是 static 的元素。

## 3. float
Float 可用于实现文字环绕图片。<br>
<b>clear:</b>
使用 clear 我们就可以将这个段落移动到浮动元素div下面。你需要用left值才能清除元素的向左浮动。你还可以用right或both来清除向右浮动或同时清除向左向右浮动。<br>

	clear: both;

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



## 8. 盒模型基本属性

### 8.1 border
#### 8.1.1 border的大小
CSS2 指出背景只延伸到内边距，而不是边框。后来 CSS2.1 进行了更正：元素的背景是内容、内边距和边框区的背景。大多数浏览器都遵循 CSS2.1 定义，不过一些较老的浏览器可能会有不同的表现。

#### 8.1.2 border单边属性和简写属性的覆盖
如果把单边属性放在 border-style 之前，简写属性的值就会覆盖单边值 none。

#### 8.1.3 默认的边框颜色
默认的边框颜色是元素本身的前景色。如果没有为边框声明颜色，它将与元素的文本颜色相同。另一方面，如果元素没有任何文本，假设它是一个表格，其中只包含图像，那么该表的边框颜色就是其父元素的文本颜色（因为 color 可以继承）。这个父元素很可能是 body、div 或另一个 table。 

### 8.2 padding

#### 8.2.1 padding宽度为本分比
上下内边距与左右内边距一致；即上下内边距的百分数会相对于父元素宽度设置，而不是相对于高度。

### 8.3 margin
#### 8.3.1 margin合并
外边距合并指的是，当两个垂直外边距相遇时，它们将形成一个外边距。合并后的外边距的高度等于两个发生合并的外边距的高度中的较大者。<br/>
只有普通文档流中块框的垂直外边距才会发生外边距合并。行内框、浮动框或绝对定位之间的外边距不会合并。

### 8.4 width
#### 8.4.1 块级盒的默认宽度
如果未声明宽度，并且盒子是静态或者相对定位的，宽度会保持 100％的宽度，padding和border会向内推动，而不是向外扩展。但是，如果明确设置盒子的宽度为 100％，那么 padding 就会向外延展。

#### 8.4.2 无宽度的绝对定位盒子
未设定宽度的绝对定位的盒子的表现有点不一样。它们的宽度只需要适合它们所包含的内容即可。因此，如果盒中只有一个单词，盒子就会像那个词的表现一样宽。如果变成两个词，盒子的宽度也会相应增加。

#### 8.4.3 无宽度浮动盒子
同无宽度的绝对定位盒子的表现一样。盒子的宽度只需要扩展到所包含内容的宽度，直到其父元素的宽度（其父元素不必是相对定位的）。

## 9. 专题

### 9.1 [CSS实现垂直居中的5种方法](http://www.qianduan.net/css-to-achieve-the-vertical-center-of-the-five-kinds-of-methods/)

#### 9.1.1 table布局
缺点： 

+ Internet Explorer(甚至 IE8 beta)中无效
+ 许多嵌套标签(其实没那么糟糕，另一个专题)	

优点：

+ content 可以动态改变高度(不需在 CSS 中定义)。
+ 当 wrapper 里没有足够空间时， content 不会被截断

例子：

	.wrapper {display:table;} 
	.cell {
    	display:table-cell; 
    	vertical-align:middle;
	}




[百度文库](http://wenku.baidu.com/link?url=EeMM7cm6j0RVegt2IrwAwwgNZFGWkODUmdrgPSHSLMyNMALGFf4i_A1DnumI0qrrmsKgNWvymvLQSgpj4RxqPzEFaM-8Nv7E34Pan93M0a7)