# jQuery

## 1  jQuery概述

**jQuery是什么**

jQuery是目前太用最广泛的javascript函数库，极大地简化了JavaScript编程，通过它能“写的更少但做的更多”。可以方便地处理HTML DOM、事件处理Events、高效灵活的操作CSS、实现动画效果，并且方便地为网站提供AJAX交互。

同类型的js函数库还有YUI，Ext-js , dojo , prototype , zeptojs等

全世界排名前100万的网站，一半以上使用jQuery已成为前端js操作的一个标准微软，google，腾讯等公司均在项目中使用了jQuery，大量国内互联网公司也在他们的产品中开始使用jQuery

**为什么选择jQuery**

小巧：jQuery自身叶分，核心库只有几十kb

代码简洁：支持链式代码风格，以前需要10几行js代码才能实现的功能，jQuery只需一两行

跨平台： jQuery对各种浏览器都保持了很好的兼容性，可大幅提高前端开发测试效率

高性能：
jQuery经过了很好的优化，每次升级都有性能的提升

插件众多：
众多的jQuery插件为开发者提供了便利性

**如何学习JQuery**

jQuery最有特色的语法特点就是具有与CSS 语法相似的选择器，并且它支持CSS1到CSS3的几乎所有选择器，并兼容所有主流浏览器，这为快速访问DOM提供了方便。

一份jQuery API文档‘：jQuery 的文档非常丰富，因为其经量级的特性，文档并不复杂，文档中有每个api的用法，有完整示例代码。

掌握jQuery操作的基本语法规律：在项目中参照api文档，熟能生巧

**引用**

必须先引用jQuery.js文件，然后在使用jQuery对象来写代码





## 2  jQuery使用

![image-20201123092705511](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201123092705511.png)

`window.jquery=window.$=jquery`

```js
let div =$("ul > li:nth-child(3) > div");
//返回的是jq对象
//类似于原生的。queryseLectALL()，返回的是节点列表，数组的形式
```



### 2.1  jq选择器

#### 2.1.1  基本选择器

jq对象中包含dom节点

```js
let nav = jQuery("#nav"); //选择id
console.log(nav)//jQuery.fn.init [ultfnav]

let menuList =$(".menu-item") //选择类
console.log(menuList);

let divList = $("div"); //选择元素
console.log(divList);

let all = $("*"); //选择全部
console.log(all);
```

返回的是jq的一个实例化对象，简称jq对象



#### 2.1.2  关系选择器

```js
let div2 = $("#nav div"); //后代选择器
console.log(div2);

let div3 =$("#nav > li > div") //子元素选择器
console.log (div3);

let p1 = $( "div~p") //div后面所有是弟元素;console.log(p1);
console.log(p1);

let p2 = $( "div+p") //div相邻的后面的兄弟元紊
console.log(p2);

```

……..

​        

#### 2.1.3  属性选择器

```js
let oipt = jQuery("[name= 'username']");
console.log(oipt)
```

……



#### 2.1.4 表单选择器

:input ,匹配所有input,textarea,seLect和 button元素

:text，匹配所有input中, type = "text"”



#### 2.1.5  混合项

#### 2.1.6  正则表达式



### 2.2  jq对象与dom对象的互换

#### 2.2.1  从jq对象中获取dom节点对象

1.下标，通过[索引下标]来获取dom节点对象

2.get方法，通过jq.get(索引下标)来获取DOM节点对象:

```js
let menuList = $(".menu-item")
console.log(menuList);

let li1 = menuList[o];
console.log(li1);

let li2 = menuList.get(1)
console. log(1i2);

```



#### 2.2.2  dom变成jq对象

使用$,或者jQuery( )

```js
let oLi = $(li2);
Console.log(oLi);
```





### 2.3  jq操作

jq对象，只能使用jq对象的属性和方法

dom节点，只能使用dom对象的属性和方法

#### 2.3.1  属性

Length,表示有几个匹配的DOM节点对象;

```js
let len = ul.length;
console.log(len);
```

#### 2.3.2  过滤

`eq（索引下标）`，只返回jq对象中，指定索引号的jq对象

。。。。。

#### 2.3.3  查找

`children()`，**找子元素**，返回所有匹配项中每一个元素的所有**子元素**



`find()`，**找后代**，查找当前对象下指定的目标对象，这个函数是找出正在处理的元素的后代元素的好方法



`next()`，**找兄弟元素**，后面**一个**兄弟节点

`nextAll()` ,**找兄弟元素**，后面**所有**兄弟节点

`siblings()`,当前对象之前，之后的所有兄弟对象



`parent()`, **找父级元素**，**直接**父级对象

`parents()`,  **找父级元素**，任意一个父级与父级以上的元素

`parents("父级的名称或者选择器")`，可以直接拿到某个祖先元素





### 2.4  属性、css、文本、html操作

`attr()`,获取或设置元素属性

`prop()`,用法与作用与attr一样

```js
let img=$("img").eq(0)

//获取属性的值
let src=img.attr(src)

//设置、修改、更新
let img=$("img").eq(1)
img.attr("src","img/01.jpg")

//多个属性同时设置、更新、修改
img.attr({"src":"02.jpg","title":"111111","alt":"wwwwww"})
//:左边的属性可以加引号也可以不加

//删除一个属性
img.removeAttr("alt")
```



`html()`

day28 demo3

```

```



`text()`

```

```



`val()`,获取元素的value值

```

```



`css()`,获取最终样式表的值，而不是style对象中的值

修改时，都将设置新的css属性到style对象上，添加了style标签属性

`css(样式名称，样式值)`，设置被选元素的一个样式属性

`addClass()`

`removeClass()`

`toggleClass()`



`offset()`,获取匹配元素在当前视口的相对偏，返回一个相对于可视区的坐标对象`{top:8,left:8}`,包括top和left

`position()`,返回一个父元素的坐标对象，`{top:8,left:8}`,包括top和left



`scrollTop()`,文档或元素的内容，向上滚动的距离值

`scrollLeft()`



`height()`，当前元素的实际内容的高度

`width()`

`innerHeight()`,当前元素的实际的高度，包括padding、

`innerWidth()`

`outerHeight()`,只包含padding和补白和边框，



### 2.5  节点的操作

`append()`，剪切

`appendTo()`

`prepend()`

`prependTo()`



`event.target`

`remove()`,删除所有匹配项



`after()`,把所有匹配的对象，添加到匹配的对象**之后**

`before()`,把所有匹配的对象，添加到匹配的对象**之前**

`insertAfter()`

`insertBefore()`



`wrap()`,把所有匹配的元素，每一个用匹配的元素包裹，添加父元素

`wrapAll()`,把所有匹配的元素，只用一个li包裹起来

`wrapInner()`

`unwrap()`



`replaceWidth()`

`replaceAll()`



`empty()`，清除匹配的元素的innerHTML

`remove()`,删除匹配的对象

`detach()`,删除dom节点，但是保留了jq对象，所有绑定的事件、附加的数据等都会保留下来



`clone()`,

`clone(true)`

`clone(false)`





### 2.6  事件

day29 demo1

#### 2.6.1  ready()

`ready()`，相当于onload事件句柄，但有区别

`window.onload()`，方法是在页面所有资源加载完毕时，才会触发

`$(document).ready()`，是在页面的html机构加载完成时，就触发

简写：`$(function(){})`



#### 2.6.2  一般的事件绑定

##### 2.6.1  on

`on(events,[selector],[data],fn)`

data的初始值不能是字符串？



##### 2.6.2  off

清除指定的事件句柄

清除全部的事件句柄

```

```

`mouseenter()`



##### 2.6.3  事件委托

js动态改变内容时，新增的内容没有事件，就需要做事件委托

给父级元素或者祖先元素或者根元素绑定一个事件，委托给子元素selector，当在子元素上触发事件时，**事件冒泡**到父级元素或者祖先元素或者根元素上，再执行函数

selector：一般只是一个css选择器



##### 2.6.4  自定义事件

`trigger()`,触发自定义事件

通过第三方来触发



##### 2.6.5  one

单次事件，只能触发一次

。。。。。

mouseenter，mouseleave与mouseout，mouseover的区别

mouseenter，mouseleave不会有事件穿透的效果

mouseout，mouseover有穿透效果，即如果给父元素添加这两个事件，会在子元素上触发他们



##### 2.6.6  隐藏显示

`show(speed)`、`hide(speed)`

speed:slow、normal、fast、具体毫秒数



`slideDown()`、`slideUp()`、`slideToggle()`



`fadeIn()`、`fadeOut()`、`fadeTo()`、`fadeToggle()`

透明度

`animate()`

有些属性不起作用





left:50%

transform:translateX(-50%)



each



取消fadeIn和fadeOut的白屏





bootstrap常见

媒体查询

就是写多个@media 命令来控制设备的大小，让页面在不同的宽度范围下，显示为不同的布局效果

如果使用min-width，则应该从小的断点到大写

不同的条件

![image-20201125121123564](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201125121123564.png)

判断什么时候加载文件

![image-20201125120936627](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201125120936627.png)

一般来讲，先写一个默认大屏幕的样式，再写其他断点下的样式

可能断点判断异常，还需要在部分区间去写一个断点



布局的类选择器

container

container-fluid

container-xx

row：一行包括12列，row的外层必须是上面三个选择器容器

col-1~12：col的外层必须是row

no-gutters，取消行中每列的padding-left和padding-right留白

row弹性布局，justify-content-start/center/end/around/betwwen，自动让里面的列进行左对齐，居中无间隔，右对齐，每个列都有左右相同的外边距，两端对齐    

offset-n（1-12）在元素的左边产生留白区域，或理解为把元素向右侧推过去

 

排版

.h1~.h6

副标题：`<small>`



文本对齐

text-left

text-center

text-right



list-inline让li在一行显示



图片

img-fluid 100%

img-thumbnail 缩略图

rounded 图片加圆角



浮动

float-left

float-right

d-block 转换成块元素

mx-auto 左右margin自动



表格

table标签上加.table基本类选择器

.table-dark背景为黑色

.tbale-bordered加边框

。。。





背景色

bg-primary 蓝色

。。。



图片区，如商品列表，图片加文字说明的地方

。。



文本颜色

。。



margin，padding

m->margin

p->padding

t->top,r->right,b->bottom,l->left

mt->margin-otp

pt->padding-top

0,1,2,3,4,5->>数值越大，留白就越大

pt-2 padding-top0.5倍的留白



宽度\高度



阴影



定位



溢出



文本选择



图片替换

text-hide用图片去替换文本









































































































































































