

# js基础

[TOC]



## 1  什么是js

是一种嵌入在网页中的程序段。
是一种解释型语言，被浏览器解释执行。由Netscape发明，ECMA将其标准化。
JavaScript借用了Java的名字，但它和java没有关系，出于安全性考虑，增加了JavaScript的限制，增强客户端的交互功能。

2015年后，推出了ES6，这次更新最大，每年增加一个版本

**查看兼容性网站：**

https://caniuse.com/

## 2   JavaScript能做什么

可以使用JS添加、删除、修改网页上的所有元素及属性。在HTML网页中动态写入文本。
响应网页中的事件，并做出相应处理。可用于较验客户端提交的数据。
检测浏览器类型及版本。
处理Cookie.
服务器的开发，如nodejs，websock.js保持长时间的通话。第三方库，three.js,echar.js。



## 3  架构体系

### 3.1  JavaScript添加到HTML的方法

在Html中嵌入JavaScript脚本（内嵌式)

在Html中链接一个外部的javaScript文件

直接编写在元素的事件属性中(所有on开头的属性名)

伪URL方法(在a标签href属性写入js代码)  

```html
//嵌入式
<script type="text/javascript">
 //输出的一个函数:弹出一个信息提示框。
window.alert( "Hello world.");
</script>


//引用外部的JS文件
<script src="../js/demo1.js"></script>

//在元素的事件属性中，on开头的标签属性
<button onclick="window.alert('今天天气好。')">click Me</button>

//伪URL方法（在a标签href属性写入js代码
<a href="http: //www.baidu.com">baidu</a>
<a href="javascript: window.alert('今天学习JS代码 ')">baidu</ a>

```

script标签必须写在`</body>`之前，不要写在`<head></head>`标签里，也不要与html标签混合写



### 3.2  输出与输出的方式

**输出:**

1. alert：弹出一个信息提示框

```js
window.alert("你好")
```

2. write：在html文档中，输出变量的值

```js
document.write("你的性别是" + sex)；
```

3. console.log

**输入:**

​	window.promt()，弹框内输入，该方法**返回用户输入的内容**；



### 3.3  变量的声明

//单行注释

/* */多行注释

**变量的声明**：var

**变量的定义**

​	弱类型,不一定要初始化。

​	变量区分大小写:a和A代表不同变量

​	必须是字母，下划线_、或者美元符号$开头，不能数字开头

**标识符**

​	**定义**∶

​	在程序中有许多需要命名的对象，以便在程序的其它地方使用。最基本的方式就是为对象命名，每种程序语言都规定了在程序里描述名字的规则。这些名字包括:变量名、常数名、数组名、函数名、文件名、类型名等，通常被统称为“标识符”。

​	比如

​	var a;
a就是变量名，即标识符

**合法的标识符:**

​	第一字符必须是一个字母、下划线(_)或一个美元符号($)，并且不能把关键字、保留字、true、false和null、undefined等作为标识符

**关键字**

​	在js系统中，有着特殊意义的单词，不可用于变量命名

|          |          |        |            |
| -------- | -------- | ------ | ---------- |
| break    | else     | new    | var        |
| case     | finally  | return | void       |
| catch    | for      | switch | while      |
| continue | function | this   | with       |
| default  | if       | throw  | delete     |
| in       | try      | do     | instanceof |
| typeof   |          |        |            |

**保留字**

​	关键字的备胎。今后可能成为关键字的单词。

|          |            |           |              |
| -------- | ---------- | --------- | ------------ |
| abstract | enum       | int       | short        |
| Boolean  | export     | interface | static       |
| byte     | final      | long      | super        |
| char     | float      | native    | synchronized |
| class    | extends    | package   | throws       |
| const    | goto       | private   | transient    |
| debugger | implements | protected | volatile     |
| double   | import     | public    |              |

**举例**

```js
//声明变量同时赋值，叫声明并初始化变量;
var userName =“吴刚";
var u_age = 18;
var u_height = 178;
var u_weight = 90;
var u_sex ="男";

//只声明变量，不初始化变量;
var d_edu;

```



### 3.4  常量的声明

常量名，全部大写，初始化后，不修改，不能给常量赋值。

const

```JS
const PI=2.33;//正确写法
PI=window.prompt("给PI赋值：");//这一行会报错，不能赋值
```



### 3.5  js数据类型

**基本类型值**

-   undefined，**变量声明，但未初始化时**，变量的值时undefined。当函数无明确返回值时，其调用结果也是undefined。

    ```js
    console.log(u_name) // undefined
    window.alert(u_name)
    document.write(u_name)
    ```

-   null:值为null，null是从undefined派生来的，都表示没有，因此**null==undefined**，null表示不存在的对象。但是**null ===undefined**是不想等的，因为值相等，但是数据类型不同，不相等。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               

-   null主要用来表示一个对象是空对象（即**对象不存在**！);

    ```js
    var Div = document.getElementById("div1");
    console.log(Div);//null
    ```

-   boolean:true或false

    ```js
    // boolean类型:true表示真值,false表示假值;
    var u_sex ="男";
    console.log(u_sex == '女')
    // false表示假值，也就是说这个表达式不成立。
    console.log(u_sex ='男') 
    // true,表示真值，也就是说这个表达式成立。
    ```

-   number:数值，包含整型（十进制、8进制、16进制）和浮点型（带小数点）两种数值，没用单精度和双精度之分

-   string:字符串，可用单引号或双引号声明，引号中，如果还要包括引号，只能嵌套使用，只能单引号中包括双引号，或者双引号包括单引号。



**判断变量的数据类型**

```js
var userName =“吴刚";
var u_age = 18;
var u_color ="黄色", u_state = false, u_id = "5123123834234", u_phone = "13990906969", u_QQ, u_email;
var oDiv = document.getElementById("div1");
console.log(typeof userName) //String
console.log(typeof u_age)//number
console.log(typeof u_color) //string
console.log(typeof u_state) // boolean
console.log(typeof u_QQ)//undefined
console.log(typeof oDiv) //object空对象，不是Null,而是object.

console.log(oDiv)//null,表示空对象
//空对象的值是null，但是类型是object
```


| 返回类型  | 类型描述   |
| --------- | ---------- |
| undefined | 未定义     |
| boolean   | 布尔值     |
| string    | 字符串     |
| number    | 数值       |
| object    | 对象或null |
| function  | 函数       |
| NaN       | number     |

​    **null类型只有一个值，null，undefined类型也只有一个值，undefined，null类型是object，undefined类型是undefined。**




### 3.6  数据类型之间的转换

**转成Boolean**

```js
var u_name =“张三"，age = 29,sex = true，u_height;
var oDiv = document.getElementById("div1");

//字符串转boolean，如果引号中没有任何字符，则是false，如果有任何字符，则是true.
console.log(Boolean(u_name)) //true
console.log(Boolean("")) //false
console.log(Boolean(" ")) //true


//null,undefined转Boolean，都是false
console.log(Boolean(u_height)) //false，undefined -> false
console.log(Boolean(oDiv)) //false，null -> false


//数字转boolean,非o为真值(true)，0为假值(false);
console.log(Boolean(age)) //true
console.1og(Boolean(o)) //flse,0 -> false
console.log (Boolean( -0.1230))//true，非o时，为true.
```



**转成字符串**

​	String（）、toString（），

​	String (number,string, boolean,null,undefined)，在原来的值上，加引号，表示字符串

​	toString()，null,undefined时，不能调用该方法;

```js
var u_name =“张三"，age = 29,sex = true，u_height;
var oDiv = document.getElementById("div1");

console.log(age)//29
console.log(string(age))//"29”
console.log(age.tostring())//"29",跟上一个String是一样的效果，只是使用方法不一样
//﹒是一个运算符，主要是通过它来使用对象的属性或方法;


console.log(sex)// true
console.log(string(sex))//"true"
console.log(sex.tostring())

console.log(u_height) //undefined
console.log(String(u_height)) //"undefined"
//一个变量未初始化时，值是undefined，但是不能使用toString（）来转成字符串，会报错

console.log(oDiv) //null
console.log(string(oDiv)) //"null"
//null时也不能使用toString（）来转成字符串，会报错

```



**转成数字**

​	Number()全部转换，parseInt()转换成**整数**，parseFloat（）转换成浮点数

```js
console.log(Number(true));//1
console.log(Number(false));//0

//判断时，从字符串第一个字符开始，依次判断是否是有效的数字符号，0-9，.，+，-,如果有一个不是，就返回NaN,只有全部是有效的数字符号时，才返回数字
//Number（），是把所有的字符串，转换成数字
console.log(Number("123"));//123
console.log(Number("a123"));//NaN
console.log(Number(".123"));//0.123
console.log(Number("123.34"));//123.34
console.log(Number("123.3.4"));//NaN
console.log(Number("-123.34"));//-123.34
console.log(Number("+123.34"));//+123.34
console.log(Number("@-123.34"));//NaN

console.log(Number(null));//0
console.log(Number(undefined));//NaN
```

```js
//parsetInt(),把字符串，从左边开始，依次向右进行转换，遇到非有效数字符号停止转换，如果第1个字符就是非有效数字符号，则返回NaN;如果转换成功一部分，则返回转换成功的数字。执行的是一种部分转换的方法。
console.log(parseInt(".123"));//NaN，整数不包括小数点。
console.log(parseInt("123.123"));//123
console.log(parseInt("AA.123"));//NaN
console.log(parseInt("123HHA233"));//123
console.log(parseInt("-123.123"))//-123
console.log(parseInt("")); //NaN
console.log(parseInt(" ")); //NaN
```

```js
//parseFloat（），把字符串转换成浮点数
console.log(parseFloat("-12hello3")); //-12
console.log(parseFloat("aa12hello3")); //NaN
console.log(parseFloat("")); //NaN
console.log(parseFloat(" ")); //NaN
console.log(parseFloat(".123")); //.123

//第1个小数点之后，再出现的小数点，都是无效的字符。
console.log(parseInt("123.222.123")); //123.222                   
```

```js
//提数字的规律
q = parseInt(n / 1000)%10
b = parseInt(n / 100)%10
s = parseInt(n / 10)%10
g = parseInt(n / 1)%10
```

 

16进制的转换，8进制的转换



**parseInt():**

| 参数   | 描述                                                         |
| :----- | :----------------------------------------------------------- |
| string | 必需。要被解析的字符串。                                     |
| radix  | 可选。表示要解析的数字的基数。该值介于 2 ~ 36 之间。如果省略该参数或其值为 0，则数字将以 10 为基础来解析。如果它以 “0x” 或 “0X” 开头，将以 16 为基数。如果该参数小于 2 或者大于 36，则 parseInt() 将返回 NaN。 |

### 3.7  html,js中的特殊符号

|   符号   |   意义    |
| :------: | :-------: |
| &nbsp ； |   空格    |
|  &lt；   |     <     |
|  &gt；   |     >     |
| &copy；  | ©，版权号 |
|  &amp；  |     &     |

string类型包含了一些特殊的字符字面量，也叫转义符

| 字面量 | 含义             |
| ------ | ---------------- |
| \n     | 换行             |
| \t     | 制表             |
| \b     | 空格             |
| \r     | 回车，相当于换行 |
| \f     | 进制             |
| \\     | 斜杠             |
| \ ‘    | 单引号           |
| \ “    | 双引号           |



### 3.8  运算符与表达式

#### 3.8.1  表达式

**最简单的表达式**

是字面量或者变量名。字面常量的计算结果等于它本身的值;
符号常量的计算结果等于使用编译指令定义它时给它指定的值;

变量的计算结果等于程序赋给它的当前值。

```js
5.96//数值字面量

'JACK'//字符串字面量

```

true//布尔值字面量
    
```js
null//空值字面量

/Java///正则表达式字面量
```

{x:1, y:2}//对象字面量、对象表达式
    
		[1,2,3]//数组字面量、数组表达式
	
		function(n){return x+y;}//函数字面量、函数表达式
	
		box//变量




**复杂表达式**

由多个更简单的表达式组成，表达式之间用**运算符连接**

```js
myNo+ 5.94//加法运算的表达式

```

typeof(myNo)//查看数据类型的表达式
    
   	 myNo > 8//逻辑运算表达式



#### 3.8.2  分类

算术运算符、一元运算符、赋值运算符、关系运算符、逻辑运算符、三元运算符

##### 3.8.2.1  赋值运算符：

​	=

```js
var a=100//是把100赋值给等号左边的变量a，从右向左运算的。
```



##### 3.8.2.2  算术运算符：

​	+ ，-，*，/，%（取模，即求余数）

​	有赋值运算符的表达式，一定要先计算右侧的表达式，右侧的表达式计算最终结果后，再赋值给左边的变量

​	当"+”遇到字符串时，就叫字符串拼接符号。**最后的结果一定是字符串。**

​	js中，没用取整的说法，取整由Math对象的方法来控制，比如：ceil（）。。。，floor（）。。。，**parseInt（）**。。。。

​	运算优先级：*，/，%大于+，-，相等级别时，从左向右依次计算，（）可以提升运算符的优先级别



##### 3.8.2.3  关系运算符

​	用于进行比较的运算符称作为关系运算符;用来描述一个或多个对象之间的关系，如果成立就是true，如果不成立，就是false

​	”==”：相等运算符,只比较值,**不比较类型**

​	“!=”：不相等运算符

​	“===”：全等(恒等)，**值和类型都必须相等**

​	“!==”：不全等(不恒等)，**完全相等时，得到false**

​	“>”：大于运算符

​	“>=”：大于等于运算符，**不能写成“=>”，是错误的写法**

​	“<”：小于运算符

​	“<=”：小于等于运算符

​	最终返回一个boolean值; true, false;



**关系运算符的规则一：**

-   关系运算符都是双目运算符,其结合性均为左结合。
    所谓左结合是指在优先级相同的情况下，从左往右开始处理。

    如: a == b == c,
    5 == 3 == 2=>false == 2 =>false
    这个表达式会先比较a==b，将比较后的返回结果再与c比较。

-   关系运算符返回的肯定是布尔值。

-   关系运算符的优先级低于算术运算符“+、-、*、%"，高于赋值运算符“=”。在六个关系运算符中，<、<=、>、>=的优先级

-   关系运算符比较时，两个操作数都是数值，则数值比较

-   关系运算符比较时，两个操作数都是字符串，则比较两个字符串对应的字符编码值

-   关系运算符比较时，两个操作数有一个是数值，则将另一个转换为数值，再进行数值比较



**关系运算符规则二：**

-   在相等和不等的比较上，如果操作数是非数值，则遵循一下规则︰
-   一个操作数是布尔值，则比较之前将其转换为数值，false转成0，true转成1
-   —个操作数是字符串，则比较之前将其转成为数值再比较
-   不需要任何转换的情况下，null和undefined是相等的
-   —个操作数是NaN，则==返回false，!=返回true ; 并国NaN和自身不等
-   两个操作数都是对象，则比较他们是否是同一个对象，如果都指向同一个对象，则返回true，否则返回false。
-   在全等和全不等的判断上，比如值和类型都相等，才返回true，否则返回false。

**NaN不等于任何东西，包括自身**

| 表达式            | 值    |
| ----------------- | ----- |
| null == undefined | true  |
| ‘NaN’ == NaN      | false |
| 5 == NaN          | false |
| NaN == NaN        | false |
| false == 0        | true  |
| true == 2         | false |
| true == 1         | true  |
| undefined == 0    | false |
| null == 0         | false |
| ‘100’ == 100      | true  |
| ‘100’ === 100     | false |

**虽然Number（null）=0，但是null == 0是false**



##### 3.8.2.4  三元运算符

​	条件表达式?表达式1:表达式2

​	条件表达式的结果为真时，执行表达式1，反之执行表达式2



##### 3.8.2.5  逻辑与运算符

​	逻辑与&&，表示和

​	全真时为真，有假为假

​	运算原理:

​	**如果&&左边的结果为假，就直接返回左边表达式的结果，不再计算右边表达式。**

​	**如果左边的结果为真，就计算右边的表达式;返回结果是右边表达式的结果。**

​	最后表达式的结果就是返回的结果，如果需要做条件判断，再把这个结果转换Boolean值来判断结果为true或者 false


```js
var a = 5, b = 10，c = 20;
console.log(a > b 8& a < c);// false && true => false
console.log( a < 10 8& a < c)// true 8& true => true
console.log( a > b 8& a > c)// false && false => false
console.log(a < b && a > c);// true && false => false
console.log(10 && false) //true && false; => false

//注意它们的返回的结果:
console.log(null && false)//false && false => null

//如果&&左边的结果为假，就直接返回左边表达式的结果，不再计算右边表达式。因为最终逻辑&&的结果为false;

```

```js
var a = 1,b = 2;
console.log( a > b && console.log(b)) //false
console.log( a < b && b)//2
//如果左边的结果为真，就计算右边的结果;返回结果是右边表达式的结果。

console.log(a < b && a == b ? a<b : b)//2
```



##### 3.8.2.6  逻辑或

有真为真，全假为假;

**如果||左边的结果为假，就计算右边的表达式，返回结果是右边表达式的结果。**

**如果||左边的结果为真，就不计算右边的表达式;返回结果是左边表达式的结果。**



##### 3.8.2.7  逻辑非

“!”，直接取非返回结果true或者false
假即真，真即假。

**使用场景:**

当一个问题需要多个条件时，用逻辑与（符号“&&“）来表示需要“同时”满足多个条件

当一个问题需要多个条件时，用逻辑或（符号"||”)来表示需要满足所有条件中其中一个条件

直接对一个条件进行否定时，用逻辑非（符号“!”）



##### 3.8.2.8  一元运算符

++(自增）,- -（自减）

```js
var a=10；

//后缀式
a++；

//前缀式
++a；

//无论是前缀式还是后缀式，变量最终都自增1或自减1

//在复杂的表达式中，就会有区别
//前缀式时，++级别最高，要优先执行
//后缀式时，++级别最低，要最后执行,比赋值运算还要低


cosole.log(++a);//11  等同于a=a+1
cosole.log(a);//11

cosole.log(a++);//10  当前语句执行完成后，最后才执行a=a+1
cosole.log(a);//11


var a=10;
var b=20;
var c=0;
c=++a + b++;
console.log(`a=${a}`)//a=11
console.log(`b=${b}`)//b=21
console.log(`c=${c})`//c=31
//1.a=a+1;
//2.c=a+b;
//3/b=b+1;

```



##### 3.8.2.9  优先级别

! , ++（前缀式), - -(前缀式)

算术+ - * / %

关系:< > <= >= == ===

逻辑:&&
||

条件表达式?表达式1:表达式2

赋值=

++（后缀式）, --（后缀式)



##### 3.8.2.10  复合赋值运算符

+=，-=，*=，/=，%=，它是算数运算符与赋值运算符的结合

```js
//把运算符左边变量和右边结果进行算术运算，再把运算的结果，赋值给左边的变量
var a=5;
a += 5;//a=a+5
a -= 5;//a=a-5
a *= 3;//a=a*3
a /= 2;//a=a/2
a %= 5;//a=a%5
console.log(a);
```



### 3.9  ES6模板字符串

使用反引号包括所有的字符串和变量，变量使用${}包起来

```js
${变量名}
document.write(`${h}时${m}分${s}秒`)
```

可以避免很多引号不配对问题







## 4  js中的程序设计

### 4.1  编程的三大结构

-   顺序结构

    代码按照由上到下的顺序一行一行地执行。程序执行过程中没有分支、没有重复，这种结构称为顺序结构

-   选择结构

    通过对一定条件判断之后，选择将要执行的语句。它可以分为简单选择和多分支选择。
    
-   循环结构

    循环结构也叫重复结构，是指重复执行一个或几个模块，直到满足某一条件为止。



### 4.2  选择结构

#### 4.2.1  if

if语句是实现选择语句最简单、最直观的方法。它最简单的形式就是判断某个条件值是否为真，如果为真则执行一段代码。

基本语法︰
if（条件表达式）{如果条件成立，执行本语句}

<img src="C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201103111715090.png" alt="image-20201103111715090"  />



#### 4.2.2  if else

当一个问题，需要出两种选择时，或者需要出两种结果时，用if-else分支语句来处理逻辑

基本语法：if（条件表达式）{执行本语句1}else {
执行本语句2
}

如果条件表达式为真值，就执行语句1，反之，执行语句2

if语句在执行时，总有代码未被执行。

![image-20201103114327926](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201103114327926.png)



#### 4.2.3  if  else if

如果if或else的{}里面，只有一条语句，则可以不写当前的{}

多分支选择语句:始终只有一条件可以满足，并且只会执行满足条件时的那个代码块里的代码。其它代码都不被执行。如果所有条件表达式都为假，则执行最后一个else中的语句。



#### 4.2.4  switch

switch语句专用于实现多分支结构程序，是多重条件判断，用于多个值相等的比较，其特点是各分支清晰而直观。

基本语法：

switch(变量名或常量名){

case 值1:执行表达式语句1;break;

case值2:执行表达式语句2; break;

case 值2:执行表达式语句3;break;

。。。

case值n:执行表达式语句n; break;

default:执行表达式语句n+1；break；

```js
//输入数字0-6，显示输出中文的星期几

var week=parseInt(window.prompt("请输入一个0-6的整数："));

switch(week){
	case 0:document.write("星期天");break;
	case 1:document.write("星期1");break;
	case 2:document.write("星期2");break;
	case 3:document.write("星期3");break;
	case 4:document.write("星期4");break;
	case 5:document.write("星期5");break;
	case 6:document.write("星期6");break;
	default:alert("输入错误");break;
}

//prompt()返回的值是字符串类型；
//switch()做的是===恒等于判断;
//break用来中断switch语句的执行，如果没有他，就会继续向下执行代码,就没有起多条件判断的作用，如果所有条件都不满足，则执行default部分的代码;
//switch主要用来做等值判断，不适合用于做范围的判断。
//与if-else在性能上相差无几。
```





### 4.3  循环

#### 4.3.1  什么是循环

重复做某件事的现象称为"循环"。
循环结构就是在满足循环条件时，重复执行某程序段，直到循环条件不满足为止。重复执行的程序段称为"循环体”。



#### 4.3.2  循环分类

-   当型循环(while语句,for语句)

    **首先判断循环**控制表达式是否为"真"，若为"真"，则反复执行循环体。若为”假"，则结束循环。

-   直到型循环(do-while语句)

    **首先执行循环体**，然后才判断循环控制表达式，若为“真”，则反复执行循环体;直到循环控制表达式为"假”时结束循环。



#### 4.3.3  while

while语句是先验证再循环

它可以执行0次或更多次。如果在循环开始部分的条件不为真的话，循环代码永远不能执行。

语法:

声明并初始化循环变量

while（条件表达式）{循环体
}

```js
var i=1;
while(i<=10){
	document.write("跑圈<br>");
	i++;
}

var i=10; //i叫做循环的变量,i是在变化的
while(i>0){ //{}里面的代码，就是循环体
	document.write("跑圈 -- 第" + i + "圈<br>");
    document.writeln(`跑圈 -- 第${i}圈<br>`);  //自动空格
	i--; //循环的迭代表达式，按一个规律，不断地进行变化
}
```

```js
//输出1-100中的偶数;
var i = 0;//修改初始值为0;
while (i<= 100){
	document.writeln(i);
	i+=2;//修改自增的方法，每次加2.
}


var i = 0;
while( i <= 100){
//每循环一次时，验证（判断)是否是偶数?
	if(i % 2 == 0){
		document.writeln(i);
	}
	i++;
}

```



#### 4.3.4  for循环

for循环是循环控制结构中使用最广泛的一种循环控制语句。它是一种**先验循环**。

语法：

for（循环变量声明并且初始化;循环条件表达式;循环变量的自增或自减表达式）{}

每一个表达式之间用分号分隔

<img src="C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201104115614506.png" alt="image-20201104115614506" style="zoom:150%;" />

```js
for(var i=1;i<=100;i++){ 
	document.writeln(i);
}

//变成while的类似语法
var i=1;
for(;i<=100;){ //必须要保留分号的分隔语法
	document.write(i)
    i++
}

//输出偶数
for(var i=0;i<=100;i+=2){
    document.write(i)
}

for(var i=1;i<=100;i++){
    if(i%2==0){
        document.write(i)
    }
}
```

![image-20201104115726368](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201104115726368.png)



#### 4.4.5  do-while

do-while语句是**后验循环**

do-while无论循环后面的判断部分的条件是否为真，**循环至少要执行一次**，然后再判断是否满足继续循环的条件，它可以执行1次或更多次，**条件为假时停止循环**。

**未知循环次数时，使用它**

语法:
do循环体Mhile(布尔表达式);

<img src="C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201104140848072.png" alt="image-20201104140848072" style="zoom:150%;" />

```js
var i=1;
do{
	document.write(i);
	i++;
}while(i<=100); //会输出1-100


var i=1;
do{
	document.write(i);
	i++;
}while(i==0);//会输出1


var i = 1;
do {
	if(i%2 == 0){
		document.writeln(i);
	}
    //一定要自增，不然会死循环
	i++;
}while (i <= 100)//输出偶数
```

```js
//求1+2+3+4+5的和

//while方法
var sum=0;
var i =1;
while(i<=5){
	//document.writeln(i);
	sum=sum+i;
	//document.writeln(sum);
	//document.write("<br>");
	i++;
}
document.write(sum);

//for方法
var i=0,sum=0;
for(i=1;i<=5;i++){
    sum+=i;
}
document.write(sum);

//do-while方法
var i=0,sum=0;
do{
    sum+=i;
    i++;
}while(i<=5)
document.write(sum);
```

```js
//计算5*4*3*2*1

//for方法
var i=5,sum=1;
for(i=5;i>0;i--){
    sum*=i;
}
document.writeln(sum);

//while方法
var i=5,sum=1;
while(i>0){
    sum*=i;
    i--;
}
document.writeln(sum);

//do-while方法
var i=5,sum=1;
do{
    sum*=i;
    i--;
}while(i>0);
document.writeln(sum);
```



#### 4.4.6  break和continue



```js
for(var i = 1; i<11; i++){
	if( i == 5){
		break;
        //直接中断循环，立即退出循环。break出现之前的代码可以执行，但紧随其后的代码都不会执行
	}
	document.write("i="+ i+ "<br>")
}
//只会到4
    //i=1
    //i=2
   // i=3
   // i=4


    
for(var i = 1; i<11; i++){
	if( i == 5){
		continue;
        //直接跳过循环体中continue后面的代码，去执行循环体的下一轮，continue出现之前的代码可以执行，但当轮的紧随气候的代码不会执行
	}
	document.write("i="+ i+ "<br>")
}
    //i=1
    //i=2
    //i=3
    //i=4
    //i=6
    //i=7
    //i=8
    //i=9
    //i=10
    //i=11



//在未知循环次数时，在循环体中，通过一个条件来判断，满足条件时，使用break语句中来中断循环
var i=1;
do{
    document.write(i)
    if(i==50){
        break;
    }
    i++
}while(true)//输出1-50
```



#### 4.4.7  解决矩阵问题

```js
//外循环语句，外循环循环一轮，内循环要全部轮都循环完。相当于手表上分针与秒针的关系。


//外循环控制行数
for(var j=1;j<11;j++){
	//内循环语句，控制一行中有多少个*，即控制一行的列数
	for(var i=1;i<11;i++){
		document.write("*")
	}
	//在行末，加一个换行HTML标签，产生一个换行的效果
	document.write("<br>")
}


/* 
*     1行  1个*
**    2行  2个*
***   3行  3个*
****  4行  4个*

*号的输出数量的变化规律，是和外循环循环变量i的迭代（变化）规律一样，都1，2，3，4，5。。。
*/
for(var i=1;i<=4;i++){
    //内循环决定每一行中，循环的列数
    //外循环的循环变量，参与内循环循环条件表达式的构成，决定内循环的循环次数
    for(var j=1;j<=i;j++){
        document.write("*")
    }
    document.write("<br>")
}
```



#### 4.4.8  穷举法

举证，反复去举例证明某个条件是否满足

一个循环或多个循环的解决方案

```js
//有一队兵，他想知道有多少人，便让士兵排队报数:
//按从1至5报数，最末一个士兵报的数为1;
//按从1至6报数，最末一个士兵报的数为5;
//按从1至7报数，最末一个士兵报的数为4;
//最后再按从1至11报数，最末一个士兵报的数为10。
//编程求韩信至少有多少兵?

var i=1;
do{
	//循环中，报数，通过整除，判断余数是否和最后一个士兵报的数相等
	//第一次满足i的值，就是至少有多少兵的数量
	if(i%5==1&&i%6==5&&i%7==4&&i%11==10){
		//因此，if条件满足，直接中断循环，把i作为结果输出
		break
	}
	i++
}while(true)
```

```js
//有30个人，其中有男人、女人和小孩，在一家饭馆里吃饭共花了500元，每个男人各花30元,每个女人各花20元，每个小孩各花10元，问男人、女人和小孩各有几人?

//i，男人、j,女人，k，小孩
//三重循环，依次控制男人、女人、小孩的数量;

for(var i=1;i<=16;i++){
	for(var j=1;j<=25;j++){
		for(var k=1;k<=30;k++){
			//条件满足时，输出结果
			if(i+j+k==30&&i*30+j*20+k*10==500){
				document.write(`男人${i},女人${j},小孩${k}<br>`)
			}
		}
	}
}
// 需要得到所有的解决方案，所以没有写break
```





#### 4.4.9  程序中解决数据交换的问题

```js
var a=2,b=3
var temp
temp=a;
a=b
b=temp
```

两个变量的数据交换，就如在网上购物一样，不能一手交钱一手交货，而需要你把钱给淘宝，商家给你发货，收到货后，淘宝付钱给商家。

Number.toFixed(n):只显示小数点后n位



#### 4.4.10  例子

```js
//分解质因数
var n=11
var flag=true//默认是一个质数
for(var i=2;i<=n-1;i++){
	if(n%i==0){
		flag=false  //设置为不是质数
		break  //只要有一个能被整除，就表示这个数不是质数了，就可以直接退出循环
	}
}
if(flag==true){
	document.write(`${n}=1*${n}`)
}else{
	//如果不是质数，就进行分解质因数
	document.write(`${n}=`)
	for(var i=2;i<n;i++){
		if(n%i==0){
			document.write(i)
			document.write("*")
			n=m/i //当能分解一次质因数时，被除数在下一轮时必须要改变的
			i=1  //重置i的值为1，以确保在下一轮，i的值为2
		}
	}
	document.write(`${n}`)
}
```







## 5  数组

### 5.1  Math()

Math对象是一个**内置对象**

对象不需要使用new运算符来创建

使用时，直接使用Math做对象名

使用对象的属性和方法的语法： 

“.”，点运算符。

object.属性名，比如Math().PI

object.方法名()，比如Math.random()…….

```js
//随机函数,返回一个大于零小于一的随机小数
var n = Math.random();
console.log(n)

//如果要生成随机整数,0-9之间的整数
var m = parseInt(Math.random()*10)
console.log(m)

//产生一个指定范围的随机整数
var k = parseInt(Math.random()*33)//0-32
var k = parseInt(Math.random()*33)+1 //1-33

//23-35随机整数
var l = paseInt(Math.random()*(35-23+1)+23);//0-12 -> 1-13 -> 23-35

//公式：paseInt(Math.random() * (大 - 小 + 1) + 小);
```

```js
vconsole.log(Math.round(12.234))//12
console.log(Math.round(12.534))//13
//四舍五入
```

```js
console.log(Math.ceil(12.234)) //13
console.log(Math.ceil(12.534)) //13
console.log(Math.ceil(12.934)) //13
//向上取最小的整数，比12.xxx大的所有整数中，最小的一个整数
```

```js
console.log(Math.floor(12.234)) //12
console.log(Math.floor(12.534)) //12
console.log(Math.floor(12.934)) //12
//向下取最大的整数，比12.xxx小的所有整数中，最大的一个整数
```

```js
document.writeln(Math.round(Math.random()*10))// 0-10
document.writeln(Math.ceil(Math.random() * 10)) // 1-10
document.writeln(Math.floor(Math.random()* 10)) //0-9
document.writeln(parseInt(Math.random()*10)) // 0-9
```

Math.PI:圆周率，值不可改变，Math.PI=222错误，像常量一样，它的属性名全部大写



### 5.2  数组的概念

数组就是按一定顺序排列，具有某种相同性质变量的集合。

这些变量具有相同的名字，在内存中顺序排列，并通过下标相互区分，所以也叫下标变量。

数组中的各数据项称为数组元素,用数组名和下标表示。

在程序设计中，数组是十分有用的数据类型。循环中使用数组能够更好的发挥循环的作用，某些问题不使用数组就难以解决



### 5.3  创建数组的方法

```js
//1.通过new运算符，从Array()原型实例化一个数组实例对象
var arrAge=new Array();
console.log(arrAge) // [],一个长度为0的空数组。

var arrAge2 = new Array(5);
console.log(arrAge2) //2.length:5,返回一个数组对象，长度为5，但是没有数组元素，空的

var arrAge3 = new Array(23,24)
console.log(arrAge3) //[23,24]，length:2
//3.如果（）中，不是一个数字项，而是大于1个数字项，就表示创建一个新的指定数组元素值的数组

var arrAge4 = [19,20,21,22,18];
console.log(arrAge4);//4.[19，20，21，22，18]


var arrAge5 =[];// 5.通过字面量创建一个空数组；

var arrAge6 = Array();//6.把原型对象当函数来调用，返回一个空数组

```

 

### 5.4  数组的属性

Array.length,返回或者设置一个数组的长度值。

```js
//使用数组的length属性:
console.log(array.length)
//直接修改数组对象的长度;
arrAge5.length = 10;//在控制台上会有提示
```

数组在内存中是地址连续的一串空间

```js
var arr1 = ["a","b","c","d"];
console.log( arr1.length)//4;
console.log(arr1[0]) //"a"
console.log(arr1[1]) //"b"
console.log(arr1[2]) //"c"
console.log(arr1[3]) //"d"

console.log(arr1[4]) //undefined,下标越界之后，不会拿到具体的值，这些值，就像一个变量未初始化一样，返回一个undefined，不会报错

//有效下标范围：
// 从0到array.length-1的结果所在范围

//修改数组中指定数组元素的值
arr1[2]="hello"
console.log(arr1)

//添加一个新的数组元素
arr1[arr1.length] = "world"//把length的值，当数组下标变量使用时，在末尾添加一个新的数组元素。
```

```javascript
var arr1 = new Array(5)
//当循环遇到数组时，一定要考虑数组的下标范围，下标范围决定了循环变量的初始值和最终值
//下标有效范围是：0-arr1.length
for(var i=0;i<arr1.length;i++){ //不能写<=
	arr1[i] = parseInt(Math.random()*10)
}
console.log(arr1)
//换行输出
for(var i=0;i<arr1.length;i++){
    document.write(`${arr1[i]<br>}`)
}
```



### 5.5  数组对象的常用方法

注意区别哪些要改变数组本身，哪些不改变

#### 5.5.1  添加

```js
var arr =[];
//1.在数组的末尾添加一个新的数组元素
arr[arr.length] = 0;
arr[arr.length] =1;
console.log(arr)

//2.Array.push(value,...),在末尾添加，返回数组新的长度
arr.push("echo")
arr.push("hello")

//3.在数组元素的最前面添加新的数组元素,Array.unshift(vaule,...),返回数组新的长度
arr.unshift(123,12333,12322)
```

#### 5.5.2  删除

```js
//1.删除最末尾的一个数组元素，并返回被删除的这个元素,arr.pop()
console.log(arr.pop())

//2.删除数组的第一个元素，并返回被删除的这个元素,arr.shift()
console.log(arr.shift())
```

#### 5.5.3  splice方法

```js
//arr.splice(index,deleteCount,item1.....)，在任意位置给数组添加或删除任意个元素，返回的是一个数组，被删除的元素组成的数组

var arr=["ww","33","dd","rr"]

//删除
arr.splice(1,1)
console.log(arr) //从下标为1开始，删除一个，返回被删除的元素构成的数组

//添加，deletCount应该为0
arr.splice(2,0,"ss","ww")
console.log(arr)//在下标为2的元素之前，添加，返回空数组

//替换，deletCount不为0
arr.splice(2,1,"ss","ww")
console.log(arr)//从下标为2的元素开始，把多少个元素替换为"ss"和"ww"，返回被删除的元素构成的数组
```



#### 5.5.4  sort方法和sortNumber方法

```js
//排序

var arrNumber=[123,111,232432,23]

//arr.sort(),转换成字符串，并按utf-16编码进行升序排序
//ASCII编码中，0：48，9：57，A-Z：65-90，a-z：97-122
var temp = arrNumber.sort();
console.log(temp)
console.log(arrNumber)

//按数字大小来排序
//a是第一个用于排序的元素，b是第二个用于排序的元素
function sortNumber(a,b){
    return b-a;//数字的降序
    return a-b;//数字的升序
}
console.log(arrNumber.sort(sortNumber))
```



#### 5.5.5  reverse方法

```js
//颠倒

//reverse()方法将数组中元素的位置颠倒，并返回该数组。数组的第一个元素会变成最后一个，数组的最后一个元素变成第一个。该方法会改变原数组

var arrNumber=[123,111,232432,23]
console.log(arrNumber.reverse())
```



#### 5.5.6  concat方法

返回一个由当前数组和其他若干个数组或若干个非数组值组合而成的新数组

```js
var arr1=["abc","kkk"]
var arr2=[123,23,34]

var resultArr=arr1.concat(arr2)

console.log(arr1) //值不改变
console.log(arr2) //值不改变
console.log(resultArr)//resultArr=["abc","kkk",123,23,34]

var resultArr=arr1.concat(arr2,"hello","ww")
console.log(resultArr)//resultArr=["abc","kkk",123,23,34,"hello","ww"]
```



#### 5.5.7   includes方法

查找是否包含

```js
console.log(arr2.includes (23))//true
console.log(arr2.includes ("23"))//false,类型不同
```

```js
//不使用includes，查找数组元素
for(var i=0;i<arr2.length;i++){
	if(arr2.[i] == 23){
		document.writeln(arr2[i])
	}
}

//不使用includes，判断是否有，应用场景：搜索数据
var flag = false;// 没有找到
for(var i = 0; i< arr2.length; i++){
	if(arr2[i]== "22343"){
		//document.writeln(arr2[i])
        flag = true;
		break;
	}
}
document.write(flag)
//return flag
```



#### 5.5.8  join方法

连接所有数组组成一个字符串

```js
var arr2 =[123，23，34，23，2432，234，23];

var str = arr2.join("")
console.log(str)//"123233423243223423”

str = arr2.join("-")
console.log(str);//"23-23-34-23-2432-234-23"

```



#### 5.5.9  slice方法

抽取当前数组中一段元素组合成一个新的数组

startIndex：**如果是负数**，那么它规定从数组尾部开始算起的位置。也就是说，-1 指最后一个元素，-2 指倒数第二个元素，以此类推。

endIndex：**如果没有指定该参数**，那么切分的数组包含从 start 到数组结束的所有元素。如果这个参数是负数，那么它规定的是从数组尾部开始算起的元素。

```js
var arr2 =[123,23,34，23,2432,34，23];
var newArr =[];
newArr = arr2.slice(2,5)//返回从索引下标2开始，到下标5结束，但不包括下标5的所有数组元素的值构成的新数组
//以begin开始，到end结束，但不包括end的值;
console.log(newArr)//[34,23,2432]
```



#### 5.5.10  map方法

map() 方法返回一个新数组，数组中的元素为原始数组元素调用函数处理后的值。

map() 方法按照原始数组元素顺序依次处理元素。

**注意：** map() 不会对空数组进行检测。

**注意：** map() 不会改变原始数组。

| 参数                                | 描述                                                         |
| :---------------------------------- | :----------------------------------------------------------- |
| *function(currentValue, index,arr)* | 必须。函数，数组中的每个元素都会执行这个函数 <br>函数参数: <br/>参数描述*currentValue*必须。当前元素的值,item<br/>*index*可选。当前元素的索引值<br/>*arr*可选。当前元素属于的数组对象 |
| *thisValue*                         | 可选。对象作为该执行回调时使用，传递给函数，用作 "this" 的值。 如果省略了 thisValue，或者传入 null、undefined，那么回调函数的 this 为全局对象。 |



#### 5.5.11 find方法

find() 方法返回通过测试（函数内判断）的数组的第一个元素的值。

find() 方法为数组中的每个元素都调用一次函数执行：

- 当数组中的元素在测试条件时返回 *true* 时, find() 返回符合条件的元素，之后的值不会再调用执行函数。
- 如果没有符合条件的元素返回 undefined

**注意:** find() 对于空数组，函数是不会执行的。

**注意:** find() 并没有改变数组的原始值。

```js
{
    "userInfo": [
        {
            "uid": 1,
            "userName": "ajiao",
            "passPwd": "123456"
        },
        {
            "uid": 2,
            "userName": "yaomucha",
            "passPwd": "123456"
        },
        {
            "uid": 3,
            "userName": "ajiao",
            "passPwd": "123456"
        }
    ]
}




let result=userData.find(item=>{
        return item.userName === userName && item.passPwd === passPwd;
    })

cosole.log(result)
//{uid: 1, userName: "ajiao", passPwd: "123456"}
```



### 5.6  数组的随机排序

```js
//数组的随机排序
var arr=["a","b","c","d","e","f","j"]
//0-6:parseInt(Math.random()*7)
for(var i=0;i<arr.length;i++){
	//通过循环，把当前i对应的下标位置的数组元素，与一个随机下标变量的值进行交换
	var temp=arr[i]
	var n=parseInt(Math.random()*7)
	arr[i]=arr[n]
	arr[n]=temp
}
console.log(arr)
```



### 5.7  数组去重的各种方法

```js
var arr=[2,3,45,65,43,45,2,2,7,8]
//通过循环，把每一个数组元素，拿来和当前数组元素之后的每一个数组元素进行相等比较，如果相等，就删除与它相等的这个数组元素

for(var i=0;i<arr.length;i++){
	for(var j=i+1;j<arr.length;j++){
		//构建两个数的比较的表达式，使用两个不同的循环变量来表示
		//j所代表的，是当前i所在数组元素之后的每一个数组元素
		if(arr[i]==arr[j]){
			arr.splice(j,1)
			//由于删除之后，被删除数组元素之后的所有数组元素的下标，都会改变（都减一）
			//再由于循环变量在自增，就会导致漏判
			j--
		}
	}
}
console.log(arr)
```



### 5.8  冒泡算法





## 6  函数

### 6.1  定义

函数是定义一次但却可以调用或执行任意多次的一段js代码

function 函数名（参数1，参数2，。。。）{

​	函数体————要执行的语句

}

就是是一段可以重复调用，并执行的代码块

它一般来讲，会取一个名字，使用这个名字，就可以执行里面的代码

### 6.2  函数的作用

- 重用

  函数重要思想，代码重用，提高代码使用率，避免在程序中出现过多重复代码

- 分离

  分离思想，以功能模块方式将代码分离，提高代码可读性，建立模块化编程结构

必须树立函数式编程的思想

每一个函数，只解决一个基本的问题

如果要解决的问题很多，那就多写几个函数，重复调用

### 6.3  语法及分类

function 函数名（参数1，参数2，….){

​	函数体，要执行的语句

}

**按形式分，可以分为有参函数和无参函数**

**无参函数**︰在调用无参函数时，调用函数不将数据传递始被调用函数，无参函数可以带或不带返回值

**有参函数**∶在调用函数时，调用函数和被调函数之间有数据传输。也就是说，调用函数可以将数据
传递给被调函数使用，被调函数中的数据也可以带回供调用函数。

**参数可以有，可以无，有参数时叫做无参函数，没有参数叫无参函数**

```js
function sayHello(){
	window.alert("hello")
}

sayHello();//调用一次就执行一次
sayHello();
sayHello();
```

```js
//实现累加的函数，并输出和
function leijia(){
	//求5的累加
	var sum=0;
	for(i=1;i<=5;i++){
		sum=sum+i;
	}
	document.write(sum)
}
//函数只声明时，不会起作用，必须要调用
leijia();
```

```js
//有参函数的声明
function checkYear(year){
	if(year % 4 == 0 && year % 100 !=0 || year % 400==0){
		document.write(`${year}是闰年。`)
	}else{
		document.write(`${year}不是闰年。`)
	}
}
//函数声明，可以在调用之前，也可以在调用之后
//因为，js中，在编译执行js代码时，会先看一下要声明哪些变量和函数，并前置声明这些变量和函数;

checkYear(100)
//有参数时，代码更有灵活性，调用函数时，要传一个参数给函数


inputDate(2000,5,1)
//实际参数必须与形参一一对应，个数相同，每个参数的数据类型要和形参一致。
//如果没有一一对应，则导致函数体出现BUG
//声明函数时，写的参数，叫形式参数，简称形参
function inputDate(year,month,day){
    document.write(`<br>{year}年`)
    document.write(`<br>{month}月`)
    document.write(`<br>{date}日`)    
}
```

**参数传参分两种：**

**1.传数值**，即基本类型的数据，number、string、boolean、null、undefined

**2.传地址**，即把**对象、数组、函数**这些引用类型的数据,object、array、function

```js
var hi =“我想你们了"
function sayHi(str){
	console.log(str)//我想你们了
	}
sayHi(hi)


//传数值，在函数内部，修改了参数的值，不会影响函数外面变量的值
var hi =“我想你们了"
function sayHi(str){
    console.log(str)//我想你们了
    str="我只想睡觉"
	console.log(str)//我只想睡觉
}
sayHi(hi)
console.log(str)//我想你们了



//传地址,当实参是一个引用类型的变量时，则实参和形参之间是共享一个内存地址
//因此，当形参的值改变时，函数外实参变量的值也会改变
var arr=[]
function addName(userArr){
    console.log(arr) // [] -> ["我是刘谦"]
    userArr[0]="我是刘谦"
    console.log(arr) // ["我是刘谦"]
}
addName(arr)
console.log(arr) // ["我是刘谦"]

//arr是一个数组，调用函数时，把arr的内存地址传给userArr，此时，userArr的内存地址，就指向arr
//它们共用一个内存地址，当任何一个数据改变时，另一个也会发生改变
```

![image-20201106112939565](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201106112939565.png)

**函数还可以按有无返回值来分类**

**1.有返回值的函数**

**2.有返回值的函数**

一个函数，如果没有返回值，则默认返回的值是undefined，undefined -> false，有些问题就会出错



**总结：**

无参函数：只能解决单一的一个问题，判断2000-2500的闰年

有参函数：比无参函数可以解决更多的问题，判断任意的闰年，无参，有参函数，在案例中，输出格式都是一样，死板!

无返回值的函数：函数的输出结果不够灵活

有返回值的函数：更加灵活，可以解决任意的闰年，也可以让用户按自己的要求来输出是不是闰年的各种格式



一个优秀的函数，应该有参数，有返回值

在开发中，应该根据实际需求，来设计自己项目中的函数

### 6.4  函数的注释标准

```js
/**
*方法说明
*@method 方法名
*@param {参数类型} 参数名 参数说明 声明函数参数
*@return {返回值类型} 返回值说明
*/

//当函数有参数时，必须使用@param必须与@method搭配使用
//当参数出现以下情况时，使用对应的格式：{参数名}，如果参数有默认值：{参数名=默认值}
//当函数有返回值时，必须使用@return
```

```js
/**
* checkYear()判断是否是闰年,返回true和false. true表示是闰年。
* @method checkYear
* @param {Number} year
* @param {Number} month(如果有多个参数，一行描述一个参数)
* @return{ Boolean} true or false
*/


//当函数有返回值时:
function checkYear(year) {
 //有返回值的函数
	if (year % 4 == 0 && year % 100 ！=0 || year % 400 == 0){
		return true;
	}else {
		return false;
	}
}
var year = 2020;
console.log(checkYear(year))


if(checkYear(year)){
	console.log(year +"是闰年。本命年要穿红》》》")
}else{
	console.log(year +"不是闰年。")
}
```



### 6.5  函数的调用方法

1.直接调用：一般用于没有返回值的函数

```js
//求和的函数
function sum(a,b){
	document.write(`${a}+${b}=${a+b}`)
}
//直接调用函数，在函数内部，把结果输出
sum(30,20)
var sum=sum(30,20)
alert(sum)
```



2.在语句或表达式中调用

```js
function sum(a,b){
	return a+b;
}
//有返回值的函数，只能在语句中或表达式中调用
var a=20,b=30
var temp=sum(a,b);
document.write(`${a}+${b}的和等于${temp}`)
if(sqium(a，b)>100){
	alert("挑战成功")
}
else {
	alert("挑战失败")
}

```



3.函数中调用函数：

3.1 所谓的递归函数就是在函数体内调用本函数。使用递归函数一定要注意，处理不当就会进入死循环。递归函数只有在特定的情况下使用 ，比如阶乘问题

递归函数是在一个函数通过名字调用自身的情况下构成的

3.2 函数之间的相互调用

```js
function checkScore(yw,sx){
	if(sum(yw,sx)==200){
		return 1;
	}else{
		return 0;
	}
}

var isStudy=checkScore(100,90);

	if(isStudy==1){  //双百分
		alert("play")
	}else{  //反之不是双百分
		alert("work")
	}
```

```js
var sum = 0;
function test(num)(
sum:=nums
num--;
if(num==0){
	return sum;
}
	return test(num);
}
document.write(test(5))

```

```js
//正常声明，可以在调用之前或之后声明
function test(){
	alert("test")
}
//把一个匿名函数赋值给变量，叫函数表达式赋值;
var test = function()i
alert( "test")
}
```



### 6.6  arguments

来接收参数

arguments是一个伪数组，只有length可用，Array的其他方法，都不能用，

在调用函数时，所有实参，都存储在argument伪数组中，可以对argument进行循环遍历，

```js
//声明一个最大数的变量，比较中，始终把大数放进max，再用max和后继的数字进行比较，返回max
let arr=arguments;
for(let i=0;i<arr.length;i++){
	if(i==0){
		max=arr[i]
	}
	if(max<arr[i]){
		max=arr[i]
	}
	return max
}
```







## 7  全部变量的与局部变量的理解

**什么是全局变量呢?**

​	全局变量具有穿透性,它可以任何的函数内部使用。

**局部变量**

​	指在函数内部声明的变量，只在函数内部可以使用。

​	形参变量，默认就是局部变量

​	输出时，他先去找函数内部是否有变量，如果没有再去函数外找

```js
//全局变量在函数内被修改，函数使用也被修改了
var a=10;
var sex="aa"
var test=function(){
	//全局变量的a，可以在函数内使用
	console.log("a=",a) //10
	a=100;
	console.log("a=",a) //100
	//在函数内部声明的变量叫做局部变量
	var b=30;
	
	//在函数中，如果没有使用var 声明变量c时，就默认把c声明成全局变量
	c=100
	console.log(c)
	
	//当局部变量与全部变量重名时，在函数中使用变量时，选择使用局部变量
	var sex="bb"
	console.log(sex)
}
test()
console.log("函数外a=",a) //100
//函数内声明的变量，不可以在函数体之外使用
console.log("函数外b=",b)
```





## 8  关于return

一个函数，只允许一个return语句被执行，但是可以通过选择语句

return 后，可以返回任意的数据类型;

写多个return，当函数执行return，就会**返回函数的调用点**，并且停止函数的执行

```js
var test =function(){
console.log(1)
	return 5;//return之后的代码，不被执行
console.log(2)
	return;
console.log(3)
}
//函数的返回值，就返回到调用点，并参与表达式的运算
var a=test()+test() //a=5+5
test()
```

```js
var aa=function(n){
	switch(n){
		case 1:return "ww";break;
		case 2:return "qq";break;
		case 3:return "ii"; //此时，break可写可不写
		default:return "default";break;
	}
}
//此时，函数中可以写多个return
console.log(aa(3))
```





## 9  ES6中的let和var

```js
var i=1 //全局变量或函数内的变量
const PI=3.14 //常量
let j=2 //比var声明的变量，有更明确的局部作用域
//let生命的变量，只在他当前所在{}里有效



for(var i=1;i<=5;i++){
	console. log(i) //12345
}
console.log(i) //6




for(let i=1;i<=5;i++){
	console. log(i) //12345
}
console.log(i) // i is not defined



{
    var name="aa"
}
console.log(name) //可以拿到？不能拿到才对，存疑


{
    let name="ww"
}
console.log(name) //不能拿到

//var规定了，只在函数内声明的变量是局部变量
//let，在ES6中，凡是在{}中声明了变量，只能在{}中使用
//const定义常量，常量定义时，必须指定初始值，不可修改，只能在块作用域有效
//ES5中作用域有:全局作用域、函数作用域。没有块作用域的概念。
//ES6中新增了块级作用域。块作用域由{}包括，if语句和for语局里面的{}也属于块作用域
//let const ,受块作用域的控制

```





## 9  顶层

顶层函数（全局函数）：顶层对象的函数，可以作用于任何对象

| 函数                 | 描述                                                         |
| -------------------- | ------------------------------------------------------------ |
| Number();            | 转换为数值类型                                               |
| parseInt();          | 将字符串转换为整型                                           |
| parseFloat();        | 转换为小数                                                   |
| String()             | 转换成字符串类型                                             |
| Boolean()            | 转换成布尔类型                                               |
| escape(字符串参数)   | 对字符串进行编码                                             |
| unescape(字符串参数) | 对编码的字符串进行解码                                       |
| isNaN()              | 判定一个数能否能转换为数值类型                               |
| isFinite()           | 判断一个数是否为有穷.(将不是有穷的数或不能转换为数值类型的数返回假) |
| eval()               | 将字符串转换为javascript命令执行(必须符合javascript语法规范，否则会出错) |

顶层属性（全局属性）

|      |      |
| ---- | ---- |
|      |      |
|      |      |
|      |      |
|      |      |
|      |      |
|      |      |
|      |      |





## 10  日期

date对象的方法

创建并修改

```js
//1.实例化一个日期对象
let myDate=new Date()
document,write("返回当前电脑的日期时间"+myDate)
//Mon Nov 09 2020 18:26:47 GMT+0800 (中国标准时间)


//2.实例化一个指定日期和对象
//myDate=new Date(year,month,day,hour,minute,second)
myDate=new Date(2020,1,1,20,20,20) //手动修改时间
document,write("返回当前电脑的日期时间"+myDate)


//3.获取日期对象的常用方法
let myDate=new Date() //直接获取当前的时间

//4.getxxx()获取时间值
let year=myDate.getFullYear() //2020 年
let month=myDate.getMonth() //10 月，返回值的数字范围时0-11
let day=myDate.getDate() //9 天数，返回值的数字范围时1-31
let week=myDate.getDay() //1 ，星期 返回的数字范围时0-6，0是星期天

let hours=myDate.getHours() //小时
let minutes=myDate.getMinutes() //分
let seconds=myDate.getSeconds() //秒

let milliSeconds=myDate.getMilliSeconds() //毫秒

document.write(`${year}年${month+1}月${day}日${hours}小时${minutes}分${seconds}秒${milliSeconds}毫秒`)

//当指定日期时，获取月的值，输出时不加一
//获取当前的时间是，月的值，输出时要加一


//5.修改时间 setxxx()
myDate.setFullYear(2018)
myDate.setMonth(1) //只能输入0-11 此时是二月
myDate.setDate(1) //修改某一天，星期几不能修改，没有setDay这个方法
//当修改为2月29日时，浏览器上会显示3月1日，他会自动判断闰年和每个月的天数，多余的天数会加到下一个月去
document.write(`当前最新的修改的日期和时间是${myDate}`)

myDate.setHours(23) //0-23
myDate.setMinutes(30) //0-59
myDate.setSeconds(60) //0-59
myDate.setMilliSeconds(999) //0-999
//超出范围时，会自动往上一单位进一


//6.转化成本地日期和时间的格式字符串的方法
document.write( myDate.toDateString()) //把Date对象的日期部分转换为字符串，Mon Nov 09 2020
document.write("<br >")
document.write( myDate.toTimeString()) //把Date对象的时间部分转换为字符串，18:39:26 GMT+0800 (中国标准时间)
document.write("<br >")
document.write(myDate.toLocaleDateString()) //根据本地时间格式，把 Date 对象的日期部分转换为字符串。2020/11/9
document.write("<br >")
document.write( myDate.toLocaleTimeString()) //根据本地时间格式，把 Date 对象的时间部分转换为字符串。下午6:41:09
document.write("<br >")
document.write( myDate.toLocaleString()) //根据本地时间格式，把 Date 对象转换为字符串。2020/11/9 下午6:41:52


//7.不需要new运算符，就可以得到一个日期和时间对象
var d=Date() //返回当前的日期和时间的字符串，但是不能当日期对象使用，当使用d.getTime()...等方法时，会报错
var d=new Date()

d.getTime() //获取当前的毫秒数


//8.Date.parse(date)
//返回指定日期的毫秒数，跟getTime()方法类似，但是它不需要实例化一个对象
```

```js
//计算两个日期之间的天数差
var d1=new Date(2018,12,31)
var d2=new Date(2020,1,1)

let _times = Math.abs(d1.getTime() - d2.getTime()); //Math.abs(),绝对值
let days = parseInt(_times / (24*60*60*1000)); //366
console.log(days)
```





## 11  字符串对象

### 11.1  创建字符串对象

```js
//1.使用new关键字创建字符串对象
var str = new String('Hello JavaScript')


//2.使用字面量方式创建字符串对象
var str2='Hello JavaScript'
```



### 11.2  length

```js
//3.length,表示字符串对象中字符的数量，或者字符的长度。
console.log(str)  // String {"Hello JavaScript"}
console.log(str2) // 'Hello JavaScript'

console.log(str.length)  //16
console.log(str2.length) //16

console.log(typeof str)  //object
console.log(typeof str2)  //string
```



### 11.3  charAt方法

charAt(index)方法从一个字符串中返回指定的字符

字符串的下标从0 -  string.length - 1这个范围

与数组的下标使用有效范围一样。

```js
//4.charAt(index)： 返回指定位置的字符；
console.log(str.charAt(0))  // "H"
console.log(str.charAt(100))  //""，空字符 
```

```js
var str ="方法从一个字符串中返回指定的字符";
console.log(str.length) //16
let n=0
let myChar = str.charAt(n)
console.log(myChar) //方
```

```js
let index = -1;//表示字符出现的位置
//通过循环，利用charAt()去返回第一个字符，再进行比较，//如果有相等的字符，则把循环变量的值，赋值给index变量,如果没有找到相等的字符，index 默认为-1.

Let str = "abcdefg" ;
let getChar = function( _char，_str){
	let index = -1;
	for(Let i = 0; i< _str.length; i++){
		if(_char == _str.charAt(i)){
			index = i;
			break;
		}
	}
	return index;
}


Let str = "abcdefg";
let getchar = function (_char，_str){…
let char = "x";
var n = getchar(char, str)
if (n -= -1){
	alert("没有找到字符")
}
else {
console.log(`${char}出现在${str}第${n +1}位`)
}


//throw 抛出一个错误信息,中断函数的执行，不会有返回值，因为函数中断了
if ( !checkNumber(a))
	throw new Error("输入的数字不在0-9的范围;"); // throw 抛出一个错误信息if (!checkNumber(b))
if ( !checkNumber(c))
	throw new Error("输入的数字不在o-9的范围;");

```



### 11.4  indexOf方法

```js
//5.indexOf('char'): 返回指定字符串在对象中第一次出现的索引下标的值；（位置）
console.log(str.indexOf('lo')) //3
```



### 11.5  concat方法

```js
//6.concat(其它字符串列表): 返回当前对象的值和参数列表中的字符串拼接后的字符串结果。
let newStr = str.concat("123","456","adbc")
console.log(newStr)  //"Hello JavaScript123456adbc"
```



### 11.6 slice方法

```js
//7.从一个字符串中，返回指定位置和长度的子字符串
//slice(start,end)，返回从start开始，到end结束，但不包括end位的子字符串
//start可以是负值，表示从倒数第几个开始
let temp =str.slice(0,5)

//如果只有start，返回从start开始到字符串结束位的所有子字符串
temp=str.slice(5) // JavaScript
temp = str.slice(-10.13) //JavaScr

console.log(temp) //Hello
```



### 11.7  substring方法

```js
//8.substring(start ,stop):返回从start 开始，到stop结束，但不包括Stop位置的子字符串
//用法与slice(start,end)相同
//start和end不能是负值

temp=str.subString(0,5) //Hello
temp=str.subString(0) //'Hello JavaScript'
temp=str.subString(-10,13) //不能使用负值
```



### 11.8  substr方法

```js
//9.substr(start,length):返回从Start开始，length个数量的子字符串。
temp = str.substr(0,3); //Hel
temp = str.substr(5) //" JavasScript",只有一个参数时，从start到字符串结束的所有子字符串。
temp = str.substr(-5) //"cript"
temp = str.substr(-5,1)//"c”

console.log(temp)
```

```js
function mySubstr(str, start，length){
let newstr="";
for(Let i = start; i< start + length; i++){
newStr+=str.charAt(i)
}
return newstr;
}

console.log(mySubstr("1234567890"，4,3))//567
```



### 11.9  split方法

```js
//10.split(char):把一个字符串，分隔成一个数组
//如果没有char参数，就一个字符分隔成一个数组元素
//如果有，就用这个char参数，就在字符串中相同字符的位置，分割成一个数组元素
str="1232 1234 56 67 2343 234 34 34"
var arr=str.split(" ")
console.log(arr) //["1232", "1234", "56", "67", "2343", "234", "34", "34"]

str="今天天气真好啊去玩吧"
var arr  = str.split("去");
console.log(arr) //["今天天气真好啊", "玩吧"]，没有去


//相反的操作是Array.join(char)
var str1=arr.join(" ")
console.log(str1)
```



### 11.10  trim方法

```js
//11. trim():去掉字符串两端的空格;主要用于表单输入项;
Let username = " 老 蚊 子 ";
username= username.trim() 
console.log(username); //'老 蚊 子',中间的空格没有去掉
```



### 11.11  replace方法

```js
//12.repalce(substr(被替换的), replacement(替换的)):
username = username.replace(" ","-")///老-蚊子，只换了第一个

username = username.replace(/\s/g,"") //老蚊子,使用正则表达式
console.log(username);
```



### 11.12  match方法

```js
//13.stringobject.match(searchvalue)，方法可在字符串内检索指定的值，或找到一个或多个正则表达式的匹配。
//stringobject.match(regexp)
str="123A456A9A9AD787ADFA"

let tempArr=str.match("A") //返回第一次出现的A的下标，["A", index: 3, input: "123A456A9A9AD787ADFA", groups: undefined]
tempArr=str.match(/A/g) //返回所有A，["A", "A", "A", "A", "A", "A"]
tempArr = str.match(/Aasdfas/g) //null

console.log(tempArr);
```



### 11.13  search方法

```js
//14.search(regexp):搜索子串，方法用于检索字符串中指定的子字符串，或检索与正则表达式相匹配的子字符串。
//总是返回 stringObject 的第一个匹配的位置,如果没有找到，就返回-1
str = "123A456A9A9AD787ADFA";
tempArr = str.search('Asdfs');
console.log(tempArr) //-1
```



//声明一个最大数的变量，比较中，始终把大数放进max，再用max和后继的数字进行比较，返回max



### 11.14  indexOf、search、match的区别

```js
str = "123A456A9A9AD787ADFA";
tempArr = str.search('A45');
tempArr1=str.indexOf('A45')
tempArr2=str.match('A45')

console.log(tempArr) // 3
console.log(tempArr1) // 3
console.log(tempArr2) //["A45", index: 3, input: "123A456A9A9AD787ADFA", groups: undefined]
```







## 12  正则表达式

### 12.1  什么是正则表达式

正则表达式是使用特定的符号来描述该组字符串的一种方法。即:正则表达式就是一个字符串模板，其本身也是一个字符串。



### 12.2  创建一个正则对象

```js
var regExp = new RegExp('模式字符串','参数');

var re = /^hello$/;//直接量化方式，建议使用

```



### 12.3  正则表达式的匹配

使用正则表达式的test()进行匹配

正确,返回true

错误，返回false

```js
var reg = new RegExp("IJK")
var str = "abc1223abc";
console.log (reg.test(str)) //false

reg = new RegExp(/IJK/)
str = "abc1223abIJKc";
console.log(reg.test(str))// true

reg = /^IJK$/ //以IJK开头，以IJK结束
str = "abc1223abIJKc"
console.log(reg.test(str)); // false
str = 'IJK'
console.log(reg.test(str));//true
str = 'IJKIJK' //false
str = 'IJKAAIJK' //false
```



### 12.4  修饰符

| 修饰符 | 描述                                                     |
| :----- | :------------------------------------------------------- |
| i      | 执行对大小写不敏感的匹配。                               |
| g      | 执行全局匹配（查找所有匹配而非在找到第一个匹配后停止）。 |
| m      | 执行多行匹配。                                           |



### 12.5  元字符

| 元字符 | 描述                                                         |
| :----- | :----------------------------------------------------------- |
| .      | 查找**单个**字符，除了换行和行结束符。                       |
| \w     | 查找**单词字符**。单词字符包括：a-z、A-Z、0-9、以及下划线    |
| \W     | 查找非单词字符。                                             |
| \d     | 查找数字。0-9                                                |
| \D     | 查找非数字字符。                                             |
| \s     | 查找空白字符。空格，\n，\r。<br/>**空白字符包括:**<br/>空格符 (space character)<br/>制表符 (tab character)<br/>回车符 (carriage return character)<br/>换行符 (new line character)<br/>垂直换行符 (vertical tab character)<br/>换页符 (form feed character) |
| \S     | 查找非空白字符。                                             |
| \b     | 匹配单词边界。                                               |
| \B     | 匹配非单词边界。                                             |
| \0     | 查找 NUL 字符。                                              |
| \n     | 查找换行符。                                                 |
| \f     | 查找换页符。                                                 |
| \r     | 查找回车符。                                                 |
| \t     | 查找制表符。                                                 |
| \v     | 查找垂直制表符。                                             |
| \xxx   | 查找以八进制数 xxx 规定的字符。                              |
| \xdd   | 查找以十六进制数 dd 规定的字符。                             |
| \uxxxx | 查找以十六进制数 xxxx 规定的 Unicode 字符。                  |

```js
//  .元字符
var reg = /^a.$/
var str = "abc";
var str2 = "2a1"
var str3 = "a2";
var str4 = "a\n" // \n 换行的转义符
     
console.log(reg.test(str));  //false
console.log(reg.test(str2)); //false
console.log(reg.test(str3)); //true
console.log(reg.test(str4)); //false
```

```js
//  \w元字符
var reg = /^a\w$/
 
var str = "ab";
var str2 = "2a1"
var str3 = "a2";
var str4 = "a\n"
var str5="a_"
var str6="a "
 
         
console.log(reg.test(str));  //true
console.log(reg.test(str2)); //false
console.log(reg.test(str3)); //true
console.log(reg.test(str4)); //false
console.log(reg.test(str5)) //true
console.log(reg.test(str6)); //false
```

```js
//  \d元字符
var reg = /^a\d\w$/
 
var str = "ab";
var str2 = "2a1"
var str3 = "a2";
var str4 = "a6b"
 
         
console.log(reg.test(str));  //false
console.log(reg.test(str2)); //false
console.log(reg.test(str3)); //false
console.log(reg.test(str4)); //true
```

```js
// \s元字符 

var reg = /^a\s$/
 
var str = "ab";
var str2 = "2a1"
var str3 = "a ";
var str4 = "a\n"
 
console.log(reg.test(str));  //false
console.log(reg.test(str2)); //false
console.log(reg.test(str3)); //true
console.log(reg.test(str4)); //true 
```

```js
//  \S元字符
 var reg = /^a\S$/
 
var str = "ab";
var str2 = "2a1"
var str3 = "a ";
var str4 = "a\n"
 
console.log(reg.test(str));  //true
console.log(reg.test(str2)); //false
console.log(reg.test(str3)); //false
console.log(reg.test(str4)); //false 
```



### 12.6  方括号

| 表达式             | 描述                               |
| :----------------- | :--------------------------------- |
| [abc]              | 查找方括号之间的任何字符。         |
| [^abc]             | 查找任何不在方括号之间的字符。     |
| [0-9]              | 查找任何从 0 至 9 的数字。         |
| [a-z]              | 查找任何从小写 a 到小写 z 的字符。 |
| [A-Z]              | 查找任何从大写 A 到大写 Z 的字符。 |
| [A-z]              | 查找任何从大写 A 到小写 z 的字符。 |
| [adgk]             | 查找给定集合内的任何字符。         |
| [^adgk]            | 查找给定集合外的任何字符。         |
| (red\|blue\|green) | 查找任何指定的选项。               |

```js
// []
var reg = /^a[IJK]b$/
var str1 = "aIb";
    
console.log(reg.test(str1)); //true
    
reg = /^a[a-zA-Z0-9\w]b$/
str2 = "a2b";
str3 = "aZb";
str4 = "a_b";
console.log(reg.test(str2)); //true
console.log(reg.test(str3)); //true
console.log(reg.test(str4)); //true
```

```js
//  [^] 
reg = /^a[^IJK]b$/
var str1 = "aIb";
         
console.log(reg.test(str1)); //false
  
str1 = "a8b" 
console.log(reg.test(str1)); //true

```



### 12.7  量词

n表示任意的字符或元字符；有些表示是一个语法糖；

| 量词   | 描述                                        |
| :----- | :------------------------------------------ |
| n+     | 匹配任何包含**至少一个** n 的字符串。       |
| n*     | 匹配任何包含**零个或多个** n 的字符串。     |
| n?     | 匹配任何包含**零个或一个** n 的字符串。     |
| n{X}   | 匹配包含 **X 个 n** 的序列的字符串。        |
| n{X,Y} | 匹配包含 **X 至 Y 个 n** 的序列的字符串。   |
| n{X,}  | 匹配包含**至少 X 个 n** 的序列的字符串。    |
| n$     | 匹配任何结尾为 n 的字符串。                 |
| ^n     | 匹配任何开头为 n 的字符串。                 |
| ?=n    | 匹配任何其后紧接指定字符串 n 的字符串。     |
| ?!n    | 匹配任何其后没有紧接指定字符串 n 的字符串。 |

```js
// n+:
//  至少一个'a'
var reg = new RegExp(/^a+$/);
var str = "a"
var str2 = "aaaaaaaaaaaa"
var str3 = "baaaaa"
console.log(reg.test(str));  // true
console.log(reg.test(str2)); //true
console.log(reg.test(str3));  // false
```

```js
// n*;零个或多个 'a'
var reg = new RegExp(/^_a*_$/);
var str = "_a_"
var str2 = "_aaaaaaaaaaaa_"
var str3 = "__"
var str4 = "_x_"
console.log(reg.test(str));  // true
console.log(reg.test(str2)); //true
console.log(reg.test(str3)); // true
console.log(reg.test(str4));// false 
```

```js
// n?: 零个或一个 'a'
var reg = new RegExp(/^_a?_$/);
var str = "_a_"
var str2 = "_aaaaaaaaaaaa_"
var str3 = "__"
var str4 = "_x_"
console.log(reg.test(str));  // true
console.log(reg.test(str2)); //false
console.log(reg.test(str3)); // true
console.log(reg.test(str4));// false
```

```js
//  n{x}: a{5} 匹配固定的数量的字符
var reg = new RegExp(/^_a{5}_$/);
var str = "_a_"
var str2 = "_aaaaaaaaaaaa_"
var str3 = "__"
var str4 = "_aaaaa_"
console.log(reg.test(str));  // false
console.log(reg.test(str2)); // false
console.log(reg.test(str3)); // false
console.log(reg.test(str4));//  true 
```

```js
//  n{x,y}: a{5,8} 匹配固定的数量范围的字符

var reg = new RegExp(/^_a{5,8}_$/);
var str = "_a_"
var str2 = "_aaaaaaaa_"
var str3 = "_aaaaaaaaaaaa_"
var str4 = "_aaaaa_"
var str5 = "_x_"
console.log(reg.test(str));  // false
console.log(reg.test(str2)); // true
console.log(reg.test(str3)); // false
console.log(reg.test(str4));//  true
console.log(reg.test(str5));//  false 
```

```js
// n{x,}; a{5,}  表达匹配5个以上的字符a  ；>=5
var reg = new RegExp(/^_a{5,}_$/);
var str = "_a_"
var str2 = "_aaaaaaaa_"
var str3 = "_aaaaaaaaaaaa_"
var str4 = "_aaaaa_"
var str5 = "_x_"
console.log(reg.test(str));  // false
console.log(reg.test(str2)); // true
console.log(reg.test(str3)); //  true
console.log(reg.test(str4));//  true
console.log(reg.test(str5));//  false
```

```js
//例子

var tel = "13258231798"
var reg = /^1[37859][0-9]\d{8}$/;

console.log(reg.test(tel)) //true
tel = "14258231798"
console.log(reg.test(tel)) //false

regId = /^(\d{18})$|^(\d{17}[xX])$/ ;
userId = "511000199910101234"
console.log(regId.test(userId)) // true
        
        
userId = "51100019991010123x"
console.log(regId.test(userId)) //true

userId = "251100019991010123x"
console.log(regId.test(userId)) //false
```



window.confirm(),弹出一个选择框，点击确定，返回true，点击取消，返回false

```js
let n=window.confirm("是否要继续？是，点击‘确定’")
if(n==true){
	saveMoney()
}
```







## 13  DOM

### 13.1  关于DOM

DON是文档对象模型(Document object Model)，由w3c组织提出的标准。dom 1级，dom 2，，，，dom5级

DOM是一种XML文档的解析标准。

DOM的原理是将XML/XHTML文档装入内容，并以节点的形式解析为一棵节点树。

DOM提供相应的API，可以对节点树进行增删改查。

利用DOM可以让JavaScript对网页中的元素进行控制，实现动态网页的功能。

DOM是关于如何获取、修改、添加或删除HTML元素的标准



### 13.2  理解DOM树

每一个标签就是一个DOM节点，html标签都是元素节点，最上层的节点是document

![image-20201110104706822](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201110104706822.png)





### 13.3  节点

#### 13.3.1  节点类型

nodeType

根据w3BC的HTMIL DOM标准，HTML文档中的所有内容都是节点:

整个文档是一个文档节点
       —>        document节点:代表整个文档,也代表根节点

每个HTML元素是元素节点       —>        Element:元素节点

HTML元素南的文本是文本节点       —>        Text:文本节点

每个HTML标签属性是属性节点

Attr:属性节点
注释是注释节点
       —>        comment:注释节点



#### 13.3.2  访问节点

1. document.getElementById(id)

   兼谷所有浏见路,挺存便用。
   id和别的元素的name不能相同，这是IE的存在的问题

2. document.getElementsByClassName (class)

  通过元素的class取得节点**集合(伪数组）,不带小数点**
  注意哪怕页面只有唯一一个名为myclass的元素，也会返回一个集合

3. document.getElementsByTagName(TagName)

  返回指定元素的称的元素节点集合document.getElementsByTagName(*)能得到所有元素节点集合

4. document.getElementsByName(name)

  按name属性值获取元素节点集合。

5. document.queryselect(）,可以传任何方式

   document.queryselectorAll(），返回一个由全部节点组成的列表



```js
//变量，对象，数组，函数都是小驼峰命名法；常量全部大写；类、原型对象是大驼峰合法
//let objectDiv
let oDiv=document.getElementById("div1") //返回唯一一个DOM对象

//三种输出方法，最好使用控制台，一般查看对象，数组，函数，都在浏览器的控制输出。F12,--console.
console.log(oDiv) 
alert(oDiv)
document.write(oDiv)
```

```js
var arrTitle = document.getElementsByclassName("title")
console.log(arrTitle) //HTMLCollection(2)[h1.title， h3.title]，伪数组对象

//获取为数组中，某一个对象：应该使用下标变量的方法来获取
console.log(arrTitle[0]);
console.log(arrTitle[1]);
console.log(arrTitle[4]); //如果没有这个下标，undefined
```

```JS
//document.getElementsByTagName(TagName):通过标签名称来获取DOM元素的集合。(返回一个伪数组)
let arrLi = document.getElementsByTagName("li");
console.log(arrLi) //HTMLCollection(4)[li， li，li，li]
//使用下标变量来获取、操作对象;
```

```JS
//document.getElementsByName(name)—按name属性值获取元素节点集合(列表)
let arrDesc = document.getElementsByName("myDesc")
console.log(arrDesc); //NodeList[p]，可以使用foreach(),entries() ,keys(), values()
```

```js
var oDiv=document.querySelector("#Div1")
console.log(oDiv);
var oTitle = document.queryselector(.title")
console.log(oritle);
var oli = document.queryselector("1i")
console.log(oliy);

//只会返回匹配的第一个DOM节点对象


var arr = document.querySelectorAl1("ttdiv1")
console.log(arr);//NodeList [divttdiv1]
arr = document.queryselectorAl1("li")
console.log(arr);
arr = document.queryselectorAll(“body li")
console.log(arr);  //NodeList(4)[li，li， li，li]|


//和1-4不同的是，第五种传参数时，要带标识，如#，.
```



#### 13.3.3  常用的节点属性和方法

1. childNodes:所有子节点，包括元素子节点、文本子节点;
2. children:元素子节点
3. hasChildNodes(),判断是否有子节点,true/false

```js
// let ul = document.getElementsByTagName("ul");//HTMLCollection(1)
// ul[0]，表示第一节ul元素节点;
let ul = document.getElementsByTagName("ul"")[0];//直接使期下标，就表示获取第一个ul元素节点;
console.log(ul)


//hasChildNodes(),判断是否有子节点  true，false
console.log(ul.haschildNodes())//true表示有子节点

let arrLi = ul.childNodes;//获取所有子节点对象;console.1og
console.log(arrLi);//NodeList(9)[text，li ,text，li, text，li, text，li, text]
//text节点来源于标签中的回车换行符号，形成的空白符号

arLi.forEach((item，i, arr)=>{
	console.log(itemt"----"+ i + "---"+arr)
    console.log(item.nodeName)
    console.log(item.nodeType)
    console.log(item.nodeValue)
});



let arrLiElement = ul.children;
console.log(arrLiElement); //[ NHITMLcollection(4)[li，li，li，li]

for(Let i = o; i< arrLiElement.length; i++){
	console.log(arrLiElement[i ].nodeName)//LI				
    console.log(arrLiElement[ i].nodevalue) // null			
    nullconsole.log(arrLiElement[i].nodeType) //1
}

```

```js
forEach语法：
Array.forEach((数组元素变量，索引号，数组别名)=>{
})
```

**domNode. nodeName节点名称**

**domNode.nodeType节点类型**

**domNode. nodevalue节点值**



不同的DOM节点，这三个属性的值，是有差别的



**nodeName:节点名字（节点名/属性名/text)。**

​	元素节点的 nodeName与标签名相同

​	属性节点的nodeName与属性名相同

​	文本节点的nodeName始终是#text

​	例:输出第一个子节点名字—document.body.childNodes[0].nodeNamenodevalue



**文本节点的值（nodevalue/null)**。

​	元素节点的 nodevalue是 undefined或null

​	属性节点的nodevalue是属性值

​	文本节点的nodevalue是文本本身

​	例:输出第一个子节点值—document.body.childNodes[0].nodevaluenode



**Type :节点类型（1/2/3)**

​	元素节点:1 ;

​	属性节点:2 ;

​	文本节点:3；

​	根节点（document） 9

​	firstchild,lastchild:第一个/最后一个节点。

了解每种节点的nodeName，nodeType,nodeValue



4. 上一个兄弟节点

```js
var oP=document.getElemtntsByName("mydesc")[0];

//由于中间有一个回车换行符，要写两次previousSibling，才可以拿到h1这个元素节点
var oh1=oP.previousSibling.previousSibling
//previousElementSibling，上一个元素兄弟节点
oh1=oP.previousElementSibling
console.log(oh1)

```



5. 下一个兄弟节点

```js
//下一个兄弟节点：nextSibling
var oh3.oP.nextSibling.nextSibling
//下一个元素兄弟节点：nextElementSibling
oh3=oP.nextElementSibling
console.log(oh3)
```



6. 父节点

```js
var oParent=oP.parentNode
console.log(oParent)
```



7. 根节点

8. 子节点： childNodes, children, firstChild,lastChild; 



#### 13.3.4  通过todoList去掌握节点创建、添加、删除

```html
<div id="todoList">
	<div class="inputBox">
		<input type="text" id="addText" value="">
		<button type="button" onclick="addTask();">添加任务</button>
	</div>
	<ul class="task-list">
		<li>学习HTML <button onclick="deleteTask()">删除</button></li>
		<li>学习CSS <button onclick="deleteTask()">删除</button></li>
        </ul>
</div>


<script>
	 // es5:
	function addTask() {
        // alert("添加");
        // 1. 获取输入框的值；
               var oAddText = document.getElementById("addText");  // input 节点对象
               var textValue = oAddText.value;  // 获取INPUT标准属性节点的值；
               // alert(textValue)
   
		// 2. 创建一个新的LI节点对象；
   
               var oLi = document.createElement("li");  // 创建出来的节点对象，现在存放在内存中，没有挂载到页面 
               console.log(oLi);
   
   
		// 3. 获取父节点：ul
               var oUl = document.getElementsByClassName("task-list");  // [ul]
   
		// 4. 在父节点上，添加一个子节点到末尾。
               oUl[0].appendChild(oLi)
   
	
        
        
		// 1. 获取输入框的值；
            var oAddText = document.getElementById("addText");  // input 节点对象
            var textValue = oAddText.value;  // 获取INPUT标准属性节点的值；
            // alert(textValue)

		// 2. 获取父节点：ul
            var oUl = document.getElementsByClassName("task-list");  // [ul]
		// 3. 创建一个新的LI节点对象；

            // 创建一个元素节点li:
            var oLi = document.createElement("li");  // 创建出来的节点对象，现在存放在内存中，没有挂载到页面 
            // console.log(oLi);

		// 4. 创建一个文本子节点：
            // oLi.appendChild(textValue)  // 字符串，不能自动转换成文本节点；
            // 错误提示：Failed to execute 'appendChild' on 'Node': parameter 1 is not of type 'Node'.

            // document.createTextNode(文本内容或变量);
            var oText = document.createTextNode(textValue);
            // console.log(oText.nodeValue)
            // console.log(oText.nodeName)
            // console.log(oText.nodeType)

		// 5. 把文本子节点，添加到oLi 元素节点中；（是在内存中完成添加的）
            oLi.appendChild(oText)  // <li>xxxxx</li>

		//  6. 在父节点上，添加一个子节点到末尾。
            oUl[0].appendChild(oLi)
			
        }
		// es6:
        // const addTask = ()=>{

        // }
    
    
    
    
    
    function newAddTask(){
           // 1. 获取输入框的值： 
           var oInput = document.getElementById("addText");
           var valueInput = oInput.value;

            // 2. 创建一个Li子节点：
            var oLi = document.createElement("li");
            oLi.innerHTML = `${valueInput} <button onclick="deleteTask()">删除</button>`

            // console.log(oLi) // <li>ssss <button onclick="deleteTask()">删除</button></li>

            // 3. 获取父节点UL，并把li 添加到 ul; 
            var oUl = document.getElementsByClassName("task-list");
            oUl[0].appendChild(oLi);

            // 4. 清除输入框的值；
            oInput.value = ""

       }

       function deleteTask(){
           alert("完成了一个任务")
       }
</script>
```

添加子节点： 

父节点对象.appendChild(子节点对象)  ： 括号中，只能是一个子节点对象。！！！     





删除子节点：

父节点对象.removeChild(子节点对象)



#### 13.3.5  获取文本节点的值

1. 双标签中的文本节点

   firstchild和lastchild用于获取元素节点中的文本节点

```js
<h2>我的儿子</h2>


var oh1=document.getElementsByclassName("title")
var oText = oh1[e].firstchild
var oText = oh1[e].lastchild;
console.log(oText) //我的儿子，这个文本节点

console.log(oText.nodeName);//#text
console.log(oText.nodeType);//3
console.log(oText.nodevalue);//我的儿子
```



2. 单标签后的文本节点

```js
var oSex = document.getElementsByName("sex");
console.log(osex[0])

//nextsibling:下一个兄弟节点:
var oTextSex = oSex[e].nextsibling;
console.log(oTextSex)
```



#### 13.3.6  属性节点的操作

元素节点对象.attributes 属性，返回该元素节点对象上**所有的属性节点的“集合”**。

元素节点对象.getAttributeNode（html标签**属性名**）,获取"指定"的属性节点对象；

元素节点对象.getAttribute("属性名"); 返回元素节点对象对应HTML标签属性名的值；

```js
// 获取最终样式：多个选择器和样式表重叠后，最后网页上显示的样式；

// JS只能获取最终样式中CSS属性的值,不能修通过该属性来修改；


        // const _getEndStyle = () => {
        function _getEndStyle () {

            let oDiv1 = document.getElementById("div1");
            let w;
            console.log(oDiv1.currentStyle) 
            // 谷歌中，undefined
            //  IE , []
            if (oDiv1.currentStyle == undefined) {
                /*DOM谷歌，ie9及以上支持*/
                w = document.defaultView.getComputedStyle(oDiv1, null).width;
            } else {
                /*IE 6- 8 兼容*/
                w = oDiv1.currentStyle.width
            }

            console.log(w)  //100px  => 400px;
```



#### 13.3.7  节点的替换、插入、克隆

1. **替换节点**

   父元素节点.replaceChild(新节点 ，旧节点)

   如果新节点是直接从页面中获取的，那么在替换时，会把这个节点剪切，再执行替换。

   在使用是时，要考虑以上这个问题。是剪切页中的节点，还是重新创建一个新节点。

   元素节点相关的属性和方法：
   https://www.w3school.com.cn/jsref/dom_obj_all.asp

2.  **插入节点**

   在指定子节点**之前**，插入新的子节点：

   父节点.insertBefore(新子节点,已经存在的子节点)   
   如果新节点是直接从页面中获取的，那么在替换时，**会把这个节点剪切，再执行插入**。
   **必须要传2个参数**！！！
   如果只有一个，提示错误如下: 
   Failed to execute 'insertBefore' on 'Node': 2 arguments required, but only 1 present.

3. **克隆节点**

   cloneNode() 方法有一个参数（**true 或 false**）。该参数指示被复制的节点是否包括原节点的所有属性和子节点。

   目标节点.cloneNode(boolean);

   原节点，还存在于页面中，不会被剪切。

```js
let cloneNode = target.cloneNode(false); 
// 只克隆标签自己，带有标签属性； <li id="target"></li>
let cloneNode = target.cloneNode(true); 
// 克隆标签自己和所有元素内容；（标签所有属性，所有子元素 和每个子元素的元素内容）
// <li id="target">hello <span>123</span></li>
```





### 13.4  事件

#### 13.4.1  事件的概述

**什么是事件？**

事件(Event):当我们与浏览器中Web页面进行某些类型的交互时，事件就发生了。

事件可能是用户在某些内容上的点击、鼠标经过某个特定元素或按下健盘上的某些按键，事件还可能是Web浏览器中发生的事情，比如说某个Web页面加载完成，或者是用户滚动窗口或改变窗口大小。说白了，事件是文档或浏览器中发生的特定交互瞬间

**事件有什么作用？**

事件处理模型最早在IE4.0浏览器里提供支持。
Netscape将其源码贡献给Mozilla开源社区后，这种浏览器的事件模型—直遵循DOM标准在发展。
后来的浏览器，Opera,Safair都遵循DOM标准。



#### 13.4.2  事件流

描述的是从页面中接收事件的顺序，或者说是事件在页面中的传播顺序，事件流意味着页面上不止—个元素可响应相同的事件

如∶当我们点击页面上的按钮时，实际上我们是点击了按钮，以及按钮的容器  -> 整个页面。

**不同的浏览器有不同实现事件流的方法:**

事件冒泡(IE，谷歌等),从html结构内部向外部依次传递事件

事件捕获(NETSCAPE),从html结构从外部依次向内部传递事件

DOM事件流(FIREFOX),先按捕获方式传递事件，再达到目标时，触发目标上的事件，然后再按冒泡方式传递事件

**DOM事件流的三个阶段:**

1.捕获阶段

2.目标阶段

3.冒泡阶段

在BOM中，最外面的几个大的对象

捕获:window 》 document 》html 》body 》div1 》div2 》div3

冒泡：div3 》div2 》div1 》 body 》html 》document 》Window



#### 13.4.3  事件类型

1. **鼠标事件** 

   单击（mousedown,mouseup）

   双击(mousedown,mouseup,click,mousedown,mouseup,click)

2. **键盘事件** 

   keydown(按下),keypress（按着不放）,keyup（弹起）

3. **HTML事件**

   load 加载,unload  卸载
   ,abort 中断 ,error 错误
   select  选择

   change  `<select>` 表单项的值发生改变时

   submit  `<form>` 提交表单时

   reset`<form>`    重置表单时

   resize  window 改变大小时

   scroll  window,页面中的元素内容滚动时

   focus  表单项，获取焦点

   blur    表单项,失去焦点

**keydown/keyup和keypress的区别！**

charCode属性： keydown,keyup，支持所有的键盘字符；

charCode属性： keypress支持普通键盘字符（不包括keypress本身不支持的键盘字符）。

SHIFT- 16,CTRL-- 17,ALT--18,WINDOW--91,
 A-Z : 65-90 ; a-z:  97-122; 0-9  :48-57



#### 13.4.4  事件处理函数

响应某个事件的函数就叫事件处理程序（也叫事件处理函数、事件句柄）。

事件处理程序的名字以"on"开头，因此click事件的事件处理程序就是onclick,load事件的事件处理程序就是onload。

传统事件处理程序指派方法
被广泛支持

现代事件处理程序指派方法。
只被现代浏览器支持。
浏览器之间存在不兼容的问题。



#### 13.4.5  传统事件的绑定

1.在html结构中，使用on开头的标签属性来绑定事件

```js
<div id="div3" onclick="alert( 'div3' )">
	div3
</div>

```

2.给dom节点对象，添加一个on开头的事件属性，把一个函数，赋值给dom对象的事件属性：

```js
document.body.onclick = function({
	alert( "body")
}

```



#### 13.4.6  事件对象获取方式

1. **直接绑定在html标签上**

   **只能通过window.event来获取事件对象**

```js
<button onclick="test(1)">click 1</button>

 // 1. 直接在HTML标签上，绑定事件：只能通过window.event来获取事件对象；
function test(event) {
	console.log(event) //undefined  // 1

	let event2 = window.event || event;

	console.log(event2)//MouseEvent {isTrusted: true, screenX: 158, screenY: 145, clientX: 37, clientY: 23, …
}
```

2. **通过函数来绑定**

```js
<button id="btn2" type="button">click 2</button>


// 2. 通过编程方式来添加事件：通过函数表达式来绑定事件；
let oBtn2 = document.getElementById("btn2")

oBtn2.onclick = function (event) {
	console.log(event) //MouseEvent {isTrusted: true, screenX: 212, screenY: 142, clientX: 91, clientY: 20, …}
}

//如果函数不需要传参数时，还可以通过第一个形参变量来表示事件对象；
function (a){
	console.log(a) //event;   
	console.log(arguments[0]) //event;  
}
```

3. **当函数中有参数时**

```js
<div id="div3" onclick="test(this)"></div>

oBtn2.onclick = function (event){
//但是在匿名函数中， 第一个形参变量，就是事件对象。
	test(123) //由于test有参数传递，所有第一个参数，不会是事件对象，在test函数中，只能通过window.event来拿事件对象。
}



// 如果是把一个具名函数赋值给事件属性，则函数后面不能写().
// test();就表示调用test函数；
// oBtn2.onclick = test2;
function test2(nubmer, event) {                                                     
	console.log(nubmer) // 123
	console.log(event) // 当有参数传递时，就不能直接拿到事件对象； undefined

	// 有参数时，只能通过window.event来获取事件对象
	let event2 = window.event || event;
	console.log(event2)//MouseEvent {isTrusted: true, screenX: 158, screenY: 145, clientX: 37, clientY: 23, …
 }
        
// 传统事件2中，调用函数时，如果要传参数：
oBtn2.onclick = function () {
	test2(123)
}



function test3 (number){
	let event2 = window.event;
	console.log(number)  //12341234
	console.log(event2);  //MouseEvent {isTrusted: true, screenX: 158, screenY: 145, clientX: 37, clientY: 23, …
}
oBtn2.onclick = function(event){
	console.log("匿名函数中的事件对象：",event)
	test3(12341234)
}

// 取消事件绑定：
oBtn2.onclick = null;
```

4. **小结**

```js
//小结： 传统事件的绑定时，后面绑定的事件，会替换前面绑定的事件；一个事件只能绑定一个函数；

   a = 1; 
   a = 3;
   a = 10;
   console.log(a) //10
//同样的道理：
   obtn.onclick = ()=>{}
   obtn.onclick = function(){}
   obtn.onclick = function(){
       test311();
       test3();
       test2(0)
}
```



#### 13.4.7  现代DOM事件绑定方法

1. **DOM添加事件**

```js
<div id="div1">国庆庆大假</div>


var div1= document.getElementById("div1");
div1.addEventListener("click",showText,true);
//参数1：事件名称，不带”on”；
//参数2：函数名, 不带”()”; 
//参数3：布尔值；
//true, 捕获；
//false,冒泡。
```

2. **IE添加事件**

```js
<div id="div1">国庆庆大假</div>


var div1= document.getElementById("div1");
div1.attachEvent("onclick",showText);
//参数1： 事件名称， 带”on“；
//参数2： 函数名, 不带”()”。
//IE 只支持冒泡事件流，所有没有第三个参数。
```

3. **小结**				

`addEventListener()`, 不兼容IE6/7/8 其它高版本都支持。
绑定事件时，函数名，都不能带()；

```js
//兼容性写法：
if (document.attachEvent == undefined) {
    oBtn3.addEventListener("click",test1,true);
} else {
    oBtn3.attachEvent("onclick",test1);
}
```



#### 13.4.8  取消事件绑定

1. **传统取消事件绑定**

   `oBtn2.onclick = null;`

2. **DOM的事件取消**

   括号中的参数，必须和添加方法中的参数一致。

   不能对使用匿名函数来绑定的事件，进行清除！！！

    DOM事件，可以支持一个事件上，绑定多个函数！

    清除时，必须一个一个的清除绑定的函数

```js
if (document.attachEvent == undefined) {
    oBtn3.removeEventListener("click",test1,true);
} else {
    oBtn3.detachEvent("onclick",test1);
}
```



#### 13.4.9  阻止默认事件

`window.event.preventDefault()`

```html
<!-- 阻止a标签的默认跳转事件 -->
<a href="../day021评讲/lx.html" onclick="test()">访问练习1</a>
    
<div>
	<!-- <form action="../day021评讲/lx.html" onsubmit="return true;"> -->
	<!-- onsubmit事件只能写在<form>上， onreset事件只能写在<form>上  -->
	<!-- 使用return 返回一个boolean值给onsubmit事件句柄（事件处理函数、事件处理程序）；事件句柄根据返回值，判断是否要提交表单的数据。  -->   
	<form action="../day021评讲/lx.html" onsubmit="return checkForm();" onreset="return true;">
		<input type="text" value="default">
		<button type="submit">submit</button>
		<button type="reset">reset</button>
	</form>
</div>



<script >
	let checkForm = ()=>{
	// return false;
		return true ; // 表单验证通过；
	}

	let test = ()=>{
		let e = window.event;
		// e.returnValue=false 如果设置了该属性，它的值比事件句柄的返回值优先级高。把这个属性设置为 fasle，可以取消发生事件的源元素的默认动作。
		e.preventDefault() //通知浏览器不要执行与事件关联的默认动作
	}
</script>
```



#### 13.4.10   阻止 事件的传递：

 阻止冒泡：`stopPropagation()`,不再派发事件

```js
if(e.stopPropagation)// 不兼容IE 678
  e.stopPropagation(); //dom 阻止冒泡
else{
  e.cancelBubble=true; //IE阻止冒泡
}
```





## 14  BOM

### 14.1  BOM概述

BOM是浏览器对象模型。（Browser object Model)仅是 JavaScript实现的一部份，没有相关标准。

**BOM能做么?**

操作浏览器窗口

提供导航对象

提供定位对象

提供跟屏幕相关对象

提供对cookie的支持

**dom级别**

dom1级 2级 3级。。。5级，只是没有申请国际化的标准，但是各浏览器厂商默认是去支持的



### 14.2  BOM体系结构

![image-20201113113554680](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201113113554680.png)



### 14.3  BOM体系结构-window对象

WINDOW对象是BOM的顶层(核心)对象，所有对象都是通过它延伸出来的，也可以称为WINDOW的子对象

**由于WINDOW是顶层对象，因此调用它的子对象时可以不显示的指明WINDOW对象**

例如下面两行代码是一样的∶

```js
document.write("www.dreamdu.com")
window.document.write("Www.dreamdu.com")
```



#### 14.3.1  window对象的基本属性及方法

##### 14.3.1.1  获取浏览器页面实际宽高

`document.documentElement.clientWidth`可视宽度

`document.documentElement.clientHeight`可视高度



##### 14.3.1.2  window其他基本属性

**浏览器距离屏幕左上角的水平或垂直位置**

`window.screenLeft`

`window.screenTop`

`window.screenX`

`window.screenY`

**浏览器窗口文档显示区的宽高，不包含工具栏**

`window.innerWidth`

`window.innerHeight`

innnerWidth、innerHeight 是可视区加上滚动条的距离，clientWidth、clientHeight不包括滚动条

**浏览器窗口的宽高，包含工具栏**

`window.outerWidth`

`window.outerHeight`

是浏览器的轮廓的高宽



##### 14.3.1.3  打开和关闭窗口

`window.open("url","新窗口名字","新窗口特性");`

新窗口的特性设置:left,top,width,height,toolbar,resizeable,status,location
window.open()

返回一个新的window对象，需要对该对象进行赋值；

```js
<button id="btn1">关闭当前窗口</button>
<button id="btn2">open 一个新的窗口</button>
<button id="btn3">关闭 一个新的窗口</button>
 
let obtn2 = document.getElementById("btn2");

//新窗口赋值
let newWindow = null;

//打开一个新的窗口
obtn2.onclick = () => {
	newWindow =window.open("http://www.baidu.com","baidu","width=400,height=400")
}

//关闭这个新窗口
obtn3.onclick = ()=>{
	newWindow.close();
}


//关闭当前窗口: 
obtn1.onclick = () => {
	window.close();
}
```



##### 14.3.1.4  输入输出

`window.alert("确认框");`

`window.confirm(“警告框”); ` 选择是返回true， 否返回false

`window.prompt(“提示信息”);` OK返回输入的字符串，取消返回null

注意：对话框的样式不可更改，对话框是模式窗口



### 14.3.2  Timing定时器

`setTimeout(function, 时间)`：等待指定的一个时间，执行函数一次

`setInterval(function, 时间)`：每间隔一个时间，执行一次函数

每一个定时器，都会返回一个定时器的ID；1，2，3，4，。。。

清除定时器时，
可以通过:

 `clearTimeout(timer)`、`clearInterval(timer)`



**定时器输出节点：**

```html
<body>
    <ul>
        <li>第0次</li>
    </ul>

    <button type="button" onclick="startAdd()">开始添加节点</button>
    <button type="button" onclick="stopAdd()">停止添加节点</button>
    
    
    <script>
        var ul = document.getElementsByTagName("ul")[0];
        var timer = null;
        var i = 1;

		//1.传统方法，让setTimeout实现循环输出
        // for (let i = 0; i < 10; i++) {

        //     timer = window.setTimeout(function () {
        //         let li = document.createElement("li");
        //         li.innerHTML = "第" + i + "次"
        //         ul.appendChild(li)
        //     }, 1000 * i)
        //     document.write(timer) // 1,2,3,...,10
        //     第四次时清除定时器
        //		if(i === 4){
        //         clearTimeout(timer)
        //     }
        // }


        const startAdd = () => {
            // timer = window.setTimeout(addLi, 1000);
            timer = window.setInterval(addLi2,1000);
        }

        const stopAdd = () => {
            window.clearTimeout(timer)
            // 清除定时器时，建议和设置用相同的方法来清除；
            // window.clearInterval(timer);
        }

        /* 
        const addLi = () => {
            let li = document.createElement("li");
            li.innerHTML = "第" + i + "次"
            i = i + 1;
            ul.appendChild(li);
            // 在函数内部，再通过setTimeout方法来调用自己；实现每间隔多少时间来执行一次b函数；达到和setInterval()相同的效果。
            timer = window.setTimeout(addLi, 1000);
        } */
    
    
        const addLi2 = () => {
            let li = document.createElement("li");
            li.innerHTML = "第" + i + "次"
            i = i + 1;
            ul.appendChild(li);
            //不需要在函数内部，再添加定时器！！
        }
    </script>
</body>
```



**定时器计算倒计时：**

```html
<body>
    <!-- 2021,8,17,20,0,0 -->
    <div id="time">
    </div>

    <script>
        // 在页面加载完成时，执行定时器
        window.onload = () => {
            window.setInterval(showTime, 1000)
        }

		// 如果数字小于10，就在前面补0；
        const addZero = (n) => {
            n = n < 10 ?  '0' + n : n;
            return n;
        }
		// 显示倒计时：
        const showTime = () => {
            // 目标日期
            let d1 = new Date(2021, 8, 17, 20, 0, 0);
            // console.log(d1)
            // 当前日期：
            let now = new Date();

			// 计算两个时间之间毫秒数之差；
            let n = d1 - now;
            // console.log(n) // 112348234
			// 求天数的部分
            let days = parseInt(n / (24 * 60 * 60 * 1000));
            // console.log(days);
            // 求小时的部分
            let hours = parseInt(n % (24 * 60 * 60 * 1000) / (60 * 60 * 1000))
            // console.log(hours);
            // 求分钟的部分
            let minutes = parseInt(n % (60 * 60 * 1000) / (60 * 1000))
            // console.log(minutes);
            // 求秒的部分
            let seconds = parseInt(n % (60 * 1000) / (1000))
            // console.log(seconds);

			// 修改节点的值：
            let timeNode = document.getElementById("time");
            timeNode.innerHTML = `距离2021成都大运会还有 ${days}天${addZero(hours)}时${addZero(minutes)}分${addZero(seconds)}秒 `

        }
    </script>
</body>
```



**定时器修改图片路径**

```html
<body>
    <div>
        <img src="img/ba1.jpg" alt="">
    </div>

    <script>
        window.onload = function () {
            let arrImg = [
                "img/ba1.jpg",
                "img/ba2.jpg",
                "img/ba3.jpg",
                "img/ba4.jpg",
                "img/ba5.jpg"];
            let i = 0;
            let img = document.getElementsByTagName("img")[0];
            window.setInterval(function () {
                i++;
                if (i >= 5) i = 0;
                img.setAttribute("src", arrImg[i]);
            }, 2000);
        }
    </script>
</body>
```



### 14.3.3  history

**属性**

length: 表示有几个历史记录。

**方法**

`window.history.go(-1)` 移动到指定的历史记录点，当前页面位置索引值为0，上一页就是-1，下一页为1

`window.history.back()`类似用户在浏览器的工具栏上点击返回按钮

`window.history.forward()`类似用户在浏览器的工具栏上点前进按钮



### 14.3.4  location

`window.location` 对象用于获得当前页面的地址 (URL)，并把浏览器重定向到新的页面。

`window.location` 对象在编写时可省略window 这个前缀

1. 获取当前页面url
           

   console.log（location.href）;

2. 跳转到新页面
          

   location.href =“index.html”; 	

   location.href =“http://www.baidu.com”;   //打开外部地址必须加上http

**location对象属性**

| 属性     | 描述                                          |
| -------- | --------------------------------------------- |
| hash     | 设置或返回从井号 (#) 开始的 URL（锚）。       |
| host     | 设置或返回主机名和当前 URL 的端口号。         |
| hostname | 设置或返回当前 URL 的主机名。                 |
| href     | 设置或返回完整的 URL。                        |
| pathname | 设置或返回当前 URL 的路径部分。               |
| port     | 设置或返回当前 URL 的端口号。                 |
| protocol | 设置或返回当前 URL 的协议。                   |
| search   | 设置或返回从问号 (?) 开始的 URL（查询部分）。 |

**location对象方法**

| 属性      | 描述                                                |
| --------- | --------------------------------------------------- |
| assign()  | 加载新的文档。 要新增加历史记录条数；               |
| reload()  | 重新加载当前文档。                                  |
| replace() | 用新的文档替换当前文档。 不会增加新的历史记录条数； |



### 14.3.5  navigator

navigator对象包含当前浏览器的详细信息，所有浏览器都支持该对象,可以通过该信息识别系统版本，浏览器内核

`window.navigator`

`navigator.userAgent`

```html
<script>
        console.log(window.navigator)


        // ie 11: Trident
        // appVersion"5.0 (Windows NT 6.1; WOW64; Trident/7.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; .NET4.0C; .NET4.0E; rv:11.0) like Gecko"
        // userAgent:"Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; .NET4.0C; .NET4.0E; rv:11.0) like Gecko"



        //  chrome: AppleWebKit/Chrome
        // appVersion: "5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/86.0.4240.183 Safari/537.36"
        // userAgent: "Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/86.0.4240.183 Safari/537.36
       


        // firefox: Firefox
        // 5.0 (Windows)
        // userAgent: "Mozilla/5.0 (Windows NT 6.1; Win64; x64; rv:69.0) Gecko/20100101 Firefox/69.0"

</script>
```



**每一款主流浏览器的内核名:**

1. **Trident**内核代表产品Internet Explorer，又称其为IE内核。Trident（又称为MSHTML），是微软开发的一种排版引擎。使用Trident渲染引擎的浏览器包括：IE、傲游、世界之窗浏览器、Avant、腾讯TT、Netscape 8、NetCaptor、Sleipnir、GOSURF、GreenBrowser和KKman等。

2. **Gecko**内核代表作品Mozilla FirefoxGecko是一套开放源代码的、以C++编写的网页排版引擎。Gecko是最流行的排版引擎之一，仅次于Trident。使用它的最著名浏览器有Firefox、Netscape6至9。

3. **WebKit**内核代表作品Safari、Chromewebkit 是一个开源项目，包含了来自KDE项目和苹果公司的一些组件，主要用于Mac OS系统，它的特点在于源码结构清晰、渲染速度极快。缺点是对网页代码的兼容性不高，导致一些编写不标准的网页无法正常显示。主要代表作品有Safari和Google的浏览器Chrome。

4. **Presto**内核代表作品OperaPresto是由Opera Software开发的浏览器排版引擎，供Opera 7.0及以上使用。它取代了旧版Opera 4至6版本使用的Elektra排版引擎，包括加入动态功能，例如网页或其部分可随着DOM及Script语法的事件而重新排版。



### 14.3.6  screen

`window.screen` 对象包含用户屏幕的信息。

`screen.width` 属性返回以像素计的访问者屏幕宽度。

`screen.height` 属性返回以像素计的访问者屏幕的高度。

`screen.availWidth` 属性返回访问者屏幕的宽度，以像素计，减去诸如窗口工具条之类的界面特征，显示以像素计的屏幕可用宽度。

`screen.availHeight` 属性返回访问者屏幕的高度，以像素计，减去诸如窗口工具条之类的界面特征，显示以像素计的屏幕可用高度。



### 14.3.7  form对象

`document.forms`返回一个form标签的集合，伪数组

**拿到form对象：**

`forms[0]`

`forms['form的name']`，一个文档中，form标签上，name的值，应该是唯一的

` document['form的name']  || document.form的name`

**拿一个对象的属性的值**

`object = {0:1234,1:324}`

`object.属性名`  => object.0; // Uncaught SyntaxError: Unexpected number

`object['属性名'] `=> object['0']

**获取表单域中的对象的方法**

```js
let forms = document.forms; //获取表单伪数组
    

let formLogin = forms["form-login"]; //获取伪数组中name名为form-login的表单域
       
console.log(formLogin.elements); //HTMLFormControlsCollection(3) [input, input, button, username: input, password: input]
    

let elements = formLogin.elements; //表单域中的对象

```

`var frm = document.getElementById("form1");`dom

`var field1 = frm.elements[0]; `通过下标来获取表单域对象，第一个表单域，可用于遍历表单域

`var field1 = frm.elements["name"];`通过name的值来获取表单域对象，得到名为name的表单域

`var field1 = frm.name;`直接用名称得到表单域

`var field1 = frm[“my name”];`得到name值有空格的表单域

`var field1 = frm[0];`得到第几个表单元素



`form.submit()`,模拟提交表单的功能；  对应的触发事件：  onsubimt, 没有触发。

`form.reset()`  ,模拟重置表单的功能； 对应的触发事件：  onreset，会触发。

表单默认的 submit 按钮，会触 发 onsubimt, 

表单默认的 reset 按钮，会触 发 onreset。 



### 14.3.8  非隐藏表单字段的共有属性和方法

`disabled`,是否可用，当设置为不可用时，表单的值不会随表单提交

`readOnly`,只读。当设置之后，表单的内容不可改变，表单的值会随表单提交。只能用于文本框

`form`,得到表单

`blur()`,使表单域失去焦点。触发 onblur 事件

`focus()`,使表单得到焦点。触发onfoucs 事件；

`blur`事件：失去焦点时触发，并调用onblur()函数。

`focus`事件：得到焦点时触发，并调用onfocus()函数。



### 14.3.9  标单的验证

**验证的时间点：**

错误发生前：边输入边验证，keydown，keyup，keypress

错误发生时：blur，change

错误发生后：submit，提交表单，submit（），ajax（）

```html
<body>
    <button type="button" id="resigter">注册</button>
    <!-- r所有的模态框 ，都是做为 body 标签的直接子元素成在的！ -->
    <section id="modal1">
        <div id="formDiv">
            <div id="close">X</div>
            <!-- <form action="login.html" onsubmit="return checkForm();"> -->
            <form action="login.html">
                <div>
                    <input onkeyup="checkUserName(this)" type="text" name="username" placeholder="input a username">
                    <span class="ts-default">请输入8-16位的字母、数字</span>
                </div>
                <div>
                    <!-- <input onchange="checkPwd(this)" type="text" name="password1" placeholder="input a password"> -->
                    <input type="text" name="password1" placeholder="input a password">
                    <span class="ts-default">请输入8位密码 包括字母、数字</span>
                </div>
                <div>
                    <input type="text" name="password2" placeholder="input a password">
                    <span class="ts-default">请输入8位密码 包括字母、数字</span>
                </div>
                <div>
                    <button type="submit">register</button>
                    <button type="button" id="login">register</button>

                </div>
            </form>
        </div>
	</section>
    
    
    
    
    <script>
// 错误发生时的验证：
        let oIptPwd1 = document.forms[0][1];
        console.log(oIptPwd1)

        oIptPwd1.addEventListener("change",function(){
            console.log(this) // input 对象;
            let value = this.value;
            console.log(value)
            let  reg = /^\w{8}$/
            if(reg.test(value) == true){
                this.nextElementSibling.innerHTML = "good1!";
                this.nextElementSibling.className = "ts-ok";
                // console.log(this.form[2]);
                this.form[2].focus()
            }else{
                this.nextElementSibling.innerHTML = "error!";
                this.nextElementSibling.className = "ts-fail";
                this.focus();
            }
        }, true);



// 错误发生前的验证：
     const checkUserName = (domNode)=>{
        console.log(domNode);
        let v = domNode.value;
        let reg = /^[a-zA-Z0-9]{8,16}$/;

        if(reg.test(v) == true){
            domNode.nextElementSibling.innerHTML = "ok";
            domNode.nextElementSibling.className = "ts-ok"
        }else{
            domNode.nextElementSibling.innerHTML = "error!";
            domNode.nextElementSibling.className = "ts-fail"
        }
     }



        // 错误发生后，验证表单：
        function checkForm() {
            let submitState = true; //允许提交表单
            let myForm = document.forms[0];
            let userIpt = myForm[0];  //用户名输入框
            // console.log(userIpt)
            let pwdIpt1 = myForm[1];
            let pwdIpt2 = myForm[2];

            let userIptValue = userIpt.value;
            let pwdIpt1Value = pwdIpt1.value;
            let pwdIpt2Value = pwdIpt2.value;

            let reg = /^\w{8,16}$/ //用户名规则
            if (reg.test(userIptValue) == true) {
                userIpt.nextElementSibling.innerHTML = "OK";
                userIpt.nextElementSibling.className = "ts-ok";
            } else {
                userIpt.nextElementSibling.innerHTML = "Fail";
                userIpt.nextElementSibling.className = "ts-fail";
                submitState = false;
            }

            reg = /^\w{8}$/; //密码规则
            if (reg.test(pwdIpt1Value) == true) {
                pwdIpt1.nextElementSibling.innerHTML = "OK";
                pwdIpt1.nextElementSibling.className = "ts-ok";
            } else {
                pwdIpt1.nextElementSibling.innerHTML = "Fail";
                pwdIpt1.nextElementSibling.className = "ts-fail";
                submitState = false;
            }

            // reg = /^\w{8}$/; //密码规则
            if (reg.test(pwdIpt2Value) == true && pwdIpt1Value == pwdIpt2Value) {
                pwdIpt2.nextElementSibling.innerHTML = "OK";
                pwdIpt2.nextElementSibling.className = "ts-ok";
            } else {
                pwdIpt2.nextElementSibling.innerHTML = "Fail";
                pwdIpt2.nextElementSibling.className = "ts-fail";
                submitState = false;
            }

            return submitState;

        }


        // 不通过submit类型的按钮来提交表单：
        let loginBtn = document.getElementById("login")
        loginBtn.onclick = ajaxSubmit;  //不是立即执行函数，所以不能带有（）;事件绑定，只绑定函数名！

        function ajaxSubmit() {
            let submitState = true; //允许提交表单
            let myForm = document.forms[0];
            let userIpt = myForm[0];  //用户名输入框
            // console.log(userIpt)
            let pwdIpt1 = myForm[1];
            let pwdIpt2 = myForm[2];

            let userIptValue = userIpt.value;
            let pwdIpt1Value = pwdIpt1.value;
            let pwdIpt2Value = pwdIpt2.value;

            let reg = /^\w{8,16}$/ //用户名规则
            if (reg.test(userIptValue) == true) {
                userIpt.nextElementSibling.innerHTML = "OK";
                userIpt.nextElementSibling.className = "ts-ok";
            } else {
                userIpt.nextElementSibling.innerHTML = "Fail";
                userIpt.nextElementSibling.className = "ts-fail";
                submitState = false;
            }

            reg = /^\w{8}$/; //密码规则
            if (reg.test(pwdIpt1Value) == true) {
                pwdIpt1.nextElementSibling.innerHTML = "OK";
                pwdIpt1.nextElementSibling.className = "ts-ok";
            } else {
                pwdIpt1.nextElementSibling.innerHTML = "Fail";
                pwdIpt1.nextElementSibling.className = "ts-fail";
                submitState = false;
            }

            // reg = /^\w{8}$/; //密码规则
            if (reg.test(pwdIpt2Value) == true && pwdIpt1Value == pwdIpt2Value) {
                pwdIpt2.nextElementSibling.innerHTML = "OK";
                pwdIpt2.nextElementSibling.className = "ts-ok";
            } else {
                pwdIpt2.nextElementSibling.innerHTML = "Fail";
                pwdIpt2.nextElementSibling.className = "ts-fail";
                submitState = false;
            }

// 全部验证通过时，通过调用 submit()来提交表单： 
            if(submitState == true){
                myForm.submit()
            }
        }
    </script>
</body>
```





## 15  冒泡排序

大数下沉，小数上浮,把第一个数比较后面所有数，得到一个最小值，再把第二个数比较后面的数，得到第二个最小值，以此类推，直到排序完成

```JS
let arr = [2, 56, 23, 9, 1]
const writeNumber = (n) => {
for (let i = 0; i < arr.length; i++) {
	if(i == n){
		document.write("<div class='border-black'>" + arr[i] + "</div>")
	}else{
		document.write("<div>" + arr[i] + "</div>")
	}
  }
document.write("<br>")
}
writeNumber();

const maoPao = (a) => {
// 外循环：控制总共要比较的轮数：
	for (let i = 0; i < a.length - 1; i++) {
	//  i = 1
	// 内循环
	// 控制每轮比较的次数
		for (let j = i + 1; j < a.length; j++) {
		// j = 2,3,4
		// 如果第一个数，比第二个数大，就交换数据；后续是用当前较小的这个数，继续和后面的数组元素的值进行比较。满足条件，继续交换数据 ，直到内循环结束，这一轮比较就结束，得到一个最小的数据。
			if (a[i] > a[j]) {
				let temp = a[i];
				a[i] = a[j];
				a[j] = temp;
			}
		}
		 writeNumber(i)
	}
}
maoPao(arr)
/* 
N个数，比较N-1轮；每一轮比较 N-当前轮数；
*/

```







## 16 js面向对象

之前学的都是面向过程编程

### 16.1  JavaScript的对象编程基础

Javascript是基于原型的面向对象语言，即每一个对象都有一个原形，对象从原形中继
i
承属性和方法

JavaScript ( ES5)中只有对象，没有类的概念。

JavaScript通过函数(function)来创建对象。

JavaScript的函数也是一种对象。

JavaScript的对象可以在运行时动态添加属性，属性可以是**原始类型，引用类型，函数**。

1. 原始类型：

   number

   string

   null

   undefined

   boolean

   symbol

2. 引用类型

   Object

   Array

   Date

   RegExp

   Function

在JS中，除了原始类型，其它的都是对象类型了，对象类型和原始类型不同，**原始类型存储的是值**，**对象类型存储的是地址（指针）**。当你创建了一个对象类型的时候，计算机会在内存中帮我们开辟一个空间来存放值，但是我们需要找到这个空间，这个空间会拥有一个地址（指针）。

**面向对象的特征：**

1. **抽象**：把生活中的实际的物体，它们相同特征抽取出来，提炼成一个共同的物种的类，这个类，在我们开发中，就是一个对象（类）
2. **封装**：应用一种思维模式来设计你的函数
3. **继承**：让具有相似性的对象或类，去继承更高级的对象或类的属性与方法，或者理解为子继承父的特征，如子类继承父类的特性，或者其他对象去继承某一个类的特征
4. **多态**：指对象在应用中，同一个方法（接口的实现），但是在不同实际对象中，表现不一样

**为什么在编程中要使用对象：**

比如，要用变量来描述一个完整的人，就需要太多的变量和函数

我们没有办法在编程中，用这么多的变量来进行程序的开发和维护，因此才会有对象这个概念的产生

每一个对象都有属性和方法

属性就是对象的特征

方法就是对象的功能

### 16.2  对象的创建

三种创建的方式：new object()、构造函数、工厂方式

1. 字面量一个对象

   属性名可加引号可不加

```js
var obj={name:"张三",age:12,height:180,eat:function(text){alter(this.name+'吃'+text)}}

let uname=obj.name

obj.eat('饭')
```

方法可传参数,可调用自己本身this



2. new object（参数）

   如果给定值是null或undefined，将会创建并返回一个空对象

   如果传进去的是一个基本类型的值，则会构造其包装类型的对象

   如果传进去的是引用类型的值，仍然会返回这个值，经他们**复制**的变量保有和源对象**相同的引用地址**

```js
var obj1=new Object() //实例化一个空对象
console.log(obj1)  //{} //引用类型

obj1=new Object(obj) //如果参数是一个引用类型，则是复制引用的内存地址，所以obj和obj1一模一样
cosole.log(obj1) //跟上面obj完全一样，它继承了上面obj的属性和方法

console.log(obj1==obj) //ture

```

```js
var obj2=new Object("hello world")
console.log(obj2) //{hello world},字符串
console.log(new String("hello world"))

//Object是js系统中，最顶层一个原型对象
```



3. Object.assign()

   Object.assign(）方法用于将所有可枚举属性的值从一个或多个源对象分配到目标对象。它将返回目标对象。

```
var obj3=Object.assign(obj,obj2)
console.log(obj3) //合并obj和obj2
console.1og(obj3[0]) //使用[]来操作属性
console. log(obj3.name) //使用.来操作属性和方法

obj3.eat(“糖"); //操作方法
obj3['eat']("米"); //操作方法
```

[]中，可以是一个变量或者字符串常量

```js
let uname="li"
obj.uname => 把uname变量当成obj的属性来看，肯定可能出现错误
obj[uname] => 把li当成obj的属性来看
```



4. Object.create()

```js
let obj5=Object.create(obj)
console.log(obj5) //{}，{},_proto_指向了obj.
//把obj对象作为obj5._proto_(原型对象)，因此，通过继承的特性，obj5可以使用obj的属性和方法
obj5.eat("饭")
console.log(obj===obj5._proto_) //ture
```



### 16.3  Object动态创建属性和方法

```js
obj5.sex =“男”
obj5.say = function { alert("hello")}
obj5.say();
console.log(obj5.sex) //"男"
```



### 16.4  Object删除属性和方法

`delete obj.属性名`

`delete obj.方法名`

**销毁一个对象:**

`obj = null` 让变量不去引用对象就可以了，利用js系统销毁机制，实现对象的销毁，节约内存空间



### 16.5  构造函数

es5，没有类的概念，只有函数

有一种函数叫构造函数，**函数名首字母大写**的（大驼峰命名法）

在函数内部，使用this关键字，来绑定一些属性和方法

通过new运算符来实例化构造函数，得到一个新的实例对象

在定义一个构造函数时，**不能使用ES6箭头函数**

ES6中箭头函数中的this，不是指向实例化对象，而是指向当前函数所在的上下文环境

```js
function Person(){
	this.name="aa"
}
var obj=new Person(); //=右边的是对象，把内存的地址给obj
console.log(obj.name) //"aa"
```

```js
//把人类的特征抽取出来，写成一个构造函数，表示为人类的一个对象
function Person(){
	this.name =“张三";
    this.age = 18;
	this.sex =“男";
	this.eat = function(text){
	alert(this.name +”正在吃“+text)
	}
}

let ajiao=new Person()
ajiao.name="ajiao"
ajiao.age="18"
console.log(ajiao.name)//方法较麻烦，需要每次都改值




//通过传参数来写
function Person(name,age,sex){
    console.log(this) //this指向当前实例,Person{}当前构造函数的实例对象
    this.name = name;
    this.age = age;
    this.sex = sex;
	this.eat = function(text){
	alert(this.name +”正在吃“+text)
	}
}
let ajiao =new Person(“吴刚，22，“男”)
ajiao.eat("aa")

let zz=new Person("zz",22,"女")
console.log(zz.name)

//构造函数中，当使用new运算符时，this指向实例化对象

Person("ww",23,"男") //当把构造函数当普通函数调用时，this指向window对象，就相当于window.Person("ww",23,"男")
window.x =1;
console. log(x)// 1
y =2;
console.log(window.y)//2
```



#### 16.5.1  构造函数上的原型函数

prototype



#### 16.5.2  call、apply、bind的继承

只会继承方法？和属性，不会继承原型链上的方法

**call()、apply()、bind() 都是用来重定义 this 这个对象的！**

call 、bind 、 apply 这三个函数的第一个参数都是 this 的指向对象，第二个参数差别就来了：

call 的参数是直接放进去的，第二第三第 n 个参数全都用逗号分隔，直接放到后面 **obj.myFun.call(db,'成都', ... ,'string' )**。

apply 的所有参数都必须放在一个数组里面传进去 **obj.myFun.apply(db,['成都', ..., 'string' ])**。

bind 除了返回是函数以外，它 的参数和 call 一样。

当然，三者的参数不限定是 string 类型，允许是各种类型，包括函数 、 object 等等！