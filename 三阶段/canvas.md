# canvas

## 1  canvas简介

### 1.1  什么是canvas

是html5提供的一种新标签，画布

`<canvas></canvas>`

Carvas是一个矩形区域的画布，可以用JavaScript 在上面绘画。控制其每一个像素。

canvas标签使用JavaScript在网页上绘制图像，本身不具备绘图功能。

canwvas拥有多种绘制路径、矩影、圆影、字行以及添加图像的方法。



### 1.2  Canvas主要应用的领域

- 游戏
- 可视化数据：数据图表话，比如：百度的echart
- banner广告



### 1.3  线、三角形

设置canvas标签的宽高是通过canvas标签的属性进行设置，**不要使用css去设置，避免对画布产生影响**

**兼容性： ie9+**

如果canvas不支持，可使用flash



```js
//不加px
<canvas id="demo" width="500" height="600">

</canvas>

//第一步：拿到canvas的标签，获取canvas对象
var canvas=document.getElementById("demo")

//第二步，拿到canvas的上下文，获取画布对象，创建画布对象
//2d的画布，也就是x轴和y轴
var ctx=canvas.getContext("2d")


//第三步，绘制
ctx.beginPath()//开启路径
ctx.moveTo(100,100)//初始坐标
ctx.lineTo(200,100) //路径
ctx.lineTo(100,200) //路径

ctx.closePath() //闭合路径，关闭路径，如果是多个坐标点，可以形成一个封闭的路径
ctx.lineWidth=4 //线宽，不带单位
ctx.strokeStyle='rgb(233,233,233)' //绘制的样式颜色，所有格式都行

ctx.fillStyle='pink'//先写
ctx.fill() //填充，默认黑色，后写

ctx.stroke() //描边
```

![image-20201129163811438](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201129163811438.png)

### 1.4  ctx.rect()，矩形

| 参数     | 描述                   |
| :------- | :--------------------- |
| *x*      | 矩形左上角的 x 坐标。  |
| *y*      | 矩形左上角的 y 坐标。  |
| *width*  | 矩形的宽度，以像素计。 |
| *height* | 矩形的高度，以像素计。 |

clearRect()：清除矩形

fillRect() ：方法绘制"已填充"的矩形。默认的填充颜色是黑色。

ctx.lineCap，绘制圆形的结束线帽，当路径闭合时，直线的两头就没有圆角效果

| 值     | 描述                                   |
| :----- | :------------------------------------- |
| butt   | 默认。向线条的每个末端添加平直的边缘。 |
| round  | 向线条的每个末端添加圆形线帽。         |
| square | 向线条的每个末端添加正方形线帽。       |

ctx.lineJoin,连接的角的效果，当两条线条交汇时，创建圆形边角：

| 值    | 描述             |
| :---- | :--------------- |
| bevel | 创建斜角。       |
| round | 创建圆角。       |
| miter | 默认。创建尖角。 |

![image-20201214094211311](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201214094211311.png)



### 1.5  globalCompositeOperation 属性

使用不同的 globalCompositeOperation 值绘制矩形。红色矩形是*目标图像*，蓝色矩形是*源图像*：

| 值               | 描述                                                         |
| :--------------- | :----------------------------------------------------------- |
| source-over      | 默认。在*目标图像*上显示*源图像*。                           |
| source-atop      | 在*目标图像*顶部显示*源图像*。*源图像*位于*目标图像*之外的部分是不可见的。 |
| source-in        | 在*目标图像*中显示*源图像*。只有*目标图像*之内的*源图像*部分会显示，*目标图像*是透明的。 |
| source-out       | 在*目标图像*之外显示*源图像*。只有*目标图像*之外的*源图像*部分会显示，*目标图像*是透明的。 |
| destination-over | 在*源图像*上显示*目标图像*。                                 |
| destination-atop | 在*源图像*顶部显示*目标图像*。*目标图像*位于*源图像*之外的部分是不可见的。 |
| destination-in   | 在*源图像*中显示*目标图像*。只有*源图像*之内的*目标图像*部分会被显示，*源图像*是透明的。 |
| destination-out  | 在*源图像*之外显示*目标图像*。只有*源图像*之外的*目标图像*部分会被显示，*源图像*是透明的。 |
| lighter          | 显示*源图像* + *目标图像*。                                  |
| copy             | 显示*源图像*。忽略*目标图像*。                               |
| xor              | 使用异或操作对*源图像*与*目标图像*进行组合。                 |

![image-20201214101724287](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201214101724287.png)

蓝色是原图像，红色是目标图像



### 1.6  arc(),绘制圆/弧/扇形

| 参数               | 描述                                                         |
| :----------------- | :----------------------------------------------------------- |
| *x*                | 圆的中心的 x 坐标。                                          |
| *y*                | 圆的中心的 y 坐标。                                          |
| *r*                | 圆的半径。                                                   |
| *sAngle*           | 起始角，以弧度计（弧的圆形的三点钟位置是 0 度）。            |
| *eAngle*           | 结束角，以弧度计。                                           |
| *counterclockwise* | 可选。规定应该逆时针还是顺时针绘图。False = 顺时针，true = 逆时针。 |

`ctx.arc(300, 75, 50, 0, 2 * Math.PI);`圆，起始角度为0，结束角度为2*Math.PI

```js
ctx.beginPath();
ctx.strokeStyle = "yellow"
ctx.fillStyle="yellow" //fillstyle必须写在fill之前
ctx.arc(300, 75, 50, 0, 2 * Math.PI);
ctx.fill() //fill不能写在arc之前，会没效果
ctx.stroke();
```

arcTo()

![image-20201214112432284](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201214112432284.png)

![image-20201214144654859](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201214144654859.png)



echart

