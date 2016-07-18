
---
最近一周在博客里学习了关于Git方面的知识，收益颇多，简单的整理一下所学内容。

>  * **什么是Git**
>  * **windows下Git的安装**
>  * **创建本地仓库**
>  * **一些常用知识和命令** 
>  * **远程仓库的使用**
>  * **分支的管理**

---
## 1. 什么是Git

Git是一种**分布式版本控制系统**。什么是分布式版本控制系统？我们首先了解一下集中版本控制系统。集中版本控制系统只有一个版本仓库，储存在中心服务器，每个人都要从这一个版本库下载最新版本，然后修改版本后提交修改到这一版本仓库。而在分布式版本控制系统中，每个人够可以在本地建立版本仓库，对自己本地的版本仓库进行修改。如果想要得到对方的版本仓库，只需要相互推送即可。

---
## 2. Windows下Git的安装

首先我们来到 [Windows版Git下载地址](https://git-for-windows.github.io/)下载安装Git,安装时全部按默认选项安装。

安装完成后， 点击开始菜单里的GitBash选项，设置该台机器的用户信息。
（git config命令的--global参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置）
```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

---
## 3. 创建本地仓库

###(1) 使用 git init 命令在某一目录初始化一个Git仓库
```
$ git init
```

###(2) 添加目录里的文件到Git仓库，分为两步：

* 第一步，使用命令git add filename
```
$ git add filename
```
* 第二步，使用命令git commit
```
$ git commit -m "提交说明"
```
不过可以使用git commit -a -m选项，Git就会自动把所有已经跟踪过的文件暂存起来一并提交，从而跳过 git add 步骤
 
---
## 4. 一些常用知识和命令

###(1)Git的工作流程

![logo](http://www.liaoxuefeng.com/files/attachments/001384907702917346729e9afbf4127b6dfbae9207af016000/0)

HEAD指向的版本就是当前版本。

用git add把文件添加进去，实际上就是把文件修改添加到暂存区。

用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支。

###(2)版本回退和回归

```
git log
```     
查看从最近到最远的提交日志，确定要回退的版本。

```
git reflog
```   
查看命令历史，确定回归的版本。

```
git reset --hard commit_id
```   
版本回退或回归。

###(3)撤销修改或删除文件

```
git checkout -- file
```
适用于修改了工作区的文件，就是让这个文件回到最近一次git commit或git add时的状态。

```
git reset HEAD file 
git checkout -- file
```  
适用于不仅修改了工作区某个文件的内容，还添加到了暂存区的文件。

```
git rm
```
用于删除版本库中的一个文件，删除后用git commit提交。

---
## 5. 远程仓库的使用
###(1)要查看当前配置有哪些远程仓库
```
git remote (-v)
```

###(2)添加远程仓库
```
$ git remote add origin + 账户仓库地址
```
###(3)从远程仓库抓取数据
```
$ git fetch [remote-name]
```
命令只是将远端的数据拉到本地仓库，并不自动合并到当前工作分支.但如果设置了某个分支用于跟踪某个远端仓库的分支，可以使用 **git pull**命令自动抓取数据下来，然后将远端分支自动合并到本地仓库中当前分支。
###(4)推送本地内容到远程仓库
```
$ git push -u origin master (第一次推送master分支时，加上了-u参数)
```
###(5)从远程仓库克隆
```
$ git clone + 远程仓库地址
```
###(5)放弃本地修改并强制更新远程仓库
```
git fetch --all
git reset --hard origin/master
```

---
## 6. 分支的管理
###(1)创建和合并分支
```
git branch
```
查看分支

```
git branch <name>
```
创建分支
```
git checkout <name>
```
切换分支
```
git merge <name>
```
合并某分支到当前分支
```
git branch -d <name>
```
删除分支
###(2)有关分支工作时的命令
```
git log --graph
```
当Git无法自动合并分支时，就必须首先解决冲突。该命令可以看到分支合并图。
```
git stash
```
把当前工作现场“储藏”起来，等以后恢复现场后继续工作.
```
git stash pop
```
回到git stash时的工作现场




