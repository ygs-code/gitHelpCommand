#  一、首先需要下载git  

　　查看电脑是否安装git,   

​       打开终端，输入git,回车如果输出如下,则代表已安装了git

![img](https://images2017.cnblogs.com/blog/1217154/201801/1217154-20180117173913459-1072951740.png)





如果未安装  到此处下载:[git下载](http://git-scm.com/downloads), pkg包下载完成，双击安装。

 

输入命令: git --version 可查看当前git版本

![img](https://images2017.cnblogs.com/blog/1217154/201801/1217154-20180117174249678-307467178.png)

 

# 二.安装后需要一些配置

 安装配置主要是要让git知道你当前的用户信息

 **配置用户名和邮箱:**

```
 git config --global user.name "Your Name"  
 git config --global user.email "email@example.com"  
```

使用 --global 修饰后设置的全局的用户,如果设置单个项目的用户,可cd到项目根目录下,执行如下命令:

```
 git config user.name "Your Name"  
 git config user.email "email@example.com"  
```

使用命令:git config --list 可查看当前用户信息以及其他的一些信息

```
 git config --list  
 user.email=yaoguanshou@rainbowcn.com
 
输出日志 
core.excludesfile=/Users/mac/.gitignore_global  
difftool.sourcetree.cmd=opendiff "$LOCAL" "$REMOTE"  
difftool.sourcetree.path=  
mergetool.sourcetree.cmd=/Applications/SourceTree.app/Contents/Resources/opendiff-w.sh "$LOCAL" "$REMOTE" -ancestor "$BASE" -merge "$MERGED"  
mergetool.sourcetree.trustexitcode=true  
http.postbuffer=524288000  
https.postbuffer=524288000  
user.email=你的邮箱@qq.com  
user.name=你的用户名  
macdeMacBook-Pro:~ Artron_LQQ$   
```



# 三.建立本地git仓库

**1. cd到你的项目目录**

```
 cd  d:/vue-project
```

2. 【】然后,输入git命令初始化git，让git去管理你的项目:

```
 git init  
```

输出如下:

```
git init  
日志
Initialized empty Git repository in 
d:/vue-project/.git/  
```

 我这个时候我们打开项目目录就看到有一个隐藏的 .git 文件夹

在项目中 添加 文件，比如js css html

查看当前库的一个状态

红色的就是我刚才在项目添加的一个文件

```
 git status
```

![2](.\2.png)







3.将项目的所有文件添加到缓存中，添加指定的某个文件:

```
 git add add.txt 
```

 

使用 修饰符

```
 git add .；  
```

```
git add -u；      将全部文件的修改、文件的删除，添加到暂存区。

git add .；       将全部文件的修改，文件的新建，添加到暂存区。

git add -A；      将全部文件的修改，文件的删除，文件的新建，添加到暂存区。 
```



3-1.在查看下文件状态

```
git status  
```

![3](.\3.png)



4.将缓存中的文件Commit到git库

git  commit -m "添加你的注释,一般是一些更改信息"

下面是第一次提交时的输出:

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 git commit -m "添加项目"
输出日志
[master (root-commit) 3102a38] 添加项目
 18 files changed, 1085 insertions(+)
 create mode 100644 GitTest.xcodeproj/project.pbxproj
 create mode 100644 GitTest.xcodeproj/project.xcworkspace/contents.xcworkspacedata
 create mode 100644 GitTest.xcodeproj/project.xcworkspace/xcuserdata/Artron_LQQ.xcuserdatad/UserInterfaceState.xcuserstate
 create mode 100644 GitTest.xcodeproj/xcuserdata/Artron_LQQ.xcuserdatad/xcschemes/GitTest.xcscheme
 create mode 100644 GitTest.xcodeproj/xcuserdata/Artron_LQQ.xcuserdatad/xcschemes/xcschememanagement.plist
 create mode 100644 GitTest/AppDelegate.h
 create mode 100644 GitTest/AppDelegate.m
 create mode 100644 GitTest/Assets.xcassets/AppIcon.appiconset/Contents.json
 create mode 100644 GitTest/Base.lproj/LaunchScreen.storyboard
 create mode 100644 GitTest/Base.lproj/Main.storyboard
 create mode 100644 GitTest/Info.plist
 create mode 100644 GitTest/ViewController.h
 create mode 100644 GitTest/ViewController.m
 create mode 100644 GitTest/main.m
 create mode 100644 GitTestTests/GitTestTests.m
 create mode 100644 GitTestTests/Info.plist
 create mode 100644 GitTestUITests/GitTestUITests.m
 create mode 100644 GitTestUITests/Info.plist
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

或者不添加注释 git commit  ,但是这样会进入vim(vi)编辑器

![4](.\4.png)

 在这里可以输入更改信息,也可以不输入,然后 按住 shift + :  ,输入wq 即可保存信息并退出vim编辑器;

# 四,建立远程库

在一些代码托管平台创建项目,例如[github](http://github.com/)或者[开源中国社区](http://git.oschina.net/),或者码云这里已github区为例;

注册一个github账号

![10](.\10.png)



然后创建仓库

![9](.\9.png)





创建项目后,会生成一个HTTPS链接,如下:

![11](.\11.png)

 复制仓库地址

```
https://github.com/qq281113270/vue-project.git
```

# 五,将本地的库链接到远

git查看远程仓库地址命令 

```
git remote -v
```



终端中输入: git remote add origin HTTPS链接

```
git remote add origin https://github.com/qq281113270/vue-project.git
```

 

如果Git 提示fatal: remote origin already exists 错误解决办法

先删除 本地仓origin 仓库

```
git remote rm origin 
git remote rm old-origin 
```

 

在添加连接远程仓库

```
git remote add origin https://github.com/qq281113270/vue-project.git
```



# 六.代码上传远程仓库

 上传代码到远程库,上传之前最好先Pull一下拉取下代码,再执行命令:

```
 git pull origin master
```

输出日志:

![5](.\5.png)

表示拉取成功



接着执行把本地代码添加到服务器中:

```
 git push origin maste
```

八. 这个时候会有个弹窗叫你输入用户和密码，这个用户账号和密码就是你github上面的账号和密码。

完成后输出:

![6](.\6.png)

 即将代码成功提交到远程库!!!

# git切换仓库源并且选择分支



````
 git checkout --track origin/<name>
````

origin是源名称  git checkout --track origin/分支名称



# 七.版本回滚

 先查看提交的版本日志

git log 查看全部，如果只是查看一条则用git log  -1

```
git log 
```

 我们主要关心的这一个id

![8](.\8.png)



当然也可以用工具看

**回滚到指定的版本**

![1559192273977](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\1559192273977.png)

命令回滚

```
git reset --hard e377f60e28c8b84158
```

**如果是正常的提交**   会出现报错

```
git   push   origin master
```



**强制提交** ，因为当前版本低于上面版本，所以只能

```
git push -f origin master
```



git强制覆盖本地：

```
git fetch --all
git reset --hard origin/master  //  master分支
git pull
```

git强制覆盖本地命令（单条执行）：

```
git fetch --all && git reset --hard origin/master &&  git pull
```











# 八. 分支管理 

## git查看远程仓库地址命令 

```
git remote -v
```



## 新建分支

### 新建本地分支

```
git branch newbranch
```

 如果创建分支的时候出错。fatal:not a valid object name: 'head'

 则表明该本地仓储没有提交过，需要执行 add 和 commit 指令提交一次

### 新建远程分支

把新建的本地分支push到远程服务器，远程分支与本地分支同名（当然可以随意起名）：

```
git push origin newbranch:newbranch
```

或者直接push

```
git push --set-upstream origin new_branch  
```

 

##查看分支

###查看本地分支

```
 git branch
```

输出: 两个分支

```
* master
  newbranch
```

*代表当前所在的分支

### 查看远程分支

```
 git branch -a
```



## 删除分支

### 删除本地分支

```
 git branch -d oldbranch
```

Deleted branch newbranch (was e28bdfd7).

表示删除成功

如果删除不了可以强制删除：

```
git branch -D oldbranch
```

### 删除远程分支

删除远程分支
我比较喜欢的简单方式，推送一个空分支到远程分支，其实就相当于删除远程分支：

```
git push origin :newbranch
```

也可以使用：

```
git push origin --delete newbranch
```

这两种方式都可以删除指定的远程分支



## 重命名分支

### 修改本地分支

```
git branch -m old_branch new_branch 
```



### 删除远程旧分支 

```
git push origin :old_branch #   删除远程旧分支 
git push origin --delete newbranch  # 也可以这样使用 删除远程旧分支 
```



### 然后到把当前分支提交到远程分支

```
git push --set-upstream origin  new_barnch
git push origin HEAD // 或者
```





## 查看当前分支状态

```
git status
```

### 切换分支

```
 git checkout newbranch
```

输出则表示切换成功

```
Switched to branch 'newbranch'
```

切换后可用git branch查看是否切换到当前分支

```
master
* newbranch
```

## 合并分支

假如我当前分支是newbranch，执行下面命令是把master分支的代码合并到我当前的newbranch分支中

```
git merge master
```

接着切回主分支

```
 git checkout master
```

输出:

```
Switched to branch 'master'
```

将新分支提交的改动合并到主分支上

```
git merge newbranch
```

输出:

```
Updating cc73a48..93a1347
Fast-forward
 GitTest.xcodeproj/project.pbxproj                        |   9 +++++++++
 .../UserInterfaceState.xcuserstate                       | Bin 0 -> 7518 bytes
 GitTest/test.h                                           |  13 +++++++++++++
 GitTest/test.m                                           |  13 +++++++++++++
 4 files changed, 35 insertions(+)
 create mode 100644 GitTest.xcodeproj/project.xcworkspace/xcuserdata/Artron_LQQ.xcuserdatad/UserInterfaceState.xcuserstate
 create mode 100644 GitTest/test.h
 create mode 100644 GitTest/test.m
```

这里我提交了两个文件,即:test.h和test.m

如果合并后产生冲突,可输入以下指令查看冲突:

```
 git diff
```

修改之后,再次提交即可;

接下来,就可以push代码了:

```
 git push -u origin master
```

这时可能需要你输入你的github用户名和密码,按照提示输入即可;

删除分支

```
 git branch -D newbranch
```

输出

```
Deleted branch newbranch (was 93a1347).
```

##  合并目录

```
git checkout 分支名 目录/**
git checkout dev check/**
(可能目录下还有多个目录所以用/**   不用/*)
```



## 提交代码到远程分支

```
git push --set-upstream origin develoment-theme
```



## Git branch 出现"HEAD detached at head xxxxx"

```
   ### 给 xxxxx 起个 branch 名
```

```
git branch <your-branch-name> xxxxx    
```

### Head 指到 master，当然可以是其它的branch

```
git checkout master       
```

### 融合到当前 branch

```
git merge <your-branch-name> 
```

### 删除临时 branch

```
git branch -d <your-branch-name>
```









# 九. 解决冲突

如果合并后产生冲突,可输入以下指令查看冲突:

```
 git diff
```



当然我们一般建议用可视化工具

* github桌面版本  <https://desktop.github.com/>   这个主要是把github主要功能放在这个软件中，比较常用的是可视化版本管理记录
* git乌龟。 下载地址 <https://tortoisegit.org/download/>
     * 先下载安装包，再安装语言包，则会汉化了。
* git乌龟主要是把git用命令提交的方式，然后变成了工具去提交，这样可减少开发人员，敲指令的一个痛苦。



#Git fetch和git pull的区别, 解决Git报错:error: You have not concluded your merge 

## **Git fetch和git pull的区别:**

### 都可以从远程获取最新版本到本地

### **1.Git fetch:只是从远程获取最新版本到本地,不会merge(合并)**

```
git fetch origin master       //从远程的origin的master主分支上获取最新版本到origin/master分支上
git log -p master..origin/master //比较本地的master分支和origin/master分支的区别
git merge origin/master          //合并123
```

### **2.Git pull:从远程获取最新版本并merge(合并)到本地**

```
git pull origin master  //相当于进行了 git fetch 和 git merge两部操作1
```

### 实际工作中,可能`git fetch`更好一些, 因为在`merge`前,可以根据实际情况决定是否`merge`

------

## **再说导致报错:error: You have not concluded your merge (MERGE_HEAD exists).的原因可能是在以前pull下来的代码自动合并失败**

### **解决办法一:保留本地的更改,中止合并->重新合并->重新拉取**

```
git merge --abort
git reset --merge
git pull123
```

### **解决办法二:舍弃本地代码,远端版本覆盖本地版本(慎重)**

```
git fetch --all
git reset --hard origin/master
git fetch
```



## VsCode git合并冲突

### Accept Current Change:丢弃远程pull，merge。保留本地更改

会丢弃远程拉取的或者合并进来的，只保留我自己本地改变的

### Accept Incoming Change: 丢弃本地。保留远程pull，merge

会丢弃我本地所有更改的，保留远程或者合并进来的内容

### Accept Both Changes: 接受变化和我本地一起

会保留我本地更改的代码和远程或者合并进来的代码，一起不丢弃任何一方。 

### Compare Change: 比较变化

选择他会弹出两个窗口给你做对比哪些更改了

 





# Git 清空工作区和暂存区

##<a href="https://git-scm.com/book/zh/v1/Git-%E5%B7%A5%E5%85%B7-%E5%82%A8%E8%97%8F%EF%BC%88Stashing%EF%BC%89">3 Git 工具 - 储藏（Stashing）</a>

## 查看git 提交的id 状态

```
git reflog  
```



###  回退到/进到，指定commit的哈希码

```
git  reset --hard  commit_id
```

git reset --hard commit_id 退到/进到，指定commit的哈希码（这次提交之前或之后的提交都会回滚）

```
 git  reset --hard fdeb212a5418cc8e31f32d63cf197550297468ec
```

- --hard – 强制将缓存区和工作目录都同步到你指定的提交



## **回滚 git reset --hard 提交id、这it reset --hard HEAD~1(1:代表回退一次)** 

####      **--mixed 意思是：不删除工作空间改动代码，撤销commit，并且撤销git add . 操作 这个为默认参数,**

```
git reset --mixed HEAD^  和  git reset HEAD^ 效果是一样的。
```

####    **--soft 不删除工作空间改动代码，撤销commit，不撤销git add .** 

```
git reset  --soft  HEAD^
```

####     **--hard 删除工作空间改动代码，撤销commit，撤销git add . 注意完成这个操作后，就恢复到了上一次的commit状态。**

```
git reset  --hard   HEAD^
```





## [git远程仓库版本回退方法](https://www.cnblogs.com/wk179002/p/11377191.html)



1.**本地分支版本回退的方法**

a.使用**git reflog**命令查看历史提交记录的commit id

```
git reflog
```

b.使用**git reset --hard commit_id**回退本地分支，commit_id为你要回退版本的commit id的前几位

```
git reset --hard commit_id
```

c.使用**git push -f**强制推送到远程分支

2.公共远程分支版本回退的方法

a.使用**git reflog**命令查看历史提交记录的commit id

```
git reflog
```

b.使用**git revert commit_id**或者**git revert HEAD~0/1/2**指令撤销最近的提交

```
git revert commit_id
```

c.revert合并代码，主要是去掉新代码，解决冲突；如果没有冲突，使用使用**git push -f**强制推送到远程分支

```
git push -f
```

3.**没有办法的办法**

a.从头再来，删仓重建

注意：

**1.使用git reflog命令后，如果记录很长，可以在大写锁定状态下输入一次'Q'或者两次'Z'退出git log和git reflog状态**

**2.git revert指令注意事项**

**a.revert是撤销一次提交，所以commit id是你要回滚到的版本的前一次提交**

**b.使用revert HEAD是撤销最近的一次提交，如果你最近一次提交是用revert命令产生的，那么再执行一次就相当于撤销了上次的撤销操作，即连续两次执行revert HEAD命令，相当于没有执行**

**c.使用revert HEAD~1表示撤销最近2次提交，后面的数字是从0开始的，即revert HEAD~n撤销n+1次提交**

**d.如果使用revert撤销的不是最近一次提交，那么一定会有代码冲突，需要合并代码，合并代码只需要把当前的代码全部取消，保留之前版本的代码即可。**



# git stash命令

当你想要保存当前的暂存区和工作区的状态的时候，你可以使用git stash命令。比如：你正在开发一个新功能，写了一些代码（保存暂存的和没有暂存的或没有记录的），现在需要去修复一个紧急bug,或者是需要更新别人的代码，你又不想提交，这时你可以选择保存当前工作区和暂存区的内容，需要的时候恢复。

这个命令会保存当前的暂存区和工作区的状态，然后返回到HEAD（git reset —hard HEAD）。最新的stach可以在.git/refs/stash中看到。

## 保存当前缓存区



先把自己本地的代码保存到缓存区域，这样就可以更新别人的代码了，或者修改其他bug。或者切换分支

```
git add .   // 添加到缓存区域
git stash save  //保存缓存区
```

## 查看缓存列表

```
git stash list
```

## 显示和他parent的差异

```
git stash show [stash]
```

## 恢复工作区, 与git stash save执行相反的操作，从stash list中移除这个stash.

```
git stash pop
```

## 恢复工作区, apply和pop类似，不会吧stash从stash list中移除

```
git stash apply
```



## 清空当前所有的stash

```
git stash clear
```



# 十.配置ssh 秘钥

在公司一般是多人开发，所以要考虑下这个功能

```
ssh-keygen -t rsa -C "邮箱" 
```

一直Enter下去生成公钥如下所示： 



![7](.\7.png)



或者你也可以直接输入命令 ：

```
cat ~/.ssh/id_rsa.pub
```

 

接下来我们

![13](.\13.png)

然后配置github 的 sshkey

![14](.\14.png)



配置好了之后验证输入命令

```
ssh -T git@github.com
```

 如果出现以下则表示成功

![15](.\15.png)



如果出现22端口报错，或者是403 则需要提交一次给该项目的负责人，可能需要负责人输入一次用户和密码。



#[git stash 用法总结和注意点](https://www.cnblogs.com/zndxall/p/9586088.html) 

常用git stash命令：

（1）**git stash** save "save message"  : 执行存储时，添加备注，方便查找，只有git stash 也要可以的，但查找时不方便识别。

（2）**git stash list**  ：查看stash了哪些存储

（3）**git stash show** ：显示做了哪些改动，默认show第一个存储,如果要显示其他存贮，后面加stash@{$num}，比如第二个 git stash show stash@{1}

（4）**git stash show -p** : 显示第一个存储的改动，如果想显示其他存存储，命令：git stash show  stash@{$num}  -p ，比如第二个：git stash show  stash@{1}  -p

（5）**git stash apply** :应用某个存储,但不会把存储从存储列表中删除，默认使用第一个存储,即stash@{0}，如果要使用其他个，git stash apply stash@{$num} ， 比如第二个：git stash apply stash@{1} 

（6）**git stash pop** ：命令恢复之前缓存的工作目录，将缓存堆栈中的对应stash删除，并将对应修改应用到当前的工作目录下,默认为第一个stash,即stash@{0}，如果要应用并删除其他stash，命令：git stash pop stash@{$num} ，比如应用并删除第二个：git stash pop stash@{1}

（7）**git stash drop** stash@{$num} ：丢弃stash@{$num}存储，从列表中删除这个存储

（8）`**git stash clear** ：`删除所有缓存的stash







## git查看远程仓库地址命令

```
git remote -v
```









# [Git更改文件名大小写，提交失败问题解决](https://www.cnblogs.com/meitian/p/11156035.html)

背景：某java文件大小写写错了，一直提交不上去

例如我只是将updatePrivacySettingsTest.java变更为UpdatePrivacySettingsTest.java，但是add后一直是未提交状态

![img](https://img2018.cnblogs.com/blog/626983/201907/626983-20190709105954318-251493284.png)

 

## **原因与解决方案：**

Git配置默认忽略了大小写，需要配置为不忽略大小写

 

**查看是否忽略大小写：**

```
git config core.ignorecase
```

备注：true为忽略了大小写，false为为忽略大小写

 

**设置默认不忽略大小写：**

```
git config core.ignorecase false
```

 

然后再次提交，成功~



# fatal: refusing to merge unrelated histories解决

## Git :fatal: refusing to merge unrelated histories解决

今天本地创建了一个仓库（有README)，把本地仓库和Github上关联以后，发现git pull，git feach提醒fatal: refusing to merge unrelated histories
![截图示例](https://img-blog.csdnimg.cn/20190830090402218.png)
上网查到原因是两个分支是两个不同的版本，具有不同的提交历史



加一句

```
$git pull origin master --allow-unrelated-histories
```

可以允许不相关历史提，强制合并，确实解决了这个问题，感谢网友







# [Git error： hint: Updates were rejected because the remote contains work that you do hint: not have locally. This is usually caused b](https://www.cnblogs.com/czwangzheng/p/5086903.html)



hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

![img](data:image/png;base64,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)

解决办法：

$ git pull origin master
$ git push origin master





# 分享 | Git中.gitignore文件不起作用的解决以及Git中的忽略规则介绍 

有些时候我们需要忽略掉一些目录或者文件，但是我们手工创建了.gitignore之后，我们已经标明了要忽略的文件或者目录，还是会被纳入到版本管理中。

我们看看.gitignore中，显然已经做了忽略声明。但是为什么没有生效呢？

![img](https://5b0988e595225.cdn.sohucs.com/images/20180110/0134af087bd24f999591c603e77af2bf.png)

原因是因为在phpstorm的git忽略目录中，新建的文件在git中会有缓存，如果某些文件已经被纳入了版本管理中，就算是在.gitignore中已经声明了忽略路径也是不起作用的，这时候我们就应该先把本地缓存删除，然后再进行git的push，这样就不会出现忽略的文件了。

我们在终端中删除git的缓存

\>git rm -r --cached .

注意上面的命令，最后那个点一定不要漏掉了。之后在重新添加

\>git add .

重新提交推送。然后我们再来看。

我们的.gitignore生效了。



然后 在重新 commit 和push一下



# git 打标签

## **列出标签**

在 Git 中列出已有的标签是非常简单直观的。 只需要输入 git tag：

```
$ git tag
```

这个命令以字母顺序列出标签，但是它们出现的顺序并不重要。

可使用特定的模式查找标签。如，Git自身的源代码仓库包含的标签数量超过500个，如果只对 1.8.5系列感兴趣，可以运行：

```git
$ git tag -l 'v1.8.5*'
v1.8.5
v1.8.5-rc0
v1.8.5-rc1
v1.8.5.1
v1.8.5.2
```



## **创建TAG标签**

Git 使用两种主要类型的标签：轻量标签（lightweight）与附注标签（annotated）。

轻量标签很像一个不会改变的分支，它只是一个特定提交的引用。

附注标签是存储在 Git 数据库中的一个完整对象。 它们是可以被校验的；其中包含打标签者的名字、电子邮件地址、日期时间；还有一个标签信息；并且可以使用 GNU Privacy Guard （GPG）签名与验证。

通常建议创建附注标签，这样你可以拥有以上所有信息；但是如果你只是想用一个临时的标签，或者因为某些原因不想要保存那些信息，轻量标签也是可用的。

### **Git创建附注标签**

创建附注标签简单的方式是运行 *tag* 命令时指定 *-a* 选项：

```git
$ git tag -a v1.5 -m 'Version 1.5'
$ git tag
v0.1
v1.2
v1.5
```

*-m* 选项指定了一条将会存储在标签中的信息。如果没有为附注标签指定一条信息，Git会运行编辑器要求你输入信息。

### **Git创建轻量标签**

轻量标签本质上是将提交校验和存储到一个文件中，没有保存任何其他信息。 创建轻量标签，不需要使用 *-a、-s* 或 *-m* 选项，只需要提供标签名字：

```git
$ git tag v1.5-lw1
```

## **查看标签信息**

查看标签信息可以运行 *git show < tag-name>* 命令：

```git
$ git show v1.51
```

对于附注标签可以看到标签信息，而轻量标签只能看到提交信息。

## **后期打标签**

你可以对过去的提交打标签。假设提交历史是这样的：

```git
$ git log --pretty=oneline
15027957951b64cf874c3557a0f3547bd83b3ff6 Merge branch 'experiment'
a6b4c97498bd301d84096da251c98a07c7723e65 beginning write support
0d52aaab4479697da7686c15f77a3d64d9165190 one more thing
6d52a271eda8725415634dd79daabbc4d9b6008e Merge branch 'experiment'
0b7434d86859cc7b8c3d5e1dddfed66ff742fcbc added a commit function
4682c3261057305bdd616e23b64b0857d832627b added a todo file
166ae0c4d3f420721acbb115cc33848dfcc2121a started write support
9fceb02d0ae598e95dc970b74767f19372d61af8 updated rakefile
964f16d36dfccde844893cac5b347e7b3d44abbc commit the todo
8a5cbc430f1a9c3d00faaeffd07798508422908a updated readme1234567891011
```

现在，假设在 v1.2 时你忘记给项目打标签，也就是在 “updated rakefile” 提交。 你可以在之后补上标签。 要在那个提交上打标签，你需要在命令的末尾指定提交的校验和（或部分校验和）:

```git
$ git tag -a v1.2 9fceb02 -m 'version 1.2'
```

这样就为那次提交打上标签了。

## **删除标签**

删除标签可执行 *git tag -d < tag-name> …* 命令：

```git
$ git tag -d v1.2-lw v1.3
Deleted tag 'v1.2-lw' (was 646b3f0)
Deleted tag 'v1.3' (was 8792400)git 123
```

执行后删除了两个标签。

### 删除标签

要删除掉你本地仓库上的标签，可以使用命令 `git tag -d <tagname>`。 例如，可以使用以下命令删除一个轻量标签：

```console
$ git tag -d v1.4-lw
Deleted tag 'v1.4-lw' (was e7d5add)
```

注意上述命令并不会从任何远程仓库中移除这个标签，你必须用 `git push <remote> :refs/tags/<tagname>` 来更新你的远程仓库：

第一种变体是 `git push <remote> :refs/tags/<tagname>` ：

```console
$ git push origin :refs/tags/v1.4-lw
To /git@github.com:schacon/simplegit.git
 - [deleted]         v1.4-lw
```

上面这种操作的含义是，将冒号前面的空值推送到远程标签名，从而高效地删除它。

第二种更直观的删除远程标签的方式是：

```console
$ git push origin --delete <tagname>
```



## **共享标签**

默认情况下，*git push* 命令并不会传送标签到远程仓库服务器上。 在创建完标签后你必须显式地推送标签到共享服务器上。 这个过程就像共享远程分支一样， 你可以运行 *git push origin < tagname>*。

```git
$ git push origin v1.51
```

如果想要一次性推送很多标签，也可以使用带有 *–tags* 选项的 *git push* 命令。 这将会把所有不在远程仓库服务器上的标签全部传送到那里。

```git
$ git push origin --tags1
```

现在，当其他人从仓库中克隆或拉取，他们也能得到你的那些标签。









默认标签是打在最新提交的commit上的。有时候，如果忘了打标签，比如，现在已经是周五了，但应该在周一打的标签没有打，怎么办？

方法是找到历史提交的commit id，然后打上就可以了：

```
$ git log --pretty=oneline --abbrev-commit
12a631b (HEAD -> master, tag: v1.0, origin/master) merged bug fix 101
4c805e2 fix bug 101
e1e9c68 merge with no-ff
f52c633 add merge
cf810e4 conflict fixed
5dc6824 & simple
14096d0 AND simple
b17d20e branch test
d46f35e remove test.txt
b84166e add test.txt
519219b git tracks changes
e43a48b understand how stage works
1094adb append GPL
e475afc add distributed
eaadf4e wrote a readme file
```

比方说要对`add merge`这次提交打标签，它对应的commit id是`f52c633`，敲入命令：

```
$ git tag v0.9 f52c633
```

或者还可以创建带有说明的标签，用`-a`指定标签名，`-m`指定说明文字：

```
$ git tag -a v0.1 -m "version 0.1 released" 1094adb
```

再用命令`git tag`查看标签：

```
$ git tag
v0.9
v1.0
```







如果标签打错了，也可以删除：

```
$ git tag -d v0.1
Deleted tag 'v0.1' (was f15b0dd)
```

因为创建的标签都只存储在本地，不会自动推送到远程。所以，打错的标签可以在本地安全删除。

如果要推送某个标签到远程，使用命令`git push origin <tagname>`：

```
$ git push origin v1.0
Total 0 (delta 0), reused 0 (delta 0)
To github.com:michaelliao/learngit.git
 * [new tag]         v1.0 -> v1.0
```

或者，一次性推送全部尚未推送到远程的本地标签：

```
$ git push origin --tags
Total 0 (delta 0), reused 0 (delta 0)
To github.com:michaelliao/learngit.git
 * [new tag]         v0.9 -> v0.9
```

如果标签已经推送到远程，要删除远程标签就麻烦一点，先从本地删除：

```
$ git tag -d v0.9
Deleted tag 'v0.9' (was f52c633)
```

然后，从远程删除。删除命令也是push，但是格式如下：

```
$ git push origin :refs/tags/v0.9
To github.com:michaelliao/learngit.git
 - [deleted]         v0.9
```



### git 切换用户下载代码。

如果有两套gitlab 服务可以能会出现这样问题，所以我们需要切换用户

```
git config --system --unset credential.helper
```











# 版本环境

* development 开发环境 
  * 开发环境是程序猿们专门用于开发的服务器，配置可以比较随意， 为了开发调试方便，一般打开全部错误报告。(程序员接到需求后，开始写代码，开发，运行程序，看看程序有没有达到预期的功能；)

*  testing测试环境
  * 一般是克隆一份生产环境的配置，一个程序在测试环境工作不正常，那么肯定不能把它发布到生产机上。(程序员开发完成后，交给测试部门全面的测试，看看所实现的功能有没有bug，测试人员会模拟各种操作情况；)
* Alpha  
  *  alpha测试是在用户组织模拟软件系统的运行环境下的一种验收测试,由用户或第三方测试公司进行的测试,模拟各类用户行为对即将面市的软件产品进行测试,试图发现并修改错误。
  *  Alpha测试是指把用户请到开发方的场所来测试,
  *  一般地,alpha测试先于beta测试执行。
* Beta
  *  Beta测试是用户公司组织各方面的典型终端用户在日常工作中实际使用beta版本,并要求用户报告异常情况,提出批评意见。
  *  beta测试是指在一个或多个用户的场所进行的测试。Alpha测试的环境是受开发方控制的,用户的数量相对比较少,时间比较集中。
  *  通用的软件产品需要较大规模的beta测试,测试周期比较长。如果产品通过了beta测试,那么就可以正式发行了。

* production   生产环境
      *  正式生产环境，表明改软件经过多次测试，已经稳定没有bug的情况下发布



