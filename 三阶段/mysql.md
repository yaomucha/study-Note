# mysql

## 1  数据库概述

### 1.1  层次模型

- 单个记录以父子关系（传统

- ![image-20201204094515061](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204094515061.png)

- 网状模型（传统

- 关系模型

  传统的缺点

  ![image-20201204094606565](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204094606565.png)

![image-20201204095005988](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204095005988.png)

![image-20201204095529129](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204095529129.png)

主键唯一性

表中，一行就是一条数据（记录）：他由多个列（字段）的属性构成，而列当中，会有一个属性列是一个实体的唯一标志，一般这种列叫主键。

表与表之间建立关系，一般都是通过主键、外键的链接来建立关系的



表与表的关系：

1. 一对一关系  1:1

   ![image-20201204100058126](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204100058126.png)

2. 一对多关系  1:m

3. 多对多关系   m:n

   ![image-20201204100915734](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204100915734.png)

![image-20201204100727350](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204100727350.png)

<img src="C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204101030054.png" alt="image-20201204101030054" style="zoom:100%;" />

现今流行新的数据库：NOSQL 非关系型数据库、mongeDB等。理解为对象型数据库

![image-20201204102056856](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204102056856.png)

不能用来开发应用程序

dba认证





### 2  DDL定义数据库及表的操作

![image-20201204103937695](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204103937695.png)



创建一个简单的数据库

以分号来表示一条sql命令的结束 

```sql
CREATE DATABASE stu;
```

创建一个数据库后，手动去修改一下字符集，都设置为utf-8，避免表中出现乱的中文字符



删除数据库

```SQL
DROP DATABASE stu;
```



创建并连接到stu库

```sql
CREATE DATABASE stu;
use stu;
```



表的创建

![image-20201204105150006](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204105150006.png)

```sql
CREATE TABLE s_stuInfo(
	s_id INT PRIMARY KEY,  --列和列之间用逗号分隔，不能是中文逗号,添加主键约束
	s_name CHAR(30) NOT NULL,--不能为空，必须输入
	s_age TINYINT,
	s_sex CHAR(1) DEFAULT "男", --默认为男、"1"0
    s_cardId CHAR(18) UNIQUE,添加一个唯一的约束，因为一个QQ号，不可能归属于多个
	s_date DATE --最后一个列不能加逗号,日期类型不需要给长度
);
```

定义int，float，double，date，datetime时，不需要写长度

char（n），varchar（n），decimal（m，d）需要写长度 

数据类型：

1. 整数数据类型：
   1. INT,4个字节
   2. TINYINT 0-255 小型的整数

2. 浮点数类型：

   ![image-20201204110155705](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204110155705.png)

m是总位数，d为小委属，m必须大于d，小数点和负数的‘-’符号不包括在m中

字符串类型：

1. CHAR 

2. VARCHAR

   char(30),存储时，站30个字符长度，固定长度

   hello：它任然赞30个字符长度的空间

   varcahr(30),存储时，最大是30时，当小于30时，就按实际数量存储，非固定长度

   hello：赞5个字符串长度的空间

   字符串类型（）中的数字，表示当前列可储存的字符串数量最大长度是多少



日期类型：

1. DATE
2. DATETIME



删除表

```sql
DROP TABLE s_stuInfo；
```



sql 不分大小写



为什么要保证数据完整性：

为了防止垃圾数据的产生,从而影响数据库的执行效率!!!

通过控制数据的可靠性，准确性，就可以控制数据的完整性



如何控制，通过表的约束，来控制

![image-20201204113907412](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204113907412.png)

保证每行所带标签的实体能互相区别

实现方法：

1. 主键约束

   主键是表中的一到多个列，**主键列不能为空，也不能重复**

   

2. 唯一约束

   唯一约束是指给定列的所有值必须唯一，**该列在表中每一行的值必须唯一,不能重复**。

   它和主键约束的区别在于该列**可以为空**，并且可以在一张表中给多个列设置唯一约束。



为什么要域完整性

实现方法：

1. 非空约束：not null

2. 默认约束：default

   mysql没有检查约束：check



引用完整性

为什么要引用完整性

实现方法：

外键约束

auto_increment,主键的自增长

decimal()?

外键：关联主表主键，表示这条数据是哪一个学生的·成绩

做外键，因此它类型必须和主表中的主键的类型一致

什么是外键，什么是外键约束

有外键约束的表，必须要先创建主表，再创建从表

当主表被外键约束时，是不能直接删除的

从表插入、修改的外键数据，必须是主表主键列中有的数据

主表当有外键约束时，主键列的数据，不能修改和删除                                                                                                                                                                                                                                   



自定义完整性

![image-20201204145103376](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204145103376.png)

![image-20201204145126598](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204145126598.png)



![image-20201204145302239](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204145302239.png)



插入数据

insert into <表名>(<列名列表>)

values（<值列表>)

插入一条数据

全字段插入

```
INSERT INTO `S_STU` (``)
```

![image-20201204153802082](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204153802082.png)

整形不需要引号，字符串和日期类型需要引号

针对普通自动增长（null）和默认值（null）以及允许为null的字段进行插入

主键列不能为空，虽然也是自增长，但是不能使用null

全字段插入时的简写

insert into 表名

value（）,必须在括号中，写上所有列的值

![image-20201204154451444](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204154451444.png)



指定字段的插入，默认、为空的可以不出现字段列表中，自增长也可以不出现在字段列表中

![image-20201204154710065](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204154710065.png)

自增长列，可以使用null来替换

自增长的列，默认的列，允许为null的列，可以不出现在指定的列表名中



同时插入多行数据

![image-20201204155955354](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204155955354.png)





更新数据

update可以更新、修改数据

update 表名 set 列1=值1，列2=值2，。。。。where 条件表达式

没有没有where，就是修改所有的行的数据

如果有，就是修改满足条件的行的数据

还可以进行简单的表达式计算

![image-20201204160746237](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204160746237.png)

![image-20201204160910263](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204160910263.png)

![image-20201204160946251](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204160946251.png)



删除某一列的值

如果要删除某列的值，只需要将该列设置为null即可，。。。

![image-20201204161142123](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204161142123.png)



删除

delete，删除表中的数据，不是删除表结构

语法：delete from 表名 [where 条件表达式]

一般可以有一个日志的回滚

![image-20201204161815446](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204161815446.png)

条件的构成，列名 = 值 and 列2 > 值2 or 列3！=值3.。。。>,<,=,!=,<=,>=,between ..and..

删除表中所有数据

truncate table 表名

有外键约束时，不能直接把主表的所有数据都删除

先删从表的数据，再删除主表的数据，或者先删除外键约束，再删除主表数据

**delete和truncate的区别：**

DELETE会记录日志，意味着删除后的数据还可以恢复，但是效率低。

TRUNCATE不会记录日志，删除后的数据不能恢复，但是效率高。

TRUNCATE不能用于有外键约束引用的表。



drop table 是直接把表结构和表中数据全部删除





查询

查询分类：

1. 投影操作

   指定查询结果中能显示哪些列

   全字段投影：

   查看表中所有数据

   ```sql
   select * from `stu`
   ```

   查看某一些列

   

   ![image-20201204163605451](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201204163605451.png)

   

   表前缀：一般再多表联合查询时，会使用表前缀

   ![image-20201207100603495](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207100603495.png)

   通过前缀指明是哪张表的列

   。。。。

   

   投影时简单的计算

   ![image-20201207100624242](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207100624242.png)

   去掉重复的行的数据

   ![image-20201207100637878](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207100637878.png)

   distinct后面只有一个列，多个列无效

   

   指定行数的数据

   ![image-20201207100837720](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207100837720.png)

   数据库中分页

   前端需要把查询第几页，每页显示几条的数据传递给后台

   后端返回，总条数，当前页，每页显示几条，查询结果

   

   

2. 选择操作

   ![image-20201207101003012](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207101003012.png)

   1. 了解select from where的执行顺序

   2. 简单的条件过滤

      ![image-20201207101112554](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207101112554.png)

      

      and、or多条件应用

      ![image-20201207102256650](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207102256650.png)

      between 21 and 24       ===>        >=21and<=24

      判断一个集合:

      条件为真时，就投影该行数据

      全都不等于，就为假，过滤掉当前行的数据

      not in的时候： 

      ![image-20201207103905266](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207103905266.png)

      ![image-20201207102110245](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207102110245.png)

      ![image-20201207102434415](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207102434415.png)

      模糊查询：

      通配符：

      “__” 表示任何单个字符

      “%” 表示包含零个或多个任意字符

      

      ![image-20201207102455124](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207102455124.png)

      ![image-20201207102815094](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207102815094.png)

      ​    ![image-20201207103106108](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207103106108.png)

      只要限制了数量，就必须使用“__”

      没有数量限制时，就使用“%”

      ![image-20201207103243982](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207103243982.png)

      ![image-20201207103419745](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207103419745.png)

      ![image-20201207103722000](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207103722000.png)

      

3. 排序操作

   1. 单列排序

      ![image-20201207104728031](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207104728031.png)

      ![image-20201207104741011](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207104741011.png)

   2. 多列排序

      先按第一列的条件排序，如果第一列中有相同的值时，按第2列的要求来排序，如果第二列有相同值时，按第三列的要求来排序，以此类推

      ![image-20201207105028344](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207105028344.png)

   3. 升序（默认）ASC

   4. 降序DESC

![image-20201207104515914](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207104515914.png)

​		按中文拼音的先后顺序来显示：CONVER(列名 USING 编码名)

![image-20201207105515071](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207105515071.png)

![image-20201207105532186](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207105532186.png)



![image-20201207105749325](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207105749325.png)



4. 管理操作

![image-20201207093956559](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207093956559.png)







复制表结构和数据

```sql
CREATE TABLE 新表名 SELECT * from 旧表名;
```

只复制表的结构

```SQL
CREATE TABLE 新表 SELECT * FROM 旧表 WHERE 1=0;
```

备份、导入数据库



5. 统计操作

   如果要做统计的操作,就必须使用聚合函数:

   聚合函数的分类

   COUNT:统计行数量

   SUM:获取单个列的合计值

   AVG:计算某个列的平均值

   MAX:计算列的最大值

   MIN:计算列的最小值



count（计算规范 ：*，all，distinct）

*：所有行，包括有null值的行

all：所有非空值的行    count（all 列名），all可以省略

distinct：不统计空值的行数，返回唯一值的行，去掉重复的数据行    count（distinct 列名）

![image-20201207112749410](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207112749410.png)

![image-20201207112935855](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207112935855.png)

先去掉重复的数据，再统计数量



![image-20201207113254509](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207113254509.png)

如果时多个sql语句同时执行，后端返回的是一个二维数组

—[[4],[1],[1]]   ===>     [0] [0]=4;  [1] [0]  =1,  [2] [0] =1

双循环来处理二维数组

![image-20201207113841232](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207113841232.png)





sum

sum（all 列名）：所有非空值的行中列的数据的总和

sum（distinct 列名）：所有非空值的行中，去掉重复的列的数据的总和

![image-20201207114014251](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207114014251.png)

![image-20201207114023810](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207114023810.png)

all 可写可不写

![image-20201207114317691](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207114317691.png)





AVG

AVG（all 列名）：所有非空值的行中列的数据的平均值

AVG（distinct 列名）：所有非空值的行中，去掉重复的列的数据的平均值

对非空值进行求平均

![image-20201207114707776](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207114707776.png)

![image-20201207114842411](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207114842411.png)

非空去重复

四舍五入取小数点后几位

ROUND（number，小数点后几位）

![image-20201207114950697](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207114950697.png)





max、min

没有

![image-20201207115228716](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207115228716.png)





可以同时执行多个聚合函数，把结果投影出来

![image-20201207115554703](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207115554703.png)







6. 分组

   ![image-20201207141118704](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207141118704.png)

分组时，一定要保证投影的结果时有效的

1. 聚合函数所在列
2. group by 后面的列名，必须出现再select子句后面
3. 其他都属于无关列，即无效数据



多个分组的列： 多个列的条件同时满足的，分为一组，再对这一组数据进行统计

![image-20201207141442363](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207141442363.png)

按业务员所在地和性别进行显示业务员的人数

![image-20201207141752337](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207141752337.png)

 ![image-20201207142050203](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207142050203.png)

having过滤

只能用于group by 子句后，分组之后

用于分组、统计后的数据进行过滤

where时在分组前进行过滤，having是分组后进行过滤

![image-20201207142415466](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207142415466.png)

having count 》=2也可以，可以用别名

![image-20201207142956384](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207142956384.png)







SQL执行顺序：

![image-20201207143122206](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207143122206.png)

select

from

where

group by

having

order by

limit





![image-20201207143420578](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207143420578.png)

![image-20201207143643725](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207143643725.png)







什么是表连接

原理？

![image-20201207160036232](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207160036232.png)

如何得到有效数据

使用on关键字

![image-20201207160626286](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20201207160626286.png)

一般是根据主外键的关系来查询数据





表连接分类：

1. 内连接：表1 join 表2 on 表1.列1=表2.列2  join

   inner这个关键字可以省略

   内连接只保留条件为真的行的数据，条件为假的行的数据都过滤掉

   内连接的另一种简单的语法

   

2. 外连接：

   是指不管有没有匹配，被定义了外连接的表数据都要出啊现在结果中

   没有商品的类型，没有显示出来？

   外连接：

   

   到底是把哪一张表的数据都投影出来？那么这张表，就是外连接表

   如果用left join来连接表，这张表就应该放在右边

   qq

   内连接表和外连接表的区别：

   1. 内连接表只投影出满足条件的数据行
   2. 外连接时，不仅投影出满足条件的数据行们还要把被指定为外连接表的不满足的数据行全部投影出来，在投影结果中，其他列以null值来表示

3. 自连接

   是内连接的一种

    