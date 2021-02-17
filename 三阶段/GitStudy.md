# Git

yaomucha

1538678381@qq.com

abcd3146036



yaomu-tea

abcd3146036

## 目的

借助github托管项目

## 基本概念

#### 仓库（Repository)

仓库的意思，即你的项目，你想在GitHub上开源一个项目，那就必须要新建一个Repository ,如果你开源的项目多了，你就拥有了多个Repositories 

#### 收藏(Star）

仓库主页star按钮，意思为收藏项目的人数，在 GitHub上如果你有一个项目获得100个star都算很不容易了!

#### 复制克隆项目(Fork）

这个不好翻译，如果实在要翻译我把他翻译成分叉，什么意思呢？你开源了一个项目，别人想在你这个项目的基础上做些改进，然后应用到自己的项目中，这个时候他就可以Fork 你的项目〈打开项目主页点击右上角的fork按钮即可〉，然后他的GitHub主页上就多了一个项目，只不过这个项目是基于你的项目基础〈本质上是在原有项目的基础上新建了一个分支〉，他就可以随心所欲的去改进，但是丝毫不会影响原有项目 的代码与结构。

该fork的项目是独立存在的

####  发起请求（Pull Request）

发起请求，这个其实是基于Fork的，还是上面那个例子，如果别人在你基础上做了改进，后来觉得改进的很不错，应该要把这些改进让更多的人收益，于是就想把自己的改进合并到原有项目里，这个时候他就可以发起一个pull Request（简称PR），原有项目创建人，也就是你，就可以收到这个请求，这个时候你会仔细review他的代码，并且测试觉得oK了，就会接受他的PR，这个时候他做的改进原有项目就会拥有了。

#### 关注（Watch)

这个也好理解就是观察，如果你watch了某个项目，那么以后只要这个项目有任何更新，你都会第一时间收到关于这个项目的通知提醒。

#### 事务卡片(lssue)

发现代码BuG，但是目前没有成型代码，需要讨论时用;
问题的意思，举个例子，就是你开源了一个项目，别人发现你的项目中有bug，或者哪些地方做的不够好，他就可以给你提个Issue , 即问题，提的问题多了，也就是lssues，然后你看到了这些问题就可以去逐个修复，修复ok了就可以一个个的Close掉。

#### Github主页

账号创建成功或点击网址导航栏github图标都可进入github主页:该页左侧主要显示用户动态以及关注用户或关注仓库的动态;右侧显示所有的git库

#### 仓库主页

仓库主页主要显示项目的信息，如:项目代码，版本，收藏/关注/fork情况等

#### 个人主页

个人信息:头像，个人简介，关注我的人，我关注的人，我关注的git库，我的开源项目，我贡献的开源项目等信息



## 安装和使用

![image-20210111154242170](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20210111154242170.png)

![image-20210111155031566](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20210111155031566.png)

![image-20210111155213058](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20210111155213058.png)

![image-20210111155242248](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20210111155242248.png)

![image-20210111155610027](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20210111155610027.png)

![image-20210111155550131](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20210111155550131.png)

![image-20210111155848459](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20210111155848459.png)



## 远程管理

![image-20210111160522331](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20210111160522331.png)

![image-20210111160528382](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20210111160528382.png)

![image-20210111160547390](C:\Users\mmm\AppData\Roaming\Typora\typora-user-images\image-20210111160547390.png)



## 分支管理

`git branch` ,查看当前的分支

`git branch dev` ,创建一个新的分支叫dev

`git checkout dev` ，切换到dev分支上

`git merge dev`，把dev分支上的修改合并到master分支上

`git reset --hard HEAD^`,取消上一步操作



