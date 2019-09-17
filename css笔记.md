# css

#### 1、css基础概念

​	CSS (Cascading Style Sheet)即层叠样式表;

​	html是实现对网页结构的定义，通过css样式表可以实现如何显示 HTML 元素，也即是实现对html元素的装饰效果。



#### 2、css分类（按照可书写的位置分类）

- **2.1 内联样式**

  即在标签中通过属性style的方式实现，只对当前元素中的内容起作用，但是这种方式结构和表现有着强耦合关系，不利于后期的维护，开发中不推荐使用。

  ~~~html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>测试css</title>
  	</head>
  	<body>
  		<span style="color: green;">span</span>
  	</body>
  </html>
  ~~~

- **2.2 内嵌样式表**

  即一般在head标签中通过**style标签**进行定义，复用性相对较好，但是也只能在当前页面生效。

  ~~~html
  <!DOCTYPE html>
  <html>
      <head>
          <meta charset="UTF-8">
          <title>测试css</title>
          <style type="text/css">
              span {
                  font-size: 30px;
                  color: #2a9bff;
              }
          </style>
      </head>
  <body>
      <!-- 可以发现将所有span元素都被添加了指定的样式-->
  	<span>我是一个span元素</span>
      <span>我是一个span元素</span>
      <span>我是一个span元素</span>
  </body>
  </html>
  
  ~~~

- **2.3 外部样式表（结构和表现分离）**

  即先新建一个css文件，再在html中通过link元素引入，当样式需要被应用到很多页面的时候，外部样式表将是理想的选择。

  ~~~html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>测试css</title>
  		<link rel="stylesheet" type="text/css" href="my.css"/>
  	</head>
  	<body>
  		<span>我是span元素</span>
  	</body>
  </html>
  ~~~

  ~~~css
  span {
      font-size: 30px;
      color: #2a9bff;
  }
  ~~~



#### 3、不同样式表的优先级

- 当同一个元素被多个样式装饰时，如果有出现样式相同，则采取**“ 就近原则 ”** ，即那个样式离此元素最近，则采用谁。

  默认:    内联样式  >  内嵌样式 >   外部样式



#### 4、 样式表的语法：

​		**选择器：{属性1：值1；属性2：值2；..... }**

​		选择器：  指的是需要改变样式的 HTML 元素

​        { }       ：  我们也叫声明，声明是由一组或多组  属性和属性值   的键值对组成



#### 5、css中的注释

​	/* */  实现多行注释



#### 6、css样式的继承

​	继承是指我们设置上级(父级)的CSS样式，上级（父级）及以下的子级（下级）都具有此属性。

​    **注： 一般只有文字文本具有继承特性，如文字大小、文字加粗、文字颜色、字体等。**

~~~html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>测试css</title>
	</head>
	<body>
        <!--会发现给div加了样式，是会影响到span中的-->
        <div style="color: green;">
			<span>span</span> 
            
            <!--
				假如设置父级文字样式后，其多个子级中，
				可能有些子级颜色不想与父级相同，这个时候只需对对应
				子级设置需要颜色即可。
			-->
            <span style="color: red;">span</span> 
        </div>
	</body>
</html>
~~~



#### 7、选择器

当我们需要对某个元素添加样式或者修改样式时，我们首先需要选中这个元素，那么此时就需要依靠选择器来实现此需求。常见选择器有：

- **7.1 id 选择器 # ** 

  通过在元素中添加id属性实现，然后在样式表中 使用# 选中

  **注： ID属性不要以数字开头，数字开头的ID在 有些浏览器中可能不起作用。**

  ~~~html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>选择器</title>
  		<style type="text/css">
              #span1 {
                  font-size: 30px;
                  color: #2a9bff;
              }
          </style>
  	</head>
  	<body>
  		<span id="span1">我是span元素</span>
  	</body>
  </html>
  ~~~

- **7.2 元素选择器**

  直接通过元素名指定给哪些元素增加样式，可以选中多个元素。

  ~~~html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>素选择器</title>
  		<style type="text/css">
              span {
                  font-size: 30px;
                  color: #2a9bff;
              }
          </style>
  	</head>
  	<body>
  		<span>我是span元素</span>
          <p>我是p元素</p>
          <span>我是span元素</span>
  	</body>
  </html>
  ~~~

- **7.3 类选择器**

  通过在元素上添加class属性，其值可以有多个，中间用空格隔开，然后在style 中通过  .类名选中

  ~~~html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>类选择器</title>
  		<style type="text/css">
              .class1{
                  font-size: 50px;
              }
              .class2{
                  color: red;
              }
              
          </style>
  	</head>
  	<body>
  		<span class="class1 class2">我是span元素</span>
          <p class="class1">我是p元素</p>
          <span>我是span元素</span>
  	</body>
  </html>
  ~~~

- **7.4 派生选择器**

  也叫做上下文选择器，即通过依据元素在其位置的上下文关系来定义样式的选择器。

  比如 我有两个div，分别都要span元素，现在实现，不同div中span元素不一致。

  ~~~html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>派生选择器</title>
  		<style>
  			#div1 span{
  				background-color: aquamarine;
  			}
  			#div2 span{
  				background-color:yellowgreen;
  			}
  			
  		</style>
  	</head>
  	<body>
  		<div id="div1">
             <span>我是span元素</span> 
             <span>我是span元素</span> 
          </div>
          
           <div id="div2">
             <span>我是span元素</span> 
             <span>我是span元素</span> 
          </div>
  	</body>
  </html>
  ~~~

- **7.5 组合选择器**

  可以将任意多个选择器分组在一起，实现相同样式，多个之间用逗号隔开，注意和派生选择器的区别。

  ~~~html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>选择器组</title>
  		<style>
  			h1,p{
  				font-size: 30px;
                  color: #2a9bff;
  			}	
  		</style>
  	</head>
  	<body>
  		<div>
             <h1>我是标题</h1>
             <span>我是span元素</span> 
             <p>我是段落</p> 
          </div>
  	</body>
  </html>
  ~~~



#### 8 、常见样式

- **8.1、背景相关**

  - **（1）、background-color设置背景颜色**

    ~~~css
    #div1{
        width: 100px;
      height: 100px;
        background-color: red;
  }
    ~~~
  
  - **（2）、background-image 指定背景图片**
  
    ~~~css
    background-image: url(image/1.png);
    ~~~
  
- **（3）、背景重复问题   background-repeat**
  
  有些时候，图片不能填充满整个元素时，会自动将图片平铺满整个元素，我们可以通过 background-repeat 对平铺效果进行调整，其值有三个：
  
  repeat-x ：图像只在水平重复
  
  repeat-y ：图像垂直方向上重复
  
  no-repeat ：则不允许图像在任何方向上平铺。
  
  ~~~css
  background-image: url(image/1.png);
  background-repeat: no-repeat;
  ~~~
  
- **8.2 文本字体：**

  - **（1）、字体颜色   color**

    ~~~css
    color: black;
    ~~~
    
  - **（2）、字体类型     font-family**
  
    ~~~css
    /*
        3、font-family 用于指定字体，可以同时指定多个，每个字体间都用逗号隔开
      注： 1、如果我们指定了字体以后，如果浏览器支持该字体，则使用，
        如果不支持则使用浏览器默认的字体。
        有多个字体时，浏览器会优先使用最前面的字体，如果不支持，则使用下一个。
    
        2、浏览器使用的字体是默认从本机上提取的，即计算机中有，浏览器才支持，
        没有就不支持，所以在使用时，尽量不要使用小众的字体，以免用户的计算机不支持
    				*/
    font-family:arial,宋体;
    ~~~
    
  - **（3）、字体大小   font-size，一般默认为16像素**
  
    ~~~css
    /*
    	4、字体默认大小为16px，
    	通过font-size设置字体大小，并不是设定文字本身的大小，
    	在页面中，所有的文字都处于一个看不见的框中（类似于练字本上的方格），
    	font-size设置的是方格的大小。
    */
    font-size: 30px;
    ~~~
    
  - **（4）、行高    line-height**
  
    ​     网页中的文字，每行都被一条看不见的线隔开（类似于写字的单线本），线和线之间的距离就是行高，所有的文字都会默认在行高中垂直居中显示。可以根据行高得出字体间的行间距
  
    **行间距：**指的是字体和字体之间的距离，行间距计算公式如下：
  
    ​			行间距 =  行高 — 字体大小
  
    ~~~html
    <style type="text/css">
       /*
    	5、行高line-height，可以接收3种类型的值
        (1)、像素值
        (2)、百分比，会自动相对字体大小进行百分比计算
        (3)、传整数值，行高就为字体的相应倍数
    
        */
        p{
            font-size: 10px;
        	line-height: 2;
        }
    <style>
    
        <p>
                原标题：香港暴徒侮辱国旗案：1名男子无条件释放，另4人获保释[环球网报道 记者 李东尧]香港警方15日晚曾证实，拘捕5名男女，怀疑他们与8月3日下午于尖沙咀发生的侮辱国旗案有关。据香港东网17日最新消息，经调查后，其中1名被捕22岁男子获无条件释放，另外4名被捕男女（20至22岁）则获准保释候查。据此前报道，本月3日，反对派煽动的“旺角再游行”期间，大批示威者偏离原定游行路线，并行至尖沙咀码头，期间一名身穿黑衣的暴徒，把码头附近海港城外五支旗杆上的一面国旗，强行拆下并抛入海中。警方其后分别拘捕4男1女，并在被捕者住所内检获涉案计算机、电话及一些衣物作进一步调查。
        </p>
    ~~~
    
    **使用小技巧：**  当只有单行文本时，我们可以将行高设置的和父元素的高度一致，使得文本垂直居中。
    
    ~~~html
    <style type="text/css">
        #div4{
            width: 150px;
            height: 100px;
            border: #000000 solid 1px;
            line-height: 100px;
        }
    <style>
    <div id="div4">
    	<a href="##">我是一个a标签</a>
    </div>
    ~~~



#### 9、盒子模型(边框模型)

<img src="1.gif" width=50%>

在css布局中，会将所有的HTML元素看成盒子，

css盒子模型组成结构有：**边距(内外边距)，边框，填充（背景），和实际内容。**

在盒子模型中最内部分是实际的内容，直接包围内容的是内边距，内边距呈现了元素的背景，内边距的边缘是边框。边框以外是外边距，外边距默认是透明的，因此不会遮挡其后的任何元素。

- **9.1 边框border**

  - 常见属性：

    - border-color 边框颜色
    - border-width  边框的宽度
    - border-style  边框的样式

    ~~~html
    <style type="text/css">
    			#div1{
    				width: 100px;
    				height: 200px;
    				
    			
    				/*
    				 1、边框颜色：
    					border-top-color：    上边框颜色
    					border-right-color    右边框颜色
    					border-bottom-color  下边框颜色
    					border-left-color 	  左边框颜色
    				*/
    				/*
    				   统一设置全边框颜色
    				*/
    				border-color: red;
    				
    				
    				
    				/*
    				 2、设置边框的样式：
    						单独对四个边样式做调整
    						border-top-style
    						border-right-style
    						border-bottom-style
    						border-left-style
    						
    					常见值：
    						solid 	定义实线。
    						double 	定义双线。双线的宽度等于 border-width 的值。
    						dashed 	定义虚线。在大多数浏览器中呈现为实线。
    						none 	定义无边框。
    				*/
    			   /*
    			    设置全边框样式
    			   */
    			   border-style: solid;
    			   
    			   
    			   /*
    			     3、设置边框的宽度
    					单独设置
    						border-top-width
    						border-right-width
    						border-bottom-width
    						border-left-width
    					
    					简写：
    						border-width
    						如果书写4个值 ，分别表示将这些值设置给 上 右 下 左 四个边框，按照瞬时针顺序
    						如果书写3个值 ，分别表示将这些值设置给 上 左右 下 四个边框
    						如果书写2个值 ，分别表示将这些值设置给 上下 左右 四个边框
    						如果书写1个值 ，分别表示将这些值设置给 上下左右  四个边框
    			   */
    			   border-width:10px;
    			}
    			
    			
    			#div2{
    				width: 100px;
    				height: 200px;	
    				/*
    					简写形式：
    						 可以同时指定边框的样式、颜色、宽度，且对书写顺序无要求
    				 */
    				border: 20px groove #DEB887;
    			}
    			
    			
    </style>
    
    <div id="div1"></div>
    
    <div id="div2"></div>
    ~~~
  
- **9.2、内边距 padding**

  元素内容和边框之间的边距叫做内边距，分别有四个属性

  | 描述           | 属性                 |
  | -------------- | -------------------- |
  | padding-bottom | 设置元素的下内边距。 |
  | padding-left   | 设置元素的左内边距。 |
  | padding-right  | 设置元素的右内边距。 |
  | padding-top    | 设置元素的上内边距。 |

  ~~~html
  <style type="text/css">
  			#box{
  				width: 150px;
  				height: 200px;
  				border:solid #87CEEB 2px;
  				
  				/*
  				  设置内边距：
  					分别设置上、右、下、左内边距
  					padding-top
  					padding-right
  					padding-bottom
  					padding-left
  					
  				  简写写法：
  					对padding： 而言
  					如果书写4个值 ，分别表示将这些值设置给 上 	右 	下	 左
  					如果书写3个值 ，分别表示将这些值设置给 上 	左右  下 
  					如果书写2个值 ，分别表示将这些值设置给 上下 左右 
  					如果书写1个值 ，分别表示将这些值设置给 上下左右  
  				*/
  		 	   padding-left: 50px; 
  			   
  			   
  			   /* 	
  				 使用padding时会导致父元素被撑大对应的内边距长度
  					即    父元素宽  =  边框 + 内边距宽 + 内部元素宽
  						  父元素高  =  边框 + 内边距高 + 内部元素高 
  				  如果期望父元素不被撑大，则可对父元素添加：
  					   box-sizing: border-box;
  				  这样就会把borders和padding全都包含在定义的宽高里面。
  				  这就意味着一个带有2px边框的200px的div仍然宽度是200px。
                  
                  
                    当然可以在设置父元素时，将父元素的实际宽高设置成扣除了
  				  边框和内边距后的宽高。
  				*/
  			   box-sizing: border-box;
  			}
  			
  			#context{
  				width: 100px;
  				height: 100px;
  				background-color: #000000;
  			}
  </style>
  
  <div id="box">
  	<div id="context"></div>
  </div>
  ~~~
  
- **9.3、外边距 margin**

  当前盒子和其他盒子的间距，也是有上下左右是个属性，用法同padding。

  其中左外边距 和 上外边距是影响盒子自身的位置，

  ​		而右和下外边距 是会影响其他盒子的位置（因为会挤动其他盒子），

  **注1:**  外边距不会影响盒子的大小

  **注2： **外边距可以为负数

  **注3：**margin值可以设置为auto，一般其是设置给水平方向的。

  ​	     如果设置 左或 右外边距的值为auto，此时会将此方向边距设置为最大值，

  ​         如果垂直方向（即上下外边距）值设置为auto，表示外边距值为0。

  ~~~html
  <style type="text/css">
      #div1{
          width: 200px;
          height: 200px;
          background-color: #008000;
  
          /* 
          margin外边距
          1、使用时，不会将自身给撑大，但是会影响其他元素的位置，
          其中 左和上 外边距主要是影响盒子自身的位置，
          右和下 外边距会影响其他盒子的位置（因为会挤动其他的盒子）
  
          2、外边距可以是负数
  
          3、margin的值可以设置为auto，该值一般给水平方向设置。
          如果 左或右 外边距值设置了auto，表示给此方法上的外边距设置为最大值。
          如果 上或下 外边距值设置了auto，表示给此方法上的外边距设置为0。
  
          小技巧：
          margin:0 auto;  将当前元素在此父元素中 设置成 水平居中
          */
          margin-top: auto;
          margin-left: auto;
          margin-bottom: 20px;
      }
      #div2{
          width: 200px;
          height: 200px;
          background-color:cyan;
          margin-left: -150px;
      }
      #div3{
          width: 200px;
          height: 200px;
          background-color:tan;
          margin:0 auto;
      }
  </style>
  ~~~



#### 10、overflow控制元素内容溢出

​	     在css布局时，如果父元素中内容部分的大小，超出了父元素的大小，则会出现内容溢出现象，此时我们可以通过overflow属性实现： 当出现内容溢出元素框时，在对应的元素区间内添加滚动条。

overflow属性有以下值：

| 值      | 描述                                                         |
| ------- | ------------------------------------------------------------ |
| visible | 默认值。内容不会被修剪，会呈现在元素框之外。                 |
| hidden  | 溢出内容会被修剪，且不可见                                   |
| scroll  | 溢出内容会被修剪，为父元素添加滚动条，来查看被修剪内容，但是该属性不管内容是否溢出都会创建水平方向和垂直方向的滚动条，不智能 |
| auto    | 溢出内容会被修剪，自动根据实际情况添加滚动条                 |
| inherit | 规定应该从父元素继承 overflow 属性的值。                     |

~~~html
<style type="text/css">
			#box{
				width: 150px;
				height: 200px;
				border:solid #87CEEB 2px;
				overflow: auto;
				
			}
			
			#context{
				width: 500px;
				height: 50px;
				background-color: #000000;
			}			
</style>

<div id="box">
	<div id="context"></div>
</div>
~~~



#### 11 、文档流、浮动、定位

- **11.1、文档流**

  - **（1）、文档流**

    这里的文档指的就是html文档，文档流指的是元素排版布局过程中，元素会**默认**自动从左往右，从上往下的**流式排列方式**。并最终窗体自上而下分成一行行，并在每行中从左至右的顺序排放元素。

  - **（2）、文档流中两种级别元素**

    按元素级别分为 **块级元素** 和 **行内（内联）元素**，

    块级元素：  有宽高，独占一行

    行内元素： 无宽高，默认的宽度就是文字的宽度，与其他元素并排

  - **（3）不同级别元素在文档流中的特点**

    在文档流中，内联元素默认从左到右流，遇到阻碍或者宽度不够自动换行，继续按照从左到右的方式布局。块级元素单独占据一行，并按照从上到下的方式布局。

- **11.2  浮动 float** 

  块级元素在文档流中垂直排列，使用flaot可以是当前	元素脱离文档流，（有点类似，原本当前和其他元素多处于一个平面，但是通过浮动，当前元素便飘到了其他元素上空）

  float属性的值如下：

  | 值      | 描述                                                 |
  | ------- | ---------------------------------------------------- |
  | left    | 元素向左浮动。                                       |
  | right   | 元素向右浮动。                                       |
  | none    | 默认值。元素不浮动，并会显示在其在文本中出现的位置。 |
  | inherit | 规定应该从父元素继承 float 属性的值。                |

  ~~~html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title></title>
  		<style type="text/css">
  			#div1{
  				height: 200px;
  				background-color: #008000;
  				line-height: 200px;
  				/* 
  				  浮动元素的特点：
  					1、浮动的元素脱离文档流以后，只会向左或者向右移动，直到碰到
  					   父边框 或者另一个浮动元素的边缘为止。
  					2、当一个元素浮动以后，其会立即脱离文档流，那么此时它之后的元素
  					   会立即向上移动，顶替其原来的位置。
  					   
  					3、一个元素浮动以后，可能会遮盖着它后面顶替上来的元素，
  					   但是只是遮盖这个元素，并不会遮盖里面的文字内容，
  					   文字会包裹在浮动元素周围 或 尽可能的显示在原位置
  					   
  					4、如果浮动的元素前面是一个未浮动的块级元素，则此浮动元素
  					   不能超过此块级元素
  					   
  					5、浮动的元素，垂直方向上不能超过他的兄弟元素
  					
  					6、在文档流，块级元素如果不指定宽度，默认宽度为父类的整个宽度，
  					   但是在脱离文档流以后，在不指定的情况下，为此元素内容的宽度。
  					
  					7、当行（内联）元素 浮动以后，会自动变成块级元素。
  				 */
  				float:right;
  			}
  			
  			
  			#div2{
  				width: 200px;
  				height: 200px;
  				background-color:cyan;
  				float:right;
  			}
  			
  			#div3{
  				width: 200px;
  				height: 200px;
  				background-color:tan;
  				line-height: 200px;
  			}
  			
  			span{
  				width: 200px;
  				height: 200px;
  				background-color:red;
  				float: left;
  			}
  		</style>
  	</head>
  	<body>
  		
  		<div id="div1">
  			<h2>div1</h2>
  		</div>
  		
  		<div id="div2">
  			 <h2>div2</h2>
  		</div>
  		
  		<div id="div3">
  			<h2>div3</h2>
  		</div>
  		
  		<span>我是span</span>
  	</body>
  </html>
  
  ~~~
  
- **11.3、浮动带来的高度塌陷问题**

  ~~~html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>浮动——高度塌陷问题</title>
  		<style type="text/css">
  			#div1{
  				border: 5px solid red;
  			}
  			#div2{
  				width: 100px;
  				height: 100px;
  				background-color: #008000;
  				border: 1px solid cadetblue;
  				
  				/* 
  				 高度塌陷问题：
  						在子元素浮动之前，父元素的高度是由子元素撑起来的，
  						现在由于子元素浮动，其会脱离文档流，此时会发现父元素
  						的高度瞬间消失。并且此时还可能会导致父元素后面的所有兄弟
  						元素的位置跟着发生变化。
  				 */
  				float: right; 
  			}
  			
  			#div3{
  				width: 100px;
  				height: 100px;
  				background-color: gold;
  				border: 1px solid black;
  			}
  		</style>
  	</head>
  	<body>
  		
  		<div id="div1">
  			<div id="div2">
  				
  			</div>
  		</div>
  		
  		<div id="div3">
  		
  		</div>
  	</body>
  </html>
  ~~~
  
- **11.4、解决高度塌陷问题**

  - 思路1 ：让父元素也跟着浮动，但是其宽度会丢失，脱离文档流以后，宽高只能根据子元素来定了

  - 思路2：将父类元素设置成 inline-block 行内块元素，但是宽度依然会丢失

  - 思路3：将元素的overflow 设置成一个非visiable值，一般推荐是hidden

     	  注：此种方式在ie6中不能生效。
    
  - 思路4： 在要浮动的子元素后 跟一个空的高度相同的兄弟元素，当子元素浮动后，其兄弟元素还有高度，依然可以撑起父元素。

    ​	      

- **11.5、清除浮动对其他元素的影响**

  ​	有些时候，当某个元素浮动上移，其后的元素会顶替他原来的位置，如果我们不希望此事发生，可以在当前元素样式中添加clear属性， 清除前面元素对自己造成的浮动影响。

  clear的值如下：

  | 值      | 描述                                  |
  | ------- | ------------------------------------- |
  | left    | 清除左浮动带来的影响。                |
  | right   | 清除右浮动带来的影响。                |
  | both    | 清除两边浮动带来的影响。              |
  | none    | 默认值。不清除浮动                    |
  | inherit | 规定应该从父元素继承 clear 属性的值。 |

  ~~~html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>clear清除浮动带来的影响</title>
  		<style type="text/css">
  			#div1{
  				width: 200px;
  				height: 200px;
  				background-color: #008000;
  				line-height: 200px;
  				float:right;
  			}
  			
  			#div2{
  				width: 200px;
  				height: 200px;
  				background-color:cyan;
  				clear: right;
  			}
  		</style>
  		
  	</head>
  	<body>
  		<div id="div1">
  			<h2>div1</h2>
  		</div>
  		
  		<div id="div2">
  			 <h2>div2</h2>
  		</div>
  	</body>
  </html>
  ~~~
  
- **11.6、定位**

  即将指定的元素放在页面任意位置，它允许你定义元素框相对于其正常位置应该出现的位置，或者相对于父元素、另一个元素甚至浏览器窗口本身的位置。

  实现定位可以通过position 属性实现，其常见值如下：

  | 值       | 描述                                                         |
  | -------- | ------------------------------------------------------------ |
  | static   | 默认值。没有定位，元素出现在正常的流中（忽略 top, bottom, left, right 或者 z-index 声明）。 |
  | relative | 生成相对定位的元素                                           |
  | absolute | 生成绝对定位的元素                                           |
  | fixed    | 生成固定定位的元素，相对于浏览器窗口进行定位。               |

  **注：**当我们通过position 开启了元素定位，即其值为非static值时，可以通过设置left 、right、top、bottom四个值来调整元素的位置。

  - left  ： 元素相对其定位位置左侧的偏移量
  - right： 元素相对其定位位置右侧的偏移量
  - top ： 元素相对其定位位置上侧的偏移量
  - bottom ：元素相对其定位位置下侧的偏移量

- **11.7 、 相对定位**

  相对其在文档流中的原始位置处开始进行定位偏移，不会脱离文档流，不会影响其他元素的位置。

  ~~~html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>相对定位</title>
  		<style type="text/css">
  			#div1{
  				width: 200px;
  				height: 200px;
  				background-color: #008000;
  				line-height: 200px;
  				
  				position: relative;
  				left: 50px;
  				top: 100px;
  			}
  			
  			#div2{
  				width: 200px;
  				height: 200px;
  				background-color:cyan;
  			}
  		</style>
  		
  	</head>
  	<body>
  		<div id="div1">
  			<h2>div1</h2>
  		</div>
  		
  		<div id="div2">
  			 <h2>div2</h2>
  		</div>
  	</body>
  </html>
  ~~~
  
  
  
- **11.8、绝对定位**

  只能根据祖先类进行定位（父类以上），且该祖先类的position 值必须是非static的，如果没有，就继续往上找，直到找到位置，如果都没有，则最终以html标签为参照，**且元素会脱离文档流，设置偏移量以后，会影响其他元素的位置定位。**

  ~~~html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title>绝对定位</title>
  		<style type="text/css">
  			#div1{
  				width: 200px;
  				height: 200px;
  				background-color: #008000;
  				line-height: 200px;
  				
  				position: absolute;
  				left: -100px;
  			}
  			
  			#div2{
  				width: 200px;
  				height: 200px;
  				background-color:cyan;
  				clear: both;
  			}
  			
  			#subDiv{
  				width: 50px;
  				height: 50px;
  				background-color:skyblue;
  				position: absolute;
  				left: 400px;
  				
  			}
  		</style>
  		
  	</head>
  	<body>
  		<div id="div1">
  			<div id="subDiv">
  				
  			</div>
  		</div>
  		<div id="div2">
  			
  		</div>
  	</body>
  </html>
  
  ~~~

  

- **11.9、固定定位**

  大部分特点和绝对定位一样，只不过固定定位永远相对浏览器窗口进行定位的。

  固定定位会定在窗口的某个位置，不会顺窗口滚动条变化（比如网页上常见的牛皮癣广告）
  
  ~~~html
  <!DOCTYPE html>
  <html>
  	<head>
  		<meta charset="utf-8">
  		<title></title>
  		<style type="text/css">
  			#div1{
  				width: 200px;
  				height: 250px;
  				border: 1px #000000 #87CEEB;
  				background-color: #FFD700;
  				position: fixed;
  				right: -50px;
  				bottom: 30%;
  			}
  			#box{
  				width: 200px;
  				height: 100000px;
  				border: 1px #000000 #87CEEB;
  				background-color: burlywood;
  				margin-left: auto;
  			}
  			
  		</style>
  	</head>
  	<body>
  		
  		<div id="box">
  			
  			
  		</div>
  		
  		<div id="div1">
  			我是牛皮癣广告
  		</div>
  	</body>
  </html>
  
  ~~~
  
  