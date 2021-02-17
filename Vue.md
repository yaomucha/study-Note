# Vue

## HelloVuejs

 vue是声明式编程，区别于jquery的命令式编程。

#### 命令式编程

 原生js做法（命令式编程）

1. 创建div元素，设置id属性
2. 定义一个变量叫message
3. 将message变量放在div元素中显示
4. 修改message数据
5. 将修改的元素替换到div

#### 声明式编程

 vue写法（声明式）

1. 创建一个div元素，设置id属性
2. 定义一个vue对象，将div挂载在vue对象上
3. 在vue对象内定义变量message，并绑定数据
4. 将message变量放在div元素上显示
5. 修改vue对象中的变量message，div元素数据自动改变



##  vue列表的展示（v-for）

 开发中常用的数组有许多数据，需要全部展示或者部分展示，在原生JS中需要使用for循环遍历依次替换div元素，在vue中，使用`v-for`可以简单遍历生成元素节点。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <title>vue列表展示</title>
</head>
<body>
  <div id="app">
      <h2>{{message}}</h2>
      <ul>
        <li v-for="(item, index) in movies" :key="index">{{item}}</li>
      </ul>
  </div>
  <script>
    const app = new Vue({
      el:"#app",//用于挂载要管理的元素
      data:{//定义数据
        message:"你好啊",
        movies:["星际穿越","海王","大话西游","复仇者联盟"]//定义一个数组
      }
    })
  </script>
</body>
</html>
```

`<li v-for="(item, index) in movies" :key="index">{{item}}</li>`item表示当前遍历的元素，index表示元素索引， 为了给 Vue 一个提示，以便它能跟踪每个节点的身份，从而重用和重新排序现有元素，你需要为每项提供一个唯一 `key` 属性。建议尽可能在使用 `v-for` 时提供 `key` attribute，除非遍历输出的 DOM 内容非常简单，或者是刻意依赖默认行为以获取性能上的提升。

因为它是 Vue 识别节点的一个通用机制，`key` 并不仅与 `v-for` 特别关联。

> 不要使用对象或数组之类的非基本类型值作为 `v-for` 的 `key`。请用字符串或数值类型的值。



## vue案例-计数器

 使用vue实现一个小计数器，点击`+`按钮，计数器+1，使用`-`按钮计数器-1。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <title>vue计数器</title>
</head>
<body>
  <div id="app">
      <h2>当前计数：{{count}}</h2>
      <!-- <button v-on:click="count--">-</button>
      <button v-on:click="count++">+</button> -->
      <button v-on:click="sub()">-</button>
      <button @click="add()">+</button>
  </div>
  <script>
    const app = new Vue({
      el:"#app",//用于挂载要管理的元素
      data:{//定义数据
        count:0
      },
      methods: {
        add:function(){
          console.log("add")
          this.count++
        },
        sub:function(){
          console.log("sub")
          this.count--
        }
      },
    })
  </script>
</body>
</html>
```

1. 定义vue对象并初始化一个变量count=0

2. 定义两个方法`add`和`sub`，用于对count++或者count--

3. 定义两个button对象，给button添加上点击事件

   在vue对象中使用methods表示方法集合，使用`v-on:click`的关键字给元素绑定监听点击事件，给按钮分别绑定上点击事件，并绑定触发事件后回调函数`add`和`sub`。也可以在回调方法中直接使用表达式。例如：`count++`和`count--`。



## **插值操作**

####  Mustache语法

 mustache是胡须的意思，因为`{{}}`像胡须，又叫大括号语法。

 在vue对象挂载的dom元素中，`{{}}`不仅可以直接写变量，还可以写简单表达式。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Mustache的语法</title>
</head>
<body>
  <div id="app">
    <h2>{{message}}</h2>
    <h2>{{message}},啧啧啧</h2>

    <!-- Mustache的语法不仅可以直接写变量，还可以写简单表达式 -->
    <h2>{{firstName + lastName}}</h2>
    <h2>{{firstName + " " + lastName}}</h2>
    <h2>{{firstName}}{{lastName}}</h2>
    <h2>{{count * 2}}</h2>
  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el:"#app",
      data:{
        message:"你好啊",
        firstName:"skt t1",
        lastName:"faker",
        count:100
      }
    })

  </script>
</body>
</html>
```



#### v-once

 v-once表示该dom元素只渲染一次，之后数据改变，不会再次渲染。

```html
  <div id="app">
    <h2>{{message}}</h2>
    <!-- 只会渲染一次，数据改变不会再次渲染 -->
    <h2 v-once>{{message}}</h2>

  </div>
```

 上述`{{message}}`的message修改后，第一个h2标签数据会自动改变，第二个h2不会。



#### v-html

 在某些时候我们不希望直接输出`<a href='http://www.baidu.com'>百度一下</a>`这样的字符串，而输出被html自己转化的超链接。此时可以使用v-html。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>v-html指令的使用</title>
</head>
<body>
  <div id="app">
    <h2>不使用v-html</h2>
    <h2>{{url}}</h2>
    <h2>使用v-html，直接插入html</h2>
    <h2 v-html="url"></h2>

  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el:"#app",
      data:{
        message:"你好啊",
        url:"<a href='http://www.baidu.com'>百度一下</a>"
      }
    })
  </script>
</body>
</html>
```



#### v-text

 v-text会覆盖dom元素中的数据，相当于js的innerHTML方法。

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>v-text指令的使用</title>
</head>
<body>
  <div id="app">
    <h2>不使用v-text</h2>
    <h2>{{message}}，啧啧啧</h2>
    <h2>使用v-text，以文本形式显示,会覆盖</h2>
    <h2 v-text="message">，啧啧啧</h2>

  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el:"#app",
      data:{
        message:"你好啊"
      }
    })
  </script>
</body>
</html>
```

 如图所示，使用`{{message}}`是拼接变量和字符串，而是用v-text是直接覆盖字符串内容。

![image-20210124224520743](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20210124224520743.png)



#### v-pre

 有时候我们期望直接输出`{{message}}`这样的字符串，而不是被`{{}}`语法转化的message的变量值，此时我们可以使用`v-pre`标签。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>v-pre指令的使用</title>
</head>
<body>
  <div id="app">
    <h2>不使用v-pre</h2>
    <h2>{{message}}</h2>
    <h2>使用v-pre,不会解析</h2>
    <h2 v-pre>{{message}}</h2>

  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el:"#app",
      data:{
        message:"你好啊"
      }
    })
  </script>
</body>
</html>
```



#### v-cloak

有时候因为加载延时问题，例如卡掉了，数据没有及时刷新，就造成了页面显示从`{{message}}`到message变量“你好啊”的变化，这样闪动的变化，会造成用户体验不好。此时需要使用到`v-cloak`的这个标签。在vue解析之前，div属性中有`v-cloak`这个标签，在vue解析完成之后，v-cloak标签被移除。简单，类似div开始有一个css属性`display:none;`，加载完成之后，css属性变成`display:block`，元素显示出来。

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>v-cloak指令的使用</title>
  <style>
    [v-cloak]{
      display: none;
    }
  </style>
</head>

<body>
  <div id="app" v-cloak>
    <h2>{{message}}</h2>
  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <script>
    //在vue解析前，div中有一个属性cloak
    //在vue解析之后，div中没有一个属性v-cloak
    setTimeout(() => {
      const app = new Vue({
        el: "#app",
        data: {
          message: "你好啊"
        }
      })
    }, 1000);
  </script>
</body>

</html>
```

 这里通过延时1秒模拟加载卡住的状态，结果一开始不显示message的值，div元素中有v-cloak的属性，1秒后显示message变量的值，div中的v-cloak元素被移除。



## **动态绑定属性**

#### v-bind的基本使用

 某些时候我们并不想将变量放在标签内容中，像这样`<h2>{{message}}</h2>`是将变量h2标签括起来，类似js的innerHTML。但是我们期望将变量`imgURL`写在如下位置，想这样`<img src="imgURL" alt="">`导入图片是希望动态获取图片的链接，此时的imgURL并非变量而是字符串imgURL，如果要将其生效为变量，需要使用到一个标签`v-bind:`，像这样`<img v-bind:src="imgURL" alt="">`，而且这里也不能使用Mustache语法，类似`<img v-bind:src="{{imgURL}}" alt="">`，这也是错误的。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>v-bind的基本使用</title>
</head>
<body>
  <div id="app">
    <!-- 错误的做法这里不能使用Mustache语法 -->
    <!-- <img v-bind:src="{{imgURL}}" alt=""> -->
    <!-- 正确的做法使用v-bind指令 -->
    <img v-bind:src="imgURL" alt="">
    <a v-bind:href="aHerf"></a>
    <!-- 语法糖写法 -->
    <img :src="imgURL" alt="">
    <a :href="aHerf"></a>

  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el:"#app",
      data:{
        message:"你好啊",
        imgURL:"https://cn.bing.com/th?id=OIP.NaSKiHPRcquisK2EehUI3gHaE8&pid=Api&rs=1",
        aHerf:"http://www.baidu.com"
      }
    })
  </script>
</body>
</html>
```

 此时vue对象中定义的`imgURL`变量和`aHerf`变量可以动态的绑定到img标签的src属性和a标签的href属性。`v-bind:`由于用的很多，vue对他有一个语法糖的优化写法也就是`:`，此时修改imgURL变量图片会重新加载。



#### v-bind动态绑定class

#####  v-bind动态绑定class(对象语法)

 有时候我们期望对Dom元素的节点的class进行动态绑定，选择此Dom是否有指定class属性。例如，给h2标签加上`class="active"`，当Dom元素有此class时候，变红`<style>.active{color:red;}</style>`，在写一个按钮绑定事件，点击变黑色，再次点击变红色。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>v-bind动态绑定class(对象语法)</title>
  <style>
    .active{
      color:red;
    }
  </style>
</head>
<body>
  <div id="app">
    <!-- <h2 class="active">{{message}}</h2>
    <h2 :class="active">{{message}}</h2> -->

    <!-- 动态绑定class对象用法  -->
    <!-- <h2 :class="{key1:value1,key2:value2}">{{message}}</h2>
    <h2 :class="{类名1:true,类名2:boolean}">{{message}}</h2> -->
    <h2 class="title" :class="{active:isActive}">{{message}}</h2>
    <h2 class="title" :class="getClasses()">{{message}}</h2>
    <button @click="change">点击变色</button>

  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el:"#app",
      data:{
        message:"你好啊",
        active:"active",
        isActive:true
      },
      methods: {
        change(){
          this.isActive = !this.isActive
        },
        getClasses(){
          return {active:this.isActive}
        }
      },
    })
  </script>
</body>
</html>
```

 定义两个变量`active`和`isActive`，在Dom元素中使用`:class={active:isActive}`，此时绑定的`class='active'`，isActive为true，active显示，定义方法change()绑定在按钮上，点击按钮`this.isActive = !this.isActive`，控制Dom元素是否有`class='active'`的属性。

##### v-bind动态绑定class(数组用法)

 class属性中可以放数组，会依次解析成对应的class。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>v-bind动态绑定class(数组用法)</title>
  <style>
  </style>
</head>
<body>
  <div id="app">
    <!-- 加上单引号当成字符串 -->
    <h2 class="title" :class="['active','line']">{{message}}</h2>
    <!-- 不加会被当成变量 -->
    <h2 class="title" :class="[active,line]">{{message}}</h2>
    <h2 class="title" :class="getClasses()">{{message}}</h2>

  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el:"#app",
      data:{
        message:"你好啊",
        active:"aaaa",
        line:'bbbb'
      },
      methods: {

        getClasses(){
          return [this.active,this.line]
        }
      },
    })
  </script>
</body>
</html>
```

1.  加上单引号的表示字符串
2.  不加的会当成变量
3.  可以直接使用方法返回数组对象

####  

#### v-for和v-bind结合

 使用v-for和v-bind实现一个小demo，将电影列表展示，并点击某一个电影列表时候，将此电影列表变成红色。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>作业(v-for和v-bind的结合)</title>
  <style>
    .active{
      color:red;
    }
  </style>
</head>
<body>
  <div id="app">

    <ul>
      <li v-for="(item, index) in movies" :key="index" :class="{active:index===currentIndex}" @click="changeColor(index)" >{{index+"---"+item}}</li>
    </ul>

  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el:"#app",
      data:{
        currentIndex:0,
        movies:["海王","海贼王","火影忍者","复仇者联盟"]
      },
      methods: {
        changeColor(index){
          this.currentIndex = index
        }
      },
    })
  </script>
</body>
</html>
```

 v-for时候的index索引，给每行绑定事件点击事件，点击当行是获取此行索引index并赋值给`currentIndex`，使用`v-bind:`绑定class，当`index===currentIndex`Dom元素有active的class，颜色变红。



#### v-bind动态绑定style

#####  v-bind动态绑定style(对象语法)

```html
<!-- <h2 :style="{key(属性名):value(属性值)}">{{message}}</h2> -->
<!-- 加单引号，当成字符串解析 -->
<h2 :style="{fontSize:'50px'}">{{message}}</h2>
<!-- 不加单引号，变量解析 -->
<h2 :style="{fontSize:fontSize}">{{message}}</h2>
<h2 :style="getStyle()">{{message}}</h2>
```

##### v-bind动态绑定style(数组语法)

```html
  <div id="app">
    <h2 :style="[baseStyle]">{{message}}</h2>
    <h2 :style="getStyle()">{{message}}</h2>
  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el:"#app",
      data:{
        message:"你好啊",
        baseStyle:{backgroundColor:'red'}
      },
      methods: {
        getStyle(){
          return [this.baseStyle]
        }
      },
    })
  </script>
```

 类似绑定class，绑定style也是一样的。





## **计算属性与侦听器**

#### 计算属性的基本使用

 现在有变量姓氏和名字，要得到完整的名字。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>计算属性的基本使用</title>
</head>
<body>
  <div id="app">
    <!-- Mastache语法 -->
    <h2>{{firstName+ " " + lastName}}</h2>
    <!-- 方法 -->
    <h2>{{getFullName()}}</h2>
    <!-- 计算属性 -->
    <h2>{{fullName}}</h2>
  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el:"#app",
      data:{
        firstName:"skt t1",
        lastName:"faker"
      },
      computed: {
        fullName:function(){
          return this.firstName + " " + this.lastName
        }
      },
      methods: {
        getFullName(){
          return this.firstName + " " + this.lastName
        }
      },
    })
  </script>
</body>
</html>
```

1. 使用Mastache语法拼接`<h2>{{firstName+ " " + lastName}}</h2>`
2. 使用方法methods`<h2>{{getFullName()}}</h2>`
3. 使用计算属性computed`<h2>{{fullName}}</h2>`

> 例子中计算属性computed看起来和方法似乎一样，只是方法调用需要使用()，而计算属性不用，方法取名字一般是动词见名知义，而计算属性是属性是名词，但这只是基本使用。





####  计算属性的复杂使用

 现在有一个数组数据books，里面包含许多book对象，数据结构如下：

```js
books:[
          {id:110,name:"JavaScript从入门到入土",price:119}, 
          {id:111,name:"Java从入门到放弃",price:80},
          {id:112,name:"编码艺术",price:99},
          {id:113,name:"代码大全",price:150},
        ]
```

 要求计算出所有book的总价格`totalPrice`。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>计算属性的复杂使用</title>
</head>
<body>
  <div id="app">


    <h2>总价格：{{totalPrice}}</h2>

  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el:"#app",
      data:{
        books:[
          {id:110,name:"JavaScript从入门到入土",price:119},
          {id:111,name:"Java从入门到放弃",price:80},
          {id:112,name:"编码艺术",price:99},
          {id:113,name:"代码大全",price:150},
        ]
      },
      computed: {
        totalPrice(){
          let result= 0;
          for (let i = 0; i < this.books.length; i++) {
            result += this.books[i].price;
          }
          return result
        }
      }
    })
  </script>
</body>
</html>
```

 获取每一个book对象的price累加，当其中一个book的价格发生改变时候，总价会随之变化。





#### 计算属性的setter和getter

 在计算属性中其实是由这样两个方法setter和getter。

```js
      computed: {
        fullName:{
          //计算属性一般没有set方法，只读属性
          set:function(newValue){
            console.log("-----")
            const names = newValue.split(" ")
            this.firstName = names[0]
            this.lastName = names[1]
          },
          get:function(){
            return this.firstName + " " + this.lastName
          }
        }
      }
```

 但是计算属性一般没有set方法，只读属性，只有get方法，但是上述中newValue就是新的值，也可以使用set方法设置值，但是一般不用。

***computed的getter/setter***

> 请看如下代码：

```html
<!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>Vue计算属性的getter和setter</title>
        <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
    </head>
    <body>
        <div id="app">
            <h1>计算属性：computed的getter/setter</h1>
            <h2>fullName</h2>
            {{fullName}}
            <h2>firstName</h2>
            {{firstName}}
            <h2>lastName</h2>
            {{lastName}}
        </div>
        <script>
            var app = new Vue({
                el:"#app",
                data:{
                firstName:"zhang",
                lastName:"san",
                },
                computed: {
                    fullName:{
                        get:function(){
                            return this.firstName+" "+this.lastName
                        },
                        set:function(value){
                            var list = value.split(' ');
                            this.firstName=list[0]
                            this.lastName=list[1]
                        }
                    }
                },
            });
        </script>
    </body>
    </html>
```

> *初始化*

> 修改fullName

> *结论*

\- 通过这种方式，我们可以在改变计算属性值的同时也改变和计算属性相关联的属性值。





#### 计算属性和methods的对比

 直接看代码，分别使用计算属性和方法获得fullName的值。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>计算属性和methods的对比</title>
</head>
<body>
  <div id="app">
    <!-- methods，即使firstName和lastName没有改变，也需要再次执行 -->
    <h2>{{getFullName()}}</h2>
    <h2>{{getFullName()}}</h2>
    <h2>{{getFullName()}}</h2>
    <h2>{{getFullName()}}</h2>
    <!-- 计算属性有缓存，只有关联属性改变才会再次计算 -->
    <h2>{{fullName}}</h2>
    <h2>{{fullName}}</h2>
    <h2>{{fullName}}</h2>
    <h2>{{fullName}}</h2>


  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el:"#app",
      data:{
        firstName:"skt t1",
        lastName:"faker"
      },
      computed: {
        fullName(){
          console.log("调用了计算属性fullName");

          return this.firstName + " " + this.lastName
        }
      },
      methods: {
        getFullName(){
          console.log("调用了getFullName");

          return this.firstName + " " + this.lastName
        }
      },
    })
  </script>
</body>
</html>
```

 分别使用方法和计算属性获取四次fullName，结果如图。

![image-20210124230438024](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20210124230438024.png)

 由此可见计算属性有缓存，在`this.firstName + " " + this.lastName`的属性不变的情况下，methods调用了四次，而计算属性才调用了一次，性能上计算属性明显比methods好。而且在改动firstName的情况下，计算属性只调用一次，methods依然要调用4次。



#### computed和watch的区别

**计算属性computed :** 

1. 支持缓存，只有依赖数据发生改变，才会重新进行计算

2. 不支持异步，当computed内有异步操作时无效，无法监听数据的变化

3. computed 属性值会默认走缓存，计算属性是基于它们的响应式依赖进行缓存的，也就是基于data中声明过或者父组件传递的props中的数据通过计算得到的值

4. 如果一个属性是由其他属性计算而来的，这个属性依赖其他属性，是一个多对一或者一对一，一般用computed

5. 如果computed属性属性值是函数，那么默认会走get方法；函数的返回值就是属性的属性值；在computed中的，属性都有一个get和一个set方法，当数据变化时，调用set方法。



**侦听属性watch：**

1. 不支持缓存，数据变，直接会触发相应的操作；

2. watch支持异步；

3. 监听的函数接收两个参数，第一个参数是最新的值；第二个参数是输入之前的值；

4. 当一个属性发生变化时，需要执行对应的操作；一对多；

5. 监听数据必须是data中声明过或者父组件传递过来的props中的数据，当数据变化时，触发其他操作，函数有两个参数，

　　immediate：组件加载立即触发回调函数执行，

　　deep: 深度监听，为了发现**对象内部值**的变化，复杂类型的数据时使用，例如数组中的对象内容的改变，注意监听数组的变动不需要这么做。注意：deep无法监听到数组的变动和对象的新增，参考vue数组变异,只有以响应式的方式触发才会被监听到。



#### Vue计算属性与侦听器总结

> **照例看一段代码：**

```html
<!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>Vue计算属性/侦听器/方法比较</title>
        <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
    </head>
    <body>
        <div id="app">
            <h1>计算属性：computed</h1>
            {{fullName}}
            <h1>方法：methods</h1>
            {{fullName2()}}
            <h1>侦听器：watch</h1>
            {{watchFullName}}
            <h1>年龄</h1>
            {{age}}
        </div>
        <script>
            var other = 'This is other';
            var app = new Vue({
                el:"#app",
                data:{
                firstName:"zhang",
                lastName:"san",
                watchFullName:"zhangsan",
                age:18,
                },
                watch: {
                    firstName:function(newFirstName, oldFirstName){
                        console.log("firstName触发了watch,newFirstName="+newFirstName+",oldFirstName="+oldFirstName)
                        this.watchFullName = this.firstName+this.lastName+","+other
                    },
                    lastName:function(newLastName, oldLastName){
                        console.log("lastName触发了watch,newLastName="+newLastName+",oldLastName="+oldLastName)
                        this.watchFullName = this.firstName+this.lastName+","+other
                    }  
                },
                computed: {
                    fullName:function(){
                    console.log("调用了fullName,计算了一次属性")
                    return this.firstName+this.lastName+","+other;
                    }
                },
                methods: {
                    fullName2:function(){
                        console.log("调用了fullName,执行了一次方法")
                        fullName2 = this.firstName+this.lastName+","+other;
                        return fullName2;
                    }
                }
            });
        </script>
    </body>
    </html>
```



> 测试结论：

1. 使用computed计算了fullName属性，值为firstName+lastName。计算属性具有`缓存功能`，当firstName和lastName都不改变的时候，fullName不会重新计算，比如我们改变age的值，fullName的值是不需要重新计算的。
2. methods并没有缓存特性，比如我们改变age的值，fullName2()方法会被执行一遍。
3. 当一个功能可以用上面三个方法来实现的时候，明显使用computed更合适，代码简单也有缓存特性。
4. 计算属性范围在vue实例内，修改vue实例外部对象，不会重新计算渲染，但是如果先修改了vue实例外对象，在修改vue计算属性的对象，那么外部对象的值也会重新渲染。

> *计算属性：computed*

计算属性范围在Vue实例的fullName内所管理的firstName和lastName,通常监听多个变量

> *侦听器：watch*

监听数据变化，一般只监听一个变量或数组

> 使用场景

watch(`异步场景`)，computed(`数据联动`)









## **事件监听**

#### v-on的基本使用

 在前面的计数器案例中使用了`v-on:click`监听单击事件。这里在回顾一下：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <title>Document</title>
</head>
<body>
  <div id="app">
      <h2>{{count}}</h2>
      <!-- <button v-on:click="count++">加</button>
      <button v-on:click="count--">减</button> -->
      <button @click="increment">加</button>
      <button @click="decrement()">减</button>
  </div>
  <script>
    const app = new Vue({
      el:"#app",
      data:{
        count:0
      },
      methods: {
        increment(){
          this.count++
        },
        decrement(){
          this.count--
        }
      }
    })

  </script>
</body>
</html>
```

 使用`v-on:click`给button绑定监听事件以及回调函数，@是`v-on:`的语法糖，也就是简写也可以使用`@click`。方法一般是需要写方法名加上()，在`@click`中可以省掉，如上述的`<button @click="increment">加</button>`。



####  v-on的参数传递

 了解了v-on的基本使用，现在需要了解参数传递。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>
<body>
  <div id="app">
    <!-- 事件没传参 -->
    <button @click="btnClick">按钮1</button>
    <button @click="btnClick()">按钮2</button>
    <!-- 事件调用方法传参，写函数时候省略小括号，但是函数本身需要传递一个参数 -->
    <button @click="btnClick2(123)">按钮3</button>
    <button @click="btnClick2()">按钮4</button>
    <button @click="btnClick2">按钮5</button>
    <!-- 事件调用时候需要传入event还需要传入其他参数 -->
    <button @click="btnClick3($event,123)">按钮6</button>
  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el:"#app",
      methods:{
        btnClick(){
          console.log("点击XXX");
        },
        btnClick2(value){
          console.log(value+"----------");
        },
        btnClick3(event,value){
          console.log(event+"----------"+value);
        }
      }
    })
  </script>
</body>
</html>	
```

1. 事件没传参，可以省略()
2. 事件调用方法传参了，写函数时候省略了小括号，但是函数本身是需要传递一个参数的，这个参数就是原生事件event参数传递进去
3. 如果同时需要传入某个参数，同时需要event是，可以通过`$event`传入事件。

按钮4调用`btnClick2(value){}`，此时`undefined`。按钮5调用时省略了()，会自动传入原生event事件，如果我们需要event对象还需要传入其他参数，可以使用`$event`对象。

![image-20210124231149142](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20210124231149142.png)





#### v-on的修饰词

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>v-on的修饰符</title>
</head>
<body>
  <div id="app">
    <!--1. .stop的使用，btn的click事件不会传播，不会冒泡到上层，调用event.stopPropagation() -->
    <div @click="divClick">
        <button @click.stop="btnClick">按钮1</button>
    </div>
    <!-- 2. .prevent 调用event.preeventDefault阻止默认行为  -->
    <form action="www.baidu.com">
      <button type="submit" @click.prevent="submitClick">提交</button>
    </form>
    <!--3. 监听键盘的事件 -->
    <input type="text" @click.enter="keyup">

  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el:"#app",
      methods:{
        btnClick(){
          console.log("点击button");
        },
        divClick(){
          console.log("点击div");
        },
        submitClcik(){
          console.log("提交被阻止了")
        },
        keyup(){
          console.log("keyup点击")
        }
      }
    })
  </script>
</body>
</html>
```

1. `.stop`的使用，btn的click事件不会传播，不会冒泡到上层，调用`event.stopPropagation()`。
2. `.prevent` 调用`event.preeventDefault`阻止默认行为。
3. `.enter`监听键盘事件



## **条件判断**

#### v-if、v-else、v-elseif

v-if用于条件判断，判断Dom元素是否显示。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>
<body>
  <div id="app">
    <h2 v-if="isFlag">isFlag为true显示这个</h2>
    <h2 v-show="isShow">isShow为true是显示这个</h2>
    <div v-if="age<18">小于18岁未成年</div>
    <div v-else-if="age<60">大于18岁小于60岁正值壮年</div>
    <div v-else="">大于60岁,暮年</div>
  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el:"#app",
      data:{
        isFlag:true,
        isShow:false,
        age:66
      }
    })
  </script>
</body>
</html>
```

1. 单独使用v-if，变量为布尔值，为true才渲染Dom
2. v-show的变量也是布尔值，为true才显示内容，类似css的display
3. v-if、v-else、v-else-if联合使用相当于if、elseif、else，但是在条件比较多的时候建议使用计算属性。



#### vue中v-if与v-show的区别

##### 区别

- 1.手段：v-if是通过控制dom节点的存在与否来控制元素的显隐；v-show是通过设置DOM元素的display样式，block为显示，none为隐藏；

- 2.编译过程：v-if切换有一个局部编译/卸载的过程，切换过程中合适地销毁和重建内部的事件监听和子组件；v-show只是简单的基于css切换；

- 3.编译条件：v-if是惰性的，如果初始条件为假，则什么也不做；只有在条件第一次变为真时才开始局部编译（编译被缓存？编译被缓存后，然后再切换的时候进行局部卸载); v-show是在任何条件下（首次条件是否为真）都被编译，然后被缓存，而且DOM元素保留；

- 4.性能消耗：v-if有更高的切换消耗；v-show有更高的初始渲染消耗；

  

#### v-if的demo

 在登录网站是经常可以选择使用账户名或者邮箱登录的切换按钮。要求点击按钮切换登录方式。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>
<body>
  <div id="app">
    <span v-if="isUser">
      <label for="username">用户账号</label>
      <input type="text" id="username" placeholder="请输入用户名" >
    </span>
    <span v-else="isUser">
        <label for="email">用户邮箱</label>
        <input type="text" id="email" placeholder="请输入用户邮箱" >
    </span>
    <button @click="isUser=!isUser">切换类型</button>
  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el:"#app",
      data:{
        isUser:true
      }
    })
  </script>
</body>
</html>
```

 使用`v-if`和`v-else`选择渲染指定的Dom，点击按钮对`isUser`变量取反。

> 这里有个小问题，如果已经输入了账号了，此时想切换到邮箱输入，输入框未自己清空。

 这里需要了解一下vue底层操作，此时input输入框值被复用了。

1. vue在进行DOM渲染是，处于性能考虑，会复用已经存在的元素，而不是每次都创建新的DOM元素。

2. 在上面demo中，Vue内部发现原来的input元素不再使用，所以直接将其映射对应虚拟DOM，用来复用。

3. 如果不希望出现类似复用问题，可以给对应的dom元素加上`key`值，并保证`key`不同。

   ```html
   <input type="text" id="username" placeholder="请输入用户名" key="username">
   <input type="text" id="email" placeholder="请输入用户邮箱" key="email">
   ```



#### v-show

 v-if 在首次渲染的时候，如果条件为假，什么也不操作，页面当作没有这些元素。当条件为真的时候，开始局部编译，动态的向DOM元素里面添加元素。当条件从真变为假的时候，开始局部编译，卸载这些元素，也就是删除。

 v-show 不管条件是真还是假，第一次渲染的时候都会编译出来，也就是标签都会添加到DOM中。之后切换的时候，通过display: none;样式来显示隐藏元素。可以说只是改变css的样式，几乎不会影响什么性能。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>
<body>
  <div id="app">
    <h2 v-show="isFlag">v-show只是操作元素的style属性display</h2>
    <h2 v-if="isFlag">v-if是新增和删除dom元素</h2>
  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el:"#app",
      data:{
        isFlag:true
      }
    })
  </script>
</body>
</html>
```





## **循环遍历**

##### v-for遍历数组

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>
<body>
  <div id="app">
    <!-- 1.遍历过程没有使用索引（下标值） -->
    <ul>
      <li v-for="item in names" >{{item}}</li>
    </ul>
    <!-- 2.遍历过程有使用索引（下标值） -->
    <ul>
        <li v-for="(item,index) in names"  >{{index+":"+item}}</li>
    </ul>
  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el:"#app",
      data:{
        names:["zzz","ttt","yyy"]
      }
    })
  </script>
</body>
</html>
```

 一般需要使用索引值。`<li v-for="(item,index) in names" >{{index+":"+item}}</li>`index表示索引，item表示当前遍历的元素。



##### v-for遍历对象

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>
<body>
  <div id="app">
    <!-- 1.遍历过程没有使用index索引-->
    <!-- 格式为：(value, name) -->
    <ul>
      <li v-for="(item,key) in user" >{{key+"-"+item}}</li>
    </ul>
    <!-- 格式为：(value, name, index) -->
    <ul>
      <li v-for="(item,key,index) in user" >{{key+"-"+item+"-"+index}}</li>
    </ul>

  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el:"#app",
      data:{
        user:{
          name:"zzz",
          height:188,
          age:24
        }
      }
    })
  </script>
</body>
</html>
```

1. 遍历过程没有使用index索引，`<li v-for="(item,key) in user" >{{key+"-"+item}}</li>`，item表示当前元素是属性值，key表示user对象属性名。
2. 遍历过程使用index索引，index表示索引从0开始。



##### v-for使用key

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>v-for使用key</title>
</head>
<body>
  <div id="app">
    <!-- 不加key如果要插入f依次改变 -->
    <ul>
      <li v-for="item in letters">{{item}}</li>
    </ul>
    <button @click="add1">没有key</button>
    <!-- 加key如果要插入f使用diff算法高效,如果使用index做key一直变，所以item如果唯一可以使用item-->
    <ul>
        <li v-for="item in letters" :key="item">{{item}}</li>
    </ul>
    <button @click="add2">有key</button>
  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el:"#app",
      data:{
        letters:['a','b','c','d','e']
      },
      methods: {
        add1(){
          this.letters.splice(2,0,'f')
        },
        add2(){
          this.letters.splice(2,0,'f')
        }
      }
    })
  </script>
</body>
</html>
```

1. 使用key可以提高效率，加key如果要插入f使用diff算法高效,如果使用index做key一直变，所以item如果唯一可以使用item。
2. 不加key如果要插入f依次替换。
3.  不加key渲染时候会依次替换渲染，加了key会直接将其放在指定位置，加key提升效率。



##### 数组的响应方式

 我们改变DOM绑定的数据时，DOM会动态的改变值。数组也是一样的。但是对于动态变化数据，有要求，不是任何情况改变数据都会变化。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>数组的响应式方法 </title>
</head>
<body>
  <div id="app">
    <!-- 数组的响应式方法 -->
    <ul>
      <li v-for="item in letters">{{item}}</li>
    </ul>
    <button @click="btn1">push</button><br>
    <button @click="btn2">通过索引值修改数组</button>
  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el:"#app",
      data:{
        letters:['a','b','c','d','e']
      },
      methods: {
        btn1(){
          //1.push
          this.letters.push('f')
          //2.pop()删除最后一个元素
          //this.letters.pop()
          //3.shift()删除第一个
          //this.letters.shift()
          //4.unshift()添加在最前面,可以添加多个
          //this.letters.unshift('aaa','bbb','ccc')
          //5.splice():删除元素/插入元素/替换元素
          //splice(1,1)在索引为1的地方删除一个元素,第二个元素不传，直接删除后面所有元素
          //splice(index,0,'aaa')再索引index后面删除0个元素，加上'aaa',
          //splice(1,1,'aaa')替换索引为1的后一个元素为'aaa'
          // this.letters.splice(2,0,'aaa')
          //6.sort()排序可以传入一个函数
          //this.letters.sort()
          //7.reverse()反转
          // this.letters.reverse()

        },
        btn2(){
          this.letters[0]='f'
        }
      }
    })
  </script>
</body>
</html>
```

1. btn2按钮是通过索引值修改数组的值，这种情况，数组letters变化，DOM不会变化。

2. 而数组的方法，例如`push()`、`pop()`、`shift()`、`unshift()`、`splice()`、`sort()`、`reverse()`等方法修改数组的数据，DOM元素会随之修改。

3. > push()：在最后添加元素
   >
   > pop()：删除最后一个元素
   >
   > shift()：删除第一个元素
   >
   > unshift()：添加在最前面，可以添加多个
   >
   > splic()：删除元素、插入元素、替换元素
   >
   > splice(1,1)再索引为1的地方删除一个元素,第二个元素不传，直接删除后面所有元素
   >
   > splice(index,0,'aaa')再索引index后面删除0个元素，加上'aaa'
   >
   > splice(1,1,'aaa')替换索引为1的后一个元素为'aaa'



##### 综合练习

 现在要求将数组内的电影展示到页面上，并选中某个电影，电影背景变红，为选中状态。

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>综合练习</title>
  <style>
    .active {
      background-color: red;
    }
  </style>
</head>

<body>
  <div id="app">
    <!-- 数组的响应式方法 -->
    <ul>
      <li v-for="(item,index) in movies"  @click="liClick(index)" :class="{active:index===curIndex}">{{index+"---"+item}}</li>
    </ul>
  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el: "#app",
      data: {
        movies: ['复仇者联盟', '蝙蝠侠', '海贼王', '星际穿越'],
        curIndex:0
      },
      methods: {
        liClick(index){
          this.curIndex = index
        }
      }
    })
  </script>
</body>

</html>
```

1. 先使用`v-for`将电影列表展示到页面上，并获取index索引定位当前的`<li>`标签。
2. 给每个`<li>`标签加上,单击事件，并将index传入单击事件的回调函数methods的`liClick()`。
3. 定义一个变量`curIndex`表示当前索引，初始值为0，用于表示选中状态的电影列。
4. 定义个class样式active，在active为激活状态是，` background-color: red;`为红色。使用表达式`index=curIndex`判断当前选中状态的列。



## **v-model**

#### v-model的基本使用

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Title</title>
</head>
<body>
<div id="app">
  <input type="text" v-model="message">{{message}}
</div>
<script src="../js/vue.js"></script>
<script>
  const app = new Vue({
    el: '#app',
    data: {
      message: "hello"
    }
  })
</script>
</body>
</html>
```

 v-model双向绑定，既输入框的value改变，对应的message对象值也会改变，修改message的值，input的value也会随之改变。无论改变那个值，另外一个值都会变化。



#### v-model的原理

 先来一个demo实现不使用v-model实现双向绑定。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Title</title>
</head>
<body>
<div id="app">
  <!-- $event获取事件对象，$event.target.value获取input值 -->
<!--  <input type="text" :value="message" @input="changeValue($event.target.value)">{{message}}-->
  <!--事件调用方法传参了，写函数时候省略了小括号，但是函数本身是需要传递一个参数的，这个参数就是原生事件event参数传递进去-->
  <input type="text" :value="message" @input="changeValue">{{message}}
</div>
<script src="../js/vue.js"></script>
<script>
  const app = new Vue({
    el: '#app',
    data: {
      message: "hello world"
    },
    methods: {
      changeValue(event){
        console.log("值改变了");
        this.message = event.target.value
      }
    }
  })
</script>
</body>
</html>
```

 `v-model = v-bind + v-on`，实现双向绑定需要是用v-bind和v-on，使用v-bind给input的value绑定message对象，此时message对象改变，input的值也会改变。但是改变input的value并不会改变message的值，此时需要一个v-on绑定一个方法，监听事件，当input的值改变的时候，将最新的值赋值给message对象。`$event`获取事件对象，target获取监听的对象dom，value获取最新的值。



####  v-model结合radio类型使用

 radio单选框的`name`属性是互斥的，如果使用v-model，可以不使用`name`就可以互斥。

```html
  <div id="app">
    <!-- name属性radio互斥 使用v-model可以不用name就可以互斥 -->
    <label for="male">
      <input type="radio" id="male" name="sex" value="男" v-model="sex">男
    </label>
    <label for="female">
        <input type="radio" id="female" name="sex" value="女" v-model="sex">女
    </label>
    <div>你选择的性别是：{{sex}}</div>

  </div>
  <script src="../js/vue.js"></script>
  <script>
    const app = new Vue({
      el:"#app",
      data:{
        message:"zzz",
        sex:"男"
      },

    })
  </script>
```

v-model绑定`sex`属性，初始值为“男”，选择女后`sex`属性变成“女”，因为此时是双向绑定。



####  v-model结合checkbox类型使用

 checkbox可以结合v-model做单选框，也可以多选框。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Title</title>
</head>
<body>
<div id="app">
  <!--单选框-->
  <h2>单选框</h2>
  <label for="agree">
    <input type="checkbox" id="agree" v-model="isAgree">同意协议
  </label>
  <!--多选框-->
  <h2>多选框</h2>
  <label :for="item" v-for="(item,index) in hobbies" :key="index">
    <input type="checkbox" name="hobby" :value="item" :id="item" v-model="hobbies">{{item}}
  </label>
  <h2>你的爱好是：{{hobbies}}</h2>
</div>
<script src="../js/vue.js"></script>
<script>
  const app = new Vue({
    el: '#app',
    data: {
      isAgree: false,
      hobbies: ["篮球","足球","乒乓球","羽毛球"]
    }
  })
</script>
</body>
</html>
```

1. checkbox结合v-model实现单选框，定义变量`isAgree`初始化为`false`，点击checkbox的值为`true`，`isAgree`也是`true`。
2. checkbox结合v-model实现多选框，定义数组对象`hobbies`，用于存放爱好，将`hobbies`与checkbox对象双向绑定，此时选中，一个多选框，就多一个true，`hobbies`就添加一个对象。

![image-20210124233103703](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20210124233103703.png)



#### v-model结合select

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>v-model结合select类型</title>
</head>
<body>
  <div id="app">
    <!-- select单选 -->
    <select name="fruit" v-model="fruit">
      <option value="苹果">苹果</option>
      <option value="香蕉">香蕉</option>
      <option value="西瓜">西瓜</option>
    </select>
    <h2>你选择的水果是：{{fruit}}</h2>

    <!-- select多选 -->
    <select name="fruits" v-model="fruits" multiple>
      <option value="苹果">苹果</option>
      <option value="香蕉">香蕉</option>
      <option value="西瓜">西瓜</option>
    </select>
    <h2>你选择的水果是：{{fruits}}</h2>
  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el:"#app",
      data:{
        fruit:"苹果",
        fruits:[]
      },

    })
  </script>
</body>
```

 v-model结合select可以单选也可以多选。

![image-20210124233653624](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20210124233653624.png)



#### v-model的修饰符的使用

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>v-model修饰符</title>
</head>
<body>
  <div id="app">
    <h2>v-model修饰符</h2>
    <h3>lazy,默认情况是实时更新数据，加上lazy，从输入框失去焦点，按下enter都会更新数据</h3>
    <input type="text" v-model.lazy="message">
    <div>{{message}}</div>
    <h3>修饰符number,默认是string类型，使用number赋值为number类型</h3>
    <input type="number" v-model.number="age">
    <div>{{age}}--{{typeof age}}</div>
    <h3>修饰符trim:去空格</h3>
    <input type="text" v-model.trim="name">

  </div>
  <script src="../js/vue.js"></script>
  <script>
    const app = new Vue({
      el:"#app",
      data:{
        message:"zzz",
        age:18,
        name:"ttt"
      },

    })
  </script>
</body>
</html>
```

1. `lazy`：默认情况下是实时更新数据，加上`lazy`，从输入框失去焦点，按下enter都会更新数据。
2. `number`：默认是string类型，使用`number`复制为number类型。
3. `trim`：用于自动过滤用户输入的首尾空白字符







## vue-router中的hash模式和history模式的关系

#### hash模式和history模式的不同

最直观的区别就是在url中 hash 带了一个很丑的 # 而history是没有#的

对于vue这类渐进式前端开发框架，为了构建 SPA（单页面应用），需要引入前端路由系统，这也就是 Vue-Router 存在的意义。前端路由的核心，就在于 —— 改变视图的同时不会向后端发出请求。



**为了达到这一目的，浏览器当前提供了以下两种支持：**

- hash —— 即地址栏 URL 中的 # 符号（此 hash 不是密码学里的散列运算）。比如这个 URL：http://www.abc.com/#/hello hash 的值为 #/hello。它的特点在于：hash 虽然出现在 URL 中，但不会被包括在 HTTP 请求中，对后端完全没有影响，因此改变 hash 不会重新加载页面。
- history —— 利用了 HTML5 History Interface 中新增的 pushState() 和 replaceState() 方法。（需要特定浏览器支持）这两个方法应用于浏览器的历史记录栈，在当前已有的 back、forward、go 的基础之上，它们提供了对历史记录进行修改的功能。只是当它们执行修改时，虽然改变了当前的 URL，但浏览器不会立即向后端发送请求。
- 因此可以说，hash 模式和 history 模式都属于浏览器自身的特性，Vue-Router 只是利用了这两个特性（通过调用浏览器提供的接口）来实现前端路由.



#### 使用场景

一般场景下，hash 和 history 都可以，除非你更在意颜值，# 符号夹杂在 URL 里看起来确实有些不太美丽。

如果不想要很丑的 hash，我们可以用路由的 history 模式，这种模式充分利用 history.pushState API 来完成URL 跳转而无须重新加载页面。

另外，根据 Mozilla Develop Network 的介绍，调用 history.pushState() 相比于直接修改 hash，存在以下优势:

- pushState() 设置的新 URL 可以是与当前 URL 同源的任意 URL；而 hash 只可修改 # 后面的部分，因此只能设置与当前 URL 同文档的 URL；
- pushState() 设置的新 URL 可以与当前 URL 一模一样，这样也会把记录添加到栈中；而 hash 设置的新值必须与原来不一样才会触发动作将记录添加到栈中；
- pushState() 通过 stateObject 参数可以添加任意类型的数据到记录中；而 hash 只可添加短字符串；
- pushState() 可额外设置 title 属性供后续使用。

当然啦，history 也不是样样都好。SPA 虽然在浏览器里游刃有余，但真要通过 URL 向后端发起 HTTP 请求时，两者的差异就来了。尤其在用户手动输入 URL 后回车，或者刷新（重启）浏览器的时候。

个人在接入微信的一个活动开发过程中 开始使用的hash模式，但是后面后端无法获取到我#后面的url参数，于是就把参数写在#前面，但是讨论后还是决定去掉这个巨丑的#

于是乎改用history模式，但是开始跑流程的时候是没问题，但是后来发现跳转后刷新或者回跳，会报一个404的错误，找不到指定的路由,最后后端去指向正确的路由 加了/hd/xxx 去匹配是否有这个/hd/{:path} 才得以解决



#### 总结

1. hash 模式下，仅 hash 符号之前的内容会被包含在请求中，如 http://www.abc.com，因此对于后端来说，即使没有做到对路由的全覆盖，也不会返回 404 错误。

2. history 模式下，前端的 URL 必须和实际向后端发起请求的 URL 一致，如 http://www.abc.com/book/id 如果后端缺少对 /book/id 的路由处理，将返回 404 错误。Vue-Router 官网里如此描述：“不过这种模式要玩好，还需要后台配置支持……所以呢，你要在服务端增加一个覆盖所有情况的候选资源：如果 URL 匹配不到任何静态资源，则应该返回同一个 index.html 页面，这个页面就是你 app 依赖的页面。”

3. 结合自身例子，对于一般的 Vue + Vue-Router + Webpack + XXX 形式的 Web 开发场景，用 history 模式即可，只需在后端（Apache 或 Nginx）进行简单的路由配置，同时搭配前端路由的 404 页面支持。





## 过滤器

过滤器是对即将显示的数据做进一步的筛选处理，然后进行显示，值得注意的是过滤器并没有改变原来的数据，只是在原数据的基础上产生新的数据。

定义过滤器

- 全局过滤器

```
Vue.filter('过滤器名称', function (value1[,value2,...] ) {  

//逻辑代码

})
```

- 局部过滤器

```
new Vue({       
 filters: {      
    '过滤器名称': function (value1[,value2,...] ) { 
       // 逻辑代码     
      } 
         }    
　　})    
```

2、过滤器使用的地方

```
　　　　双花括号插值
　　　　v-bind表达式
过滤器应该被添加在 JavaScript 表达式的尾部，由“管道”符号指示
```

```
<!-- 在双花括号中 -->
<div>{{数据属性名称 | 过滤器名称}}</div>
<div>{{数据属性名称 | 过滤器名称(参数值)}}</div>
<!-- 在 `v-bind` 中 -->
<div v-bind:id="数据属性名称 | 过滤器名称"></div>
<div v-bind:id="数据属性名称 | 过滤器名称(参数值)"></div>
```

三、实例

1、传递一个参数的全局过滤器

```
<div id="app">
    <span>{{msg|capitalize}}</span>//data中声明msg:'hello'
</div>
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 //全局过滤器，将信息转成大写
  Vue.filter('capitalize', function (value) {
    //value左边那个属性值
    return value.toUpperCase()

  })
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

2、传递多个参数的局部过滤器

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
<div id="app">

    <!--过滤器接收多个参数-->
    <span>{{value1|multiple(value2,value3)}}</span>

</div>
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
<script>

  var vm = new Vue(
    {
      el: '#app',
      data: {
        msg: 'hello',
        value1:10,
        value2:20,
        value3:30
      },
    //局部过滤器
      filters: {
        'multiple': function (value1, value2, value3) {
          return value1*value2*value3
        }
      }

    }
  )

</script>
```





## 混入











`$emit`

`slot-scope`



事件总线

子传父

父传子

兄弟

`$root`

`$children`

`$parent`

`$refs`

`$scopedSlots`

`$attrs`

`$slots`



## 生命周期

事物从诞生到消亡

一个`new Vue()`,里面做了一系列事情

![](E:\学习相关\国信安培训\笔记\四阶段\lifecycle.png)



































## 懒加载

用到时才加载

当打包构建应用时，Javascript包会变得非常大，影响页面加载。
如果我们能把不同路由对应的组件分割成不同的代码块，然后当路由被访问的时候才加载对应组件，这样就更加高效了

首先,我们知道路由中通常会定义很多不同的页面.
这个页面最后被打包在哪里呢?一般情况下，是放在一个js文件中.但是，页面这么多放在一个js文件中,必然会造成这个页面非常的大.
如果我们一次性从服务器请求下来这个页面,可能需要花费一定的时间,甚至用户的电脑上还出现了短暂空白的情况.
如何避免这种情况呢?使用路由懒加载就可以了.

![image-20210109141251668](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20210109141251668.png)

![image-20210109141155921](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20210109141155921.png)



## 路由嵌套

实现嵌套路由有两个步骤:

- 创建对应的子组件,并且在路由映射中配置对应的子路由
- 在组件内部使用<routerview>标签.



## 参数传递

 Profile，档案

 ![image-20210109142622337](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20210109142622337.png)

URL：协议：//localhost：80/path

URL：协议//主机：端口/路径？查询



如何使用它们呢？有两种方式：<router-link>的方式和JavaScript代码方式



#### 子组件和父组件传值

##### **父组件与子组件传值props**

##### **子组件向父组件传递数据**

子组件通过$emit方法（用来触发事件,详情见[官网](https://cn.vuejs.org/v2/api/#vm-emit)）传递参数：



## `$route`和`$router`的区别

自己写插件需要install

所有的组件都继承自vue原型

defineProperty方法



## 导航守卫

导航守卫就是路由跳转过程中的一些钩子函数，再直白点路由跳转是一个大的过程，这个大的过程分为跳转前中后等等细小的过程，在每一个过程中都有一函数，这个函数能让你操作一些其他的事儿的时机，这就是导航守卫。

#### **全局前置守卫** `router.beforeEach(fn)`

前置钩子

**全局前置守卫是写在入口文件 main.js 中的，在进入路由前执行**

```js
//router-> index.js中
//全局前置守卫
//一般用来做一些进入页面的限制。比如没有登录，就不能进入某些页面，只有登录了之后才有权限查看某些页面。。。说白了就是路由拦截。
router.beforeEach((to,from,next)=>{
	//从from跳转到to
	document.title=to.matched[0].meta.title //在to的路由配置中，写上meta信息,matched是有路由嵌套的时候用，0是一级路由
	next()

})

```

meta元数据，路由元信息

1、Vue.beforeEach(function(to,form,next){}) /*在跳转之前执行*/

2.Vue.afterEach(function(to,form))/*在跳转之后判断*/

```js
// 全局前置路由守卫
router.beforeEach( (to,from,next) =>{
    const name = localStorage.getItem('name');//查看本地存储上是否有name对象
    if( name || to.path === '/login'){//短路逻辑，有就可以继续执行，没有就跳转到登录页面
        next()
    }else{
     next( '/login' )//跳转登录页面
    }
})


// 全局后置路由守卫 router.afterEach(fn)，表示离开当前路由时执行
router.afterEach( (to,from,next)=> {
    if(to.path === '/user'){//当to的path值等于这个时
        alert('确定进入user吗')
    }
})

```

#### 全局的后置守卫 `afterEach(fn)`

后置钩子

可以做一些用户友好提示

不需要主动执行next

#### 路由独享守卫

- 写在路由表中的守卫钩子
- 针对的是和当前路由相关的，那么其他与之不相关的路由，它是无法监听它的变化情况的

```js
{
path: '/user',
component: User,
beforeEnter: ( to,from,next ) =>{
    // console.log(to)
    const name = localStorage.getItem('name');//判断本地存储有没有name对象
    if( name){//存在就可以继续执行
        next()
    }else{
        setTimeout(()=>{
                alert('你还没有登录，点击跳转登录')//不存在就弹窗告诉没有登录，点击登录
                next('/login')
            },0)
       }
    }
},
```

#### 组件内守卫

- 有三种
  - beforeRouteEnther( (to,from,next) =>{} ) 进入组件时触发【 //注意写法，fore route 】
  - beforeRouteUpdate( (to,from,next) =>{} ) 数据改变时触发
  - beforeRouteLeave( (to,from,next) =>{} ) 离开组件时触发                                                                                                                                       

##### 组件内的前置守卫

- 导航进入组件时，调用
- this是访问不到的，如果非要访问this ,必须通过 next(vm=>{})访问
- 因为组件此时没有创建，所以没有this
- 案例： 数据预载（进入组件前就获得数据）

##### 组件内的后置守卫

- 离开组件时，调用
- this是可以访问到

##### 组件内的更新守卫（ 路由传参和路由的接参 ）

- **在当前路由改变，但是该组件被复用时调用**
- 举例来说，**对于一个带有动态参数的路径 /foo/:id，在 /foo/1 和 /foo/2 之间跳转的时候，**
- 由于会渲染同样的 Foo 组件，因此组件实例会被复用。而这个钩子就会在这个情况下被调用。
- 可以访问组件实例 `this`



## keepalive

keep-alive是Vue内置的一个组件，可以使被包含的组件保留状态，或避免重新渲染。使组件不被频繁的创建和销毁

router-view也是一个组件 ，如果直接被包在keep-alive里面，所有路径匹配到的视图组件都会被缓存

```js
<keep-alive exlude="About,User">  //把组件名(name)为About，User的组件排除在外
	<router-view></router-view>
</keep-alive>
```

但是有嵌套路由时，因为可能设置过默认路由的原因，所以可能会失效，就需要设置组件内的导航守卫：

```js
activated(){
	this.$rouyer.push(this.path)
}
//activated函数和deactivated函数，只有该组件使用了keep-alive时，才是有效的
beforeRouterLeave(to,from,next){
	this.path=this.$route.path
	next()
}
```

include 字符串或正则表达，只有匹配的组件会被缓存

exlude 字符串或正则表达式，任何匹配的组件都不会被缓存



## 路径问题

 给路径起别名

比如说@对应src

webpack.base.conf.js文件中，alias



## promise

#### 什么是promise

- ES6中一个非常终于和好用的特性就是promise

- promise是异步编程的一种解决方案

- 那什么时候我们会来处理异步事件呢?

- 一种很常见的场景应该就是网络请求了。
  我们封装一个网络请求的函数 ，因为不能立即拿到结果，所以不能像简单的3+4=7一样将结果返回。

- 所以往往我们会传入另外一个函数,在数据请求成功时，将数据通过传入的函数回调出去。
  如果只是一个简单的网络请求，那么这种方案不会给我们带来很大的麻烦。

- 但是,当网络请求非常复杂时,就会出现回调地狱。

  

  setTimeout是异步的

  

  promise是一个类

  链式编程

#### 什么情况下会用到promise？

一般情况下是将异步操作进行封装



#### 使用

在执行传入的回调函数时，会闯入两个参数，resolve,reject，它们两个本身又是函数

```js
//写法一
new Promise((resolve,reject)=>{
	setTime(()=>{
        //成功的时候调用resolve
		resolve("ajiao") //将这个数据返回
        
        //失败的时候调用reject
        reject('ERR MESSAGE')
	},1000)
})
.then((data)=>{ //接收到上一个成功时返回的数据
	cosole.log(data) //ajiao
})
.catch((err)=>{ //接收到上一个失败时返回的数据
    console.log(err) //ERR MESSAGE
})
```

```js
//写法二
new Promise((resolve,reject)=>{
	setTime(()=>{
        //成功的时候调用resolve
		resolve("ajiao") //将这个数据返回
        
        //失败的时候调用reject
        reject('ERR MESSAGE')
	},1000)
})
.then((data)=>{ //接收到上一个成功时返回的数据
	cosole.log(data) //ajiao
},(err)=>{
	console.log(err) //ERR MESSAGE
})
```



#### 三种状态

sync->同步

async->异步

 

#### Promise的链式调用

```js
new Promise((resolve,reject)=>{
	setTime(()=>{
        //成功的时候调用resolve
		resolve("ajiao") //将这个数据返回
        
        //失败的时候调用reject
        reject('ERR MESSAGE')
	},1000)
})
.then((data)=>{ //接收到上一个成功时返回的数据
	cosole.log(data) //ajiao
	//写法一
	return new Promise((resolve,reject)>{
		resolve(data + "aaa")
		reject("err aaa")
	})
	
	//写法二 是方法一的简写
	return Promise.resolve(data + "aaa")
	return Promise.reject("err aaa")
	
	//写法三 是方法二的简写，省略掉Promise.resolve
	return data+"aaa"
})
.then(data=>{
	console.log(data) //aaa
})
.catch((err)=>{ //接收到上一个失败时返回的数据
    console.log(err) //ERR MESSAGE
})
//如果某一层失败了，后面的then就不会执行了，会执行catch
```



#### Promise的all函数

 可迭代对象

   

当出现需要两次及多次请求都实现时，再怎么怎么样的需求，需要用all函数对两个及多次请求进行封装，.then拿到的结果是一个数组，里面有这两次请求返回的数据

```js
Promise.all([
	new Promise((resolve,reject)=>{
		setTimeout(()=>{
			resolve("aaa")
		},2000)
	}),
	new Promise((resolve,reject)=>{
		setTimeout(()=>{
			resolve("bbb")
		},2000)
	})
])
.then(results=>{
	console.log(results) //["aaa","bbb"]
})
```



## Vuex

官方解释: Vuex是一个专为Vuejs应用程序开发的状态管理模式。

状态管理到底是什么?

- 状态管理模式、集中式存储管理这些名词听起来就非常高大上,让人捉摸不透。
- 其实，你可以简单的将其看成把需要多个组件共享的变量全部存储在一个对象里面。
- 然后，将这个对象放在顶层的Vue实例中,让其他组件可以使用。
- 那么，多个组件是不是就可以共享这个对象中的所有变量属性了呢?

所有的组件都继承自vue实例，可以把数据放在vue的原型对象上来达到所有组件共用的目的，但是这种方法不是响应式的，所以就要使用vuex，他能保证这些属性都是响应式的

token



#### 单页面的状态管理

![](E:\学习相关\国信安培训\笔记\四阶段\flow.png)

state数据渲染到view视图上，再view上进行Actions事件操作，然后改变state数据，再改变view视图



#### 多页面的状态管理



#### 创建

```js
import Vue from 'vue'
import Vuex from 'vuex'

//1.安装插件
Vue.use(Vuex)

//创建并导出
export default new Vuex.Store({})
//还可以这样：
//先创建
const store = new Vuex.Store({})
//再导出store独享
export default store

//然后在main.js中进行挂载
important store from './store'
new Vue({
    el:'#app',
    store,
    render:h=>h(App)
})
```

![](E:\学习相关\国信安培训\笔记\四阶段\vuex.png)

就是在组件中触发 Action，Action 则会提交 Mutation，Mutaion 会对 State 进行修改，组件再根据 State 、Getter 渲染页面。

vuex解决跨组件的通信问题：1、父子之间通信 2、非父子之间通信

父子之间通信通过prop实现父组件向子组件传递数据，通过子组件中触发事件实现向父组件传递数据

非父子组件之间的通信一般都是通过一个vue实例作为中转站，也可以成为事件中心、event bus



现在也有用sessionStorage储存信息的，但是用这个方法的话主要是对数据进行存储，但是在关闭浏览器窗口后，数据就会被删除。

如果是不变的数据的话可以用本地数据代替vuex，但是当两个组件共用一个数据源，对象或数组的时候，如果一个组件改变了数据员，另一个要变化的时候，sessionStorage是无法做到的

和vuex的区别：

1. vuex储存在内存，sessionStorage（会话储存），临时保存，只能存储字符串类型，对于复杂的对象可以使用ECMAscript提供的JSON对象和parse来处理
2. vuex用于组件传值，而sessionStorage主要是不同页面之间的传值



#### 基本使用

```js
const store = new Vuex.Store({
	state:{
		counter:1000
	},
	mutations:{
		//方法
		//但是要修改值，还需要commit提交
		increment(state){
			state.counter++
		},
		decrement(state){
			state.counter--
		}
	},
	actions:{},
	getters:{},
	modules:{}
})


//在组件中
<h2>{{$store.state.counter}}
<button @click="add"></button>
<button @click="sub"></button>

methods:{
	add(){
		this.$store.commit('increment')
	},
	sub(){
		this.$store.commit('decrement')
	}
}
```



#### 核心概念

##### state

相当于组件的data

###### 单一状态树

也可以叫做单一数据源

Vue建议把所有需要共享的数据放在一个store中，而不是 创建很多个store来分开管理，这样不方便



##### getters

**相当于计算属性**,可以在里面对state的数据进行一些处理

```js
<h1>{{$store.getters.getGreater}}</h1>



state:{
	counter:1000
},
getters:{
	getGreater(){
		return state.counter * state.counter
	}
},	
```

还可以传参,第一个参数永远是state，第二个参数永远是getters，无论写什么名字

```js
<h1>{{$store.getters.moreAgestu(20)</h1>


getters:{
	more20stu(state){
		return state.students.filter(s => s.age>20)
	},
	more20stuLength(state,getters){ //还可以把getters作为参数传进去，就可以使用其他getters方法了
		return getters.more20stu.length
	}，
    moreAgestu(state){  //在state，getters之外动态传参
        return function(age){
            return state.stufents.filter(s => s.age>age)
        }
    }
}
```



##### mutation

相当于组件的methods

Vuex的store状态更新唯一方式：**提交Mutation**

Mutation主要包括两部分∶

- 字符串的事件类型( type )
- 一个回调函数( handler ) ,该回调函数的第一个参数就是state。

###### 传入参数,payload,负载

参数被称为是mutation的**载荷(payload)**

```js
<h1>{{$store.state.count}} </h1>
<button @click="addNum(5)">+5</button>
<button @click="addNum(15)">+15</button>
//还可以传入一个对象
<button @click="addStu"></button>

methods:{
	addCount(num){
        this.$store.commit('addNum',num)
    }
    addStu(){
        obj={id:'1',name:'ajiao',age:'18'}
        this.$store.commit("addStu",obj)
    }
}



mutations:{
    addNum(state,num){
        return state.count+=num
    }
    addStu(state,obj){
        return state.Student.push(obj)
    }
}
```



###### 提交风格

```js
//1.普通的提交封装
this.$store.commit('addNum',num)

//2.特殊的提交封装 ,此时提交给mutation的是一个对象
this.$store.commit({
    type:'addNum',
    num
})
```



###### 响应规则

state中属性都会被加入到响应式系统中,而响应式系统会监听属性的变化

当属性发生变化时,
会通知所有界面中用到该属性的地方,让界面发生刷新

Vue.set

Vue.delete



###### 常量类型

把函数名等抽成常量来使用

###### 同步函数

Vuex要求我们mutation中的方法必须是同步方法

如果是异步操作，devtools将不能含好的追踪这个操作什么时候会被完成



##### action

相当于组件异步methods

但是某些情况,我们确实希望在Vuex中进行一些异步操作,比如网络请求,必然是异步的.这个时候怎么处理呢?

Action类似于Mutation,但是是用来代替Mutation进行异步操作的.

```js
mutations:{
    updateInfo(state){
        setTimeout(()=>{
			state.count=2000
		},1000)
    }
	
}
actions:{
    //context上下文
    //可以返回一个Promise，然后在dispatch中通过.then来继续后面的操作
	updateInfo(context,payload){
        setTimeout(()=>{
            context.commit('updateInfo')
            console.log(payload)
        },1000)
    }
}


//组件中
updateInfo(){
    this.$store.dispatch('updateInfo')
}

///组件dispatch派发到actions，actions再commit提交到mutation进行修改
```



##### module

Module是模块的意思,为什么在Vuex中我们要使用模块呢?

Vue使用单—状态树,那么也意味着很多状态都会交给Vuex来管理.
当应用变得非常复杂时,store对象就有可能变得相当臃
肿.

为了解决这个问题, Vuex允许我们将store分割成模块(Module),而每个模块拥有自己的state、mutation、action、getters等



#### 项目结构

Vuex 并不限制你的代码结构。但是，它规定了一些需要遵守的规则：

1. 应用层级的状态应该集中到单个 store 对象中。
2. 提交 **mutation** 是更改状态的唯一方法，并且这个过程是同步的。
3. 异步逻辑都应该封装到 **action** 里面。

只要你遵守以上规则，如何组织代码随你便。如果你的 store 文件太大，只需将 action、mutation 和 getter 分割到单独的文件。

对于大型应用，我们会希望把 Vuex 相关代码分割到模块中。下面是项目结构示例：

```
├── index.html
├── main.js
├── api
│   └── ... # 抽取出API请求
├── components
│   ├── App.vue
│   └── ...
└── store
    ├── index.js          # 我们组装模块并导出 store 的地方
    ├── actions.js        # 根级别的 action
    ├── mutations.js      # 根级别的 mutation
    └── modules
        ├── cart.js       # 购物车模块
        └── products.js   # 产品模块
```



## http

![image-20210112225534322](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20210112225534322.png)

## axios

#### 选择

Vue中发送网络请求有非常多的方式，那么,在开发中,如何选择呢?

**选择一**:传统的Ajax是基于XMLHttpRequest(XHR)

为什么不用它呢?

非常好解释,配置和调用方式等非常混乱.编码起来看起来就非常蛋疼.
所以真实开发中很少直接使用,而是使用jQuery-Ajax

**选择二**:在前面的学习中,我们经常会使用jQuery-Ajax>

相对于传统的Ajax非常好用.
为什么不选择它呢?

首先,我们先明确一点:在Vue的整个开发中都是不需要
使用jQuery 了.

那么,就意味着为了方便我们进行一个网络请求,特意引用一个jQuery,你觉得合理吗?

jQuery的代码:w+行.
Vue的代码才1w+行.
完全没有必要为了用网络请求就引用这个重量级的框架.

**选择三**:官方在Vue1.x的时候,推出了Vue-resource.

Vue-resource的体积相对于jQuery小很多.

另外Vue-resource是官方推出的.

为什么不选择它呢?

在Vue2.0退出后, Vue作者就在GitHub的Issues中说明
了去掉vue-resource,并且以后也不会再更新.

那么意味着以后vue-reource不再支持新的版本时,也不
会再继续更新和维护.

对以后的项目开发和维护都存在很大的隐患.

**选择四**：axios

#### axios功能特点

- 在浏览器中发送XMLHttpRequests请求

- 在node.js 中发送http请求，而jq-AJAX不可以

- 支持 Promise API

- 拦截请求和响应

- 转换请求和响应数据

- 等等

#### 基本使用

axios是基于promise对ajax的一种封装

支持Promise

ajax是基于mvc

axios是基于mvvm



```js
//默认使用get方式请求
axios({
	url:'',
    params:{
        id:1,
        age:20
    }
})
.then(res=>{
	console.log(res)
})


//2.axios发送并发请求 ,在两次网络请求都成功之后，在执行then
axios.all([axios({
    url:''
}),axios({
    url:'',
    params:{}
})])
.then(results=>{
    console.log(results) //数组，两条数据
})
```

```js
//指定请求方式为post请求、get请求
axios({
	url:'',
	method:'post', //method:'get'
    data:{
        id:1
    } 
})
.then(res=>{
	console.log(res)
})


此时发送给后端的是对象{id:1},java可能拿不到
axios使用携带请求参数请求默认使用application/json
解决方案1：
	把data换成params
解决方案2：
	"name=漳卅四年"
解决方案3：
	服务器端给接受的参数加上@requestBody
```

因为此时传参都是使用？问号在路径后面拼接的方式，不是很安全，所以推荐使用axios.get和axios.post方法



对象解构

```js
const obj1={
	name:'ajiao',
    age:'18',
    sex:'女'
}

const {name,age,sex}=obj1
```

数组结构

```js
const names=['ajiao','mumu','yaoyao']
const [name1,name2,name3]=names
```



baseURL



#### axios请求方式

```js
//使用axios.get方式发送无参请求
axios.get('路径').then(res=>{}).catch(err=>{})
```

```js
//使用axios.get方式发送有参请求
axios.get('路径',{params:{id:1,name:ww}}).then(res=>{}).catch(err=>{})
```



```js
//使用axios.post无参请求
axios.post('路径').then(res=>{}).catch(err=>{})
```

```js
//使用axios.post发送有参请求
axios.post('路径',"id=1&age=10").then(res=>{}).catch(err=>{})
```



#### 四次拦截

