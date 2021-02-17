# [CSS 基础]()

## 1  引入方式

-   内联样式，不需要引用css，直接作用于html元素，但是没有遵循结构和表现分离的原则

    ```html
    <p style="color: red;">1111</p>
    ```

    

-   嵌入式样式，在head里，title之后，一般来说，定义的选择器都要引用，或者其他选择器，直接作用于作用域

    ```html
    <style>
            p{
                color: red;
            }
        </style>
    ```

-   外部样式表

    不需要style标签

    rel：角色，告诉浏览器，这是一个样式表文件（stylesheet）

    href：文件来源，链接地址

    ```html
    <link rel="stylesheet" href="index.css">
    ```

-   导入外部样式表

    ```html
    <style>
            @import url(index.css);
        </style>
    ```

    **要写在style最前面**





## 2  类型



###### 基本选择器

-   *（通配选择器）匹配任何一个html标签

-   id （ID选择器）匹配被唯一引用的一个html标签，一个ID选择器，只能被引用一次

-   class（CLASS类选择器）匹配被引用的所有html标签

-   E（element元素选择器）自动匹配选择器同名的所有标签，如h1，匹配页面中所有h1

    **!important >ID > CLASS > E > ***

    -   ```html
        p{
        	color:red !important
        }
        ```

        提高某一个css属性到最高级，不是p的所有属性

    -   css始终遵循最近优先选择的原则，在同一个样式表中，后面定义的css属性，当他们前面定义的css属性，都作用于同一个html时，后面的定义的起作用



###### 复合选择器

复合选择器就是两个或多个基本选择器，通过不同方式连接而成的选择器。
    
    -   交集
    -   并集
    -   后代、子元素选择器
    -   兄弟选择器
    -   属性选择器





## 3  css属性

### 3.1  文字属性（font）

-   font-style：字体样式，斜体样式。
    -   normal：取消斜体样式
    -   italic：斜体样式
    -   

-   font-variant：规定是否以小型大写字母的字体显示文本
-   font-weight：加粗或变细
-   font-size：字号大小，
-   line-height：行高，也叫行间距离
-   font-family：字体
-   color：颜色
    -   颜色名：如red
    -   十六进制：#ff0000（red)，每个字符的取值范围是：0-9，a-f，
    -   RGB（红，绿，蓝）
    -   RGBA（红，绿，蓝，透明度）：每个颜色的取值范围是0-255，透明度取值范围为0-1
-   letter-spacing：字符间距
-   word-spacing：单词间距（英文有效）
-   text-align：文本在块元素中的对齐方式
    -   left（默认）
    -   center
    -   right
-   text-decoration
    -   none：无（主要用于取消下划线）
    -   underline：下划线
    -   overline：上划线
    -   line-through：删除线
-   text-indent：首行缩进，值是一个固定值或相对值
-   text-transform：控制文字的大小写转换
    -   capitalize：每个单词的首字母大写
    -   uppercase：全部大写
    -   lowercase：全部小写

### 3.2  css中的单位

-   可变单位：em（字号大小的倍数），rem，vw，vh，%
-   可固定的单位：cm，mm，pt，pc，in，px

### 3.3  列表属性

-   list-style-type：
    -   none
    -   disc：
    -   circle：
    -   square
    -   decimal
-   list-style-position：
    -   inside：显示在列表内容的位置
    -   outside（默认）：显示在列表内容的左侧

-   list-style-image：
    -   优先显示图片项目符号
    
    ```css
        list-style-image：url(001.jpg);
    ```
    
-   在实现开发时，应该清除列表的上、下、左边的留白

    ```css
    *{
    	margin:0px;
    	padding:0px;
    }
    //IE==>margin-left:40px;
    chrome==>padding-left:40px;
    ```

    list-style是list-style-type、list-style-image、list-style-positionr的缩写

### 3.4  背景属性

-   background-attachment：设置背景图片是否固定或者随着页面的其余部分滚动

-   background-color：设置元素的背景颜色

-   background-img：设置元素的背景图像

-   background-position：设置背景图像的开始位置

-   background-repeat：设置是否及如何重复背景图像

    ```css
    background-img：url（001.jpg）；
    
    background-repeat：repeat-x；/*横向重复显示*/
    background-repeat：repeat-y；/*纵向重复显示*/
    background-repeat：repeat；/*默认值，重复显示*/
    background-repeat：no-repeat；/*不重复显示*/
    
    /*控制图片的位置*/
    /*1.固定值*/
    background-position：X(横向) Y（纵向）;
    background-position:100px 50px;
    ```

2.方向

![image-20201020163511285](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201020163511285.png)

```css
/*3.百分比*/
background-positio:0% 50%;
```

-   百分比时，容器的点与图片的点相对应，点点对应，固定值时，图片的左上角与容器相对应

![image-20201020164822149](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201020164822149.png)

-   background-size
    -   contain：保证最大的那边的值完整的显示出来
    -   cover：保证最小的那边的值完整的显示出来
    -   百分比
    -   固定的宽高值
-   background-attachment
    -   fixed：页面滚动时，背景图不动
    -   scroll：背景图滚动，默认值
    -   inherit：从父元素继承

![image-20201020170704033](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201020170704033.png)

### 3.5  浮动原理

如果height==line-height，块元素中，**单行文本**就会在块元素中垂直居中显示



###### 文档流

-   原始文档流，也叫自然文档流。按照HTML结构来自然排版
-   浮动文档流，通过float属性来控制布局
-   定位文档流，通过定位css来控制布局



###### 浮动布局方式

-   原始文档流布局
-   浮动文档流布局
-   定位文档流布局
-   盒模型文档流布局



###### 浮动原理

-   一个块元素添加float属性后，宽度变成实际内容的大小宽度
-   一个元素浮动后，它在原来的位置，直接脱离了原始的文档流，变成了浮动的文档流，并且显示在原始文档流的上一层，会遮挡原始文档流
-   原始文档流中的文本内容，会受浮动元素的影响，跟随浮动元素显示（紧挨着浮动元素与浮动方向相反的一侧进行排版显示）
-   当所有子元素都浮动后，会导致父元素下没有原始文档流，父元素
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   
-   就没有内容撑起它的高度。那么高度就为0
-   浮动塌陷会导致后面的内容，显示在父元素所在的位置，也就是显示在浮动元素的下层，被遮挡住
-   如果一行显示不下所有的浮动内容，就会往下



###### 浮动目的

让纵向排版的内容，实现横向排版。



###### 如何处理浮动塌陷的问题?

-   给浮动的父元素添加高度
-   让父元素也变成浮动元素，并且后续的一个原始文档流需要使用clear来清除浮动的影响
    -   clear
        -   left
        -   right，上一个元素是向左浮动时，right就不起作用
        -   both，清除左浮动、右浮动的影响。
-   给父元素添加overflow：hidden（溢出隐藏，浏览器是把父元素高度修正为子元素的高度）；
-   只给后续添加clear，但是浮动的父元素没有高度，存在bug，不推荐



###### 超链接的四个伪类

顺序不可颠倒，非a标签只有hover一个伪类

-   link，默认

-   visited，访问之后的样式

-   hover，鼠标悬在上面时的样式

-   active，鼠标按下时的样式

    ```css
    .tools>li>a:link{
    	display:inline-block;
    	width:80px;
    }
    让a标签变成内联块
    ```



###### block、inline、inline-block的区别

-   **行内元素**：又叫**内联元素**，
    特点是行高以及底边距不可改变，只。0度)；
    行内的元素都会在同一条直线上，也就是水平布局的；
    默认不会换行(不强制换行)。

    ```html
    常见的行内元素有：<span>、<br>、<em>、<input>、<a>、<label>、<img>、<strong>、<select>、<textarea>、<sub>、<sup>、<small>等。
    ```

-   **块级元素**：是一个元素，占用了全部宽度，在前后都是换行符。
    可以设置width、height、padding、margin等属性。

    ```html
    常见的块元素有：<h1~6>、<p>、<form>、<table>、<ul>、<ol>、<li>、<dl>、<hr>、<div>等。
    ```

-   **block**：

    -   block元素会独占一行，多个block元素会各自新起一行。默认情况下，block元素宽度自动填满其父元素宽度。
    -   block元素可以设置width,height属性。**块级元素即使设置了宽度,仍然是独占一行。**
    -   block元素可以设置margin和padding属性。

-   **inline**：

    -   inline元素不会独占一行，多个相邻的行内元素会排列在同一行里，直到一行排列不下，才会新换一行，其宽度随元素的内容而变化。
    -   inline元素设置width,height属性无效。
    -   inline元素的margin和padding属性，水平方向的padding-left, padding-right, margin-left, margin-right都产生边距效果；
    -   但竖直方向的padding-top, padding-bottom, margin-top, margin-bottom不会产生边距效果。

-   **inline-block**：

    -   简单来说就是将对象呈现为inline对象，但是对象的内容作为block对象呈现。之后的内联对象会被排列在同一行内。
    -   比如我们可以给一个link（a元素）inline-block属性值，使其既具有block的宽度高度特性又具有inline的同行特性。

-   **行内元素和块级元素的区别**：

    -   块级元素独自占一行且宽度会占满父元素宽度，行内元素不会独占一行，相邻行内元素可以排在同一行
    2. 块级元素可以设置width和height，行内元素设置width和height无效，而且块级元素即使设置宽度也还是独占一行
    3. 块级元素可以设置margin和padding属性，行内元素水平方向的margin和padding如margin-left、padding-right,可以产生边距效果，但是竖直方向的如padding-top和margin-bottom不会产生边距效果。

-  **常见用法 display**：

    3. 其中块级元素对应display：block，一是显示，一是块级
    3. 行内元素对应display：inline。
    3. 可以通过修改元素的display属性来切换行内元素和块级元素。
    3. display：inline-block；可以让元素具有块级元素和行内元素的特性：既可以设置长宽，可以让padding和margin生效，又可以和其他行内元素并排。
    3. table-cell：单元格模式，具有td的功能

-  **案例(简单实现导航栏)**：

    ```html
    <!DOCTYPE html>
    <html>
    	<head>
    		<meta charset="utf-8">
    		<title>other</title>
    		<style>
    			ul{
    				margin: 0 auto;
    				text-align: center;
    			}
    			/*将块级元素转换成内联元素*/
    			ul li{
    				line-height: 50px; /*与height设为一致 则字体垂直居中显示*/
    				width: 80px;
    				display: inline-block;
    				height: 50px;
    				text-align: center;
    				background-color: greenyellow;
    			}
    		</style>
    	</head>
    	<body>
            <ul>
            	<a href="#"><li>News</li></a>
            	<li>Sport</li>
            	<li>Read</li>
            	<li>War</li>
            	<li>Games</li>
            </ul>
    	</body>
    </html>
    
    ```

    ![image-20201021132851526](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201021132851526.png)

### 3.6  盒模型

盒子模型是css布局一种布局的概念，它把一个块（容器）理解为以下css属性的构成

-   盒模型之padding：内留白，内边距
    -   padding：top right  bottom left
    -   一个参数时是四边
    -   两个参数是是上下、左右
    -   三个参数时是上、右、下，左边没有找右边
    -   四个参数时是上、右、下、左

-   边框（border）
    -   border-width：边框粗细
    -   border-style：边框样式
        -   solid：实线
        -   dashed：虚线
        -   dotted：点线
    -   边框的大小，会影响盒子模型的总宽度和总高度

-   轮廓（outline）
    
    -   渲染出边框的效果，不会影响盒子模型的宽高
-   border-radius（圆角）,依赖于border使用
    
    -   半径（X/Y)
-   box-shadow（阴影）
    
    -   box-shadow：h-shadow（水平方向)  v-shadow（垂直方向） blur（模糊值） spread（阴影的尺寸） color（颜色)  inset（内部阴影），水平和垂直都为0时，四周就都有阴影
    
        ```css
        box-shadow:0px 0px 5px 1px red;
        ```



### 3.7  选择器

![image-20201022092228741](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201022092228741.png)

![image-20201022092256017](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201022092256017.png)



![image-20201022094635917](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201022094635917.png)



![image-20201022094733353](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201022094733353.png)



contain？

![image-20201022095613840](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201022095613840.png)

-   属性选择器

    一般用于表单元素的时候比较多，蛀牙是去匹配html的标签属性和标签属性的值

    元素名：【元素名=值】

    ![image-20201023104722658](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201023104722658.png)

![image-20201023104804508](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201023104804508.png)

-   关系选择器
    -   子元素选择器

        ​	E>F{}

        ![image-20201023105520038](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201023105520038.png)

    -   后代元素选择器

        E  F{}

        ```css
        div li{
        	color:red;
        }
        ```

    -   兄弟选择器

        E+F{},只选择下面相邻的选择器

        ![image-20201023110718219](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201023110718219.png)

        ```html
        <!DOCTYPE html>
        <html lang="en">
        <head>
            <meta charset="UTF-8">
            <meta name="viewport" content="width=device-width, initial-scale=1.0">
            <title>Document</title>
            <style>
                h5+p{
                    color: red;
                }
            </style>
        </head>
        <body>
            <p>111</p>
            <h5>222</h5>
            <p>333</p>
            <p>444</p>
            <p>555</p>
        </body>
        </html>
        ```

        ![image-20201023111052085](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201023111052085.png)

    -   所有兄弟选择器（css3新增的）

        E~F{},匹配**之后的所有**兄弟元素

-   伪类选择器

    before、after、first。。。。

### 3.8  position定位

一个页面中，尽量减少定位的布局

一般布局都是自然文档流、浮动布局，盒子模型，最后才选择定位布局

如果没有背景色，就改用相对定位来修改显示的层次，设置元素显示的层次，默认是0，数字越大，就越显示在屏幕中最上层，可以是负值

-   relative（相对定位）、以元素**自己原来的位置**为参考位置，进行位置偏移，偏移后，元素原来的位置空间还在，其他元素不会移动上去替代它
    -   top
    -   left
    -   right
    -   bottom
    
-   absolute（绝对定位）

    绝对定位元素，是参照，离它“最近的”，“己定位的”父级元素”进行定位，定位后，它原来的位置不会被保留，后面的HTML元素，就会占据它原始的位置。实际原理就是，当前元素脱离了原始文档流，变成了一个内联元素，他的宽度就变成元素内容的宽度。如果没有在父级上找到以定位的元素，最后一定是找HTML根元素来参照定位。（浏览器的边框)

    如何把一个未定位的元素，变成以定位的元素？

    给他设置position：“relative”![image-20201022163655681](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201022163655681.png)

-   fixed（固定定位）

    直接参照浏览器的边框（HTML），进行定位的位置偏移

    也会脱离文档流，也是一种绝对定位

-   static（静态定位）

    取消定位效果，或者叫没有定位

clac（100% * 4),运算符两边必须加空格，不然不会生效



3.9  

before、after





## 4  CSS3

CSS3:
CSS3是CSs第三版，是一个标准。主要在CSS2的基础上，新增一些的特性。如动画、过渡、转换，还有新的选择器。。 

### 4.1  新增的选择器

-   nth-child（n）

    是第几个子元素，并且叫什么

-   first-child（n）

    是第一个子元素，并且叫什么

-   last-child（n）

    是最后一个子元素，并且叫什么

-   only-child（n）

    是父元素下的唯一一个子元素，并且叫什么

-   nth-last-child（n）

    是倒数第几个子元素，并且叫什么 

-   nth-of-type（n）

    是什么的第几个（例：把子元素按指定的h4来分类，匹配列表中的第二个h4）

-   nth-last-of-type（n）

    是什么的倒数第几个

-   only-of-type（n）

    例：按h4分类后，匹配唯一一个h4，先分类，在匹配唯一

-   first-of-type

    匹配分类后，第一个叫什么的元素

-   last-of-type

    匹配分类后，最后一个叫什么的元素





-   ：root

    找到的就是根元素html

-   ：empty

    找到的是没有元素内容的html标签，任何有文字、空格、子元素都不能匹配





###### 状态伪类选择器

-   ：disable

    匹配禁用状态时

-   ：enabled

    匹配允许使用状态时

-   ：checked

    匹配是被选中状态时

-   ：：selection

    匹配文本被鼠标选中状态时

-   not（）

    排除所有匹配项中，指定的选择器所匹配的内容，其他匹配项样式起作用。。。。。不同的写法。。。。。



### 4.2  a标签的锚点用法

点击链接是，是跳到页面中某一个锚点的位置

1.  埋下一个锚点
2.  跳转到锚点 href=“#锚点名称”



### 4.3  隐藏和显示

display：none；隐藏，但是会脱离文档流，回收位置，下面内容往上移

visibility：hidden，隐藏，隐藏后不脱离文档流

opacity：0，隐藏，隐藏后不脱离文档流



visibility：visible，显示

opacity：1，显示

display：block，显示，会加入文档流，下面内容往下移



### 4.4  @font-face，自定义字体图标

iconfont.cn下载图标

把解压后的文件夹，放到项目工程中去

在html文件中，通过link，应用外部css文件

在标签中，通过class=“iconfont icon-图标名”来引用图标

字体图标，是矢量化的，可以放大、缩小、改颜色，而不像图片那个会失真!不能改颜色!

。。。。。。。

font awesome。。。

自定义字体 ttf文件 定义字体图标名称。。。。。   

一定要使用伪元素来放Unicode字符码

  

### 4.5  过渡

transition：过渡的css属性名 动画时长 动画变化的类型  动画开始时间（延迟）

过度的css属性名和动画时长必须写

display隐藏显示元素时，不能实现添加过度效果、opacity可以，visibility不能，还可以控制高宽来控制显示与隐藏



### 4.6  动画

1.  定义动画规则

    ```css
    1.使用from、to
    @keyframes name{
        from{
            width:150px;
        }
        to{
            width:0px;
        }
    }
    
    
    2.使用百分比，即在某一个时间节点时，让html原色的css样式，变成什么样子
    @keyframes name{
        0%{}
        5%{}
        10%{}
        50%{}
        90%{}
        100%{}
    }
    ```

2.  给目标元素添加一个动画属性

    ```css
    animation:name 时间 快慢节奏 等待时间 播放次数 下一周期是否逆向播放（alternate） animation:name 时间 快慢节奏 等待时间 播放次数 下一周期是否逆向播放（alternate） 
    ```

-   快慢节奏(animation-timing-function)：
    | 值          | 描述                                           |
    | :---------- | :--------------------------------------------- |
    | linear      | 动画从头到尾的速度是相同的。                   |
    | ease        | 默认。动画以低速开始，然后加快，在结束前变慢。 |
    | ease-in     | 动画以低速开始。                               |
    | ease-out    | 动画以低速结束。                               |
    | ease-in-out | 动画以低速开始和结束。                         |

-   播放次数(animation-iteration-count)

    | 值       | 描述                             |
    | :------- | :------------------------------- |
    | *n*      | 一个数字，定义应该播放多少次动画 |
    | infinite | 指定动画应该播放无限次（永远）   |

-   animation-play-state:指定动画是否正在运行或已暂停。

    | 值      | 描述               |
    | :------ | :----------------- |
    | paused  | 指定暂停动画       |
    | running | 指定正在运行的动画 |



### 4.7  transform 2D 3D转换

-   内联元素，像span等不能进行转换，要先display：inline-block，再进行转换

-   transform：
    -   translate（x，y），平移效果
    -   transformX：x轴方向，水平移动
    -   transformY：y轴方向，垂直移动
-   rotate，，旋转：
    -   transform：rotate（deg），2d旋转
    -   transformX：rotate（deg），沿x轴进行旋转，3d
    -   transformY：rotate（deg），沿y轴进行旋转，3d
-   scale，缩放：
    -   2d缩放转换，改变元素的宽度和高度
    -   transform：scale（n），一个参数时，宽度和高度都是同等的缩放比例
    -   transform：scale（w，h）
    -   transform：scaleX（w）
    -   transform：scaleY（h）

-   skew，倾斜翻转

-   旋转基点固定

    ​			ransform-origin：50% 50%，单词，固定值，百分比



### 4.8  css3中的前缀

关于css3中新增的CSs属性，针对不同的浏览器，需要加前缀。

| 值       | 意义                 |
| -------- | -------------------- |
| -moz-    | 火狐浏览器           |
| -webkit- | 使用谷歌内核的浏览器 |
| -o-      | 使用opera浏览器      |
| -ms-     | 微软IE浏览器         |

每个浏览器的内核名，如何工作，渲染原理

  



## 5  BFC

主要解决常见的浮动塌陷的问题

-   在自然的文档流，相邻两个块元素之间的margin，上下是最大值

-   行内元素左右的margin是相加的，没有上下的margin值
-   浮动块元素的左右margin是相加求和的，上下也是相加求和的
-   inline-block标签换行会变成空格键，会占一个字符嘚嘚大小，无法在一行显示，解决方案是：font-size：0



## 6  开发规范

-   css规范

    文件命名规范：home.css，about.css ，common.css（公共模块的css），base.css(重置所有样式的文件)

    选择器命名规范：id(helloWord，驼峰命名) ,class(hello-word)，给大的板块用ID，观察页面整体样式，相同的样式必须要写在公用的class，避免与他人的css冲突！所有的选择器都应该带有可区别的标志性字符来命名所有的选择器，尽量少用元素选择器

    css代码规范：1.必须格式化 2.必须要写注释

-   html规范

    首页必须叫index.html，必须放在项目的根目录下面，子页面都统一放在pages或者html文件夹中。

    在开发前，先梳理有那些文件，并且命名好文件名，再分配任务

-   文件名规范

    只能是英文或者拼音，不能有中文和空格，可以用减号来连接多个单词，或者直接写，如hello-world

-   标签规范

    html标签和标签属性只能是小写字母，标签属性之前，必须空格来分隔，标签属性的值，统一用双引号

    必须遵循W3C规范

-   图片规范

    imgs、images命名，如果图片很多，建议在下面再创建子文件夹，根据页面来命名子文件夹，放在对应的子文件夹中

    不能使用中文和空格，缩短文件名的字符量。特别是网络下载的素材，一定要重新命名。

-   字体规范

    统一使用字体库，统一一次性下载所有图标，只允许在一个项目中，使用一个字体目录（包括子目录）

-   JS规范

    文件名不能使用中文，或者带有空格字符

    变量命名要求，统一使用小驼峰命名：myHeader

    常量，构造函数，原型对象：大驼峰命名：MyHeader

    必须格式化代码，必须有注释

-   结构与表现分离

    行为与表现分离

    ![image-20201028165503891](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201028165503891.png)

![image-20201030085707437](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201030085707437.png)

mask：。

https://www.cnblogs.com/coco1s/p/13253423.html



## 7  flex布局

**布局的方法：**

- 原始文档流布局
- 浮动布局
- 定位布局
- 盒模型布局
- 弹性盒模型布局：主要是IE不支持，IE10，11部分支持



任何一个容器都可以指定为flex布局

行内元素也可以指定为flex布局

注意，设为flex布局后，子元素的float、clear和vertical-align属性将失效





