# Git

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

#### 初始化一个新的Git仓库

1.创建文件夹 <br/>
`mkdir demo1`

2.在文件夹内初始化Git（创建Git仓库） <br/>
`cd demo1`  <br/>

`git init` 

#### 添加到暂存区
`git add a1.php` 添加某一个文件 <br/>
`git add .` 添加所有文件

#### 删除文件
1.删除文件<br/>
`rm test.php`<br/>

2.从git中删除文件<br/>
`git rm test.php`<br/>

3.提交操作<br/>
`git commit -m '提交描述'`



## 远程管理

#### 建立远程连接
`git remote add origin [url]` origin是建立的连接名称，后面的url是需要关联github上面那个仓库的地址，或者是使用命令<br>

`git remote -v` 查看所有连接

#### 推送到远程
`git push origin master` 把缓存区的文件推送到远程master分支

此时会提示输入账号和密码

>**推荐使用个人访问令牌**
作为安全预防措施，GitHub 会自动删除一年内未使用过的个人访问令牌。

##### 创建令牌
1.在任何页面的右上角，单击您的个人资料照片，然后单击 **Settings（设置）。**<br>
2.在左侧边栏中，单击 **Developer settings。**<br>
3.在左侧边栏中，单击 **Personal access tokens（个人访问令牌）。**<br>
4.单击 **Generate new token（生成新令牌）。**<br>
5.将令牌复制到剪贴板。 出于安全原因，离开此页面后，您将无法再次看到令牌。<br>
6.在输入账号和密码时，密码就是这个token令牌


## 分支管理

`git branch` ,查看当前的分支

`git branch dev` ,创建一个新的分支叫dev

`git checkout dev` ，切换到dev分支上

`git merge dev`，把dev分支上的修改合并到master分支上

`git reset --hard HEAD^`,取消上一步操作

`git status` 查看状态及执行提交命令

`git remote update origin --prune` 更新远程分支列表

`git branch -a` 查看所有分支

`git push origin --delete Chapater6` 删除远程分支Chapater6

`git branch -d  Chapater6` 删除本地分支 Chapater6


## 其他问题

1. ! [rejected] master -> master (fetch first) error: failed to push some refs to ' 。。。'

出现这个问题是因为github中的README.md文件不在本地代码目录中，可以通过如下命令进行代码合并

`git pull --rebase origin master`

2. ! 出现了这样的问题 ` everything up-to-date`

原因：git提交改动到缓存，要push的时候不会将本地所有的分支都push掉，所以出现这个问题。那么我们就需要新建分支提交改动然后合并分支。

**1.先创建一个新的分支提交改动**
`git branch newbranch`

**2.检查这条命令是否创建成功**
`git branch`

这时终端会输出：
```
newbranch

*master
```
这样就创建成功了，前面的*代表的是当前你所在的工作分支，接下来就要切换工作分支。

**3.git checkout newbranch**

**4.然后将你的改动提交到新的分支上***
```
git add .

git commit -m "提示消息"
```

此时可以`git status` 检查下提交情况。如果提交成功，我们接下来就要回主分支了，`git checkout master`

**5.我们将新分支提交的改动合并到主分支上**
`git merge newbranch`

合并分支可能产生冲突这是正常的，虽然我们这是新建的分支不会产生冲突，但还是在这里记录下。可以用

`git diff` 来查看产生冲突的文件，然后做对应的修改再提交一次就可以了。

**6.我们的问题解决了，接下来就可以push代码了**
`git push -u origin master`

**7.最后，新建分支的朋友别忘了删除分支**
`git branch -D newbranch`

如果想保留分支只是想删除已经合并的部分只要把大写的D改成小写的d就行了。
