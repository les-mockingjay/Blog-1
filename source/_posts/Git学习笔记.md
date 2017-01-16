---
title: Git学习笔记
date: 2017-01-15 20:57:06
tags: Git
---

# Git简介
最先进的分布式版本控制系统（没有之一）
## 集中式vs分布式
### 集中式版本控制系统
>**含义：**  
>将版本库集中存放在中央服务器的，干活的时候先从中央服务器取得最新的版本至自己的电脑，然后修改完后再把文件推送给中央服务器。

### 分布式版本控制系统
>**含义：**  
>分布式的版本控制就是每个人都可以创建一个独立的代码仓库用于管理，各种版本控制的操作都可以在本地完成。每个人修改的代码都可以推送合并到另外一个代码仓库中。

# 安装Git
## 在Linux上安装Git
①：看看系统有没有安装Git：`git`
```bash
$ git
The program 'git' is currently not installed. You can install it by typing:
sudo apt-get install git
```
②：完成Git的安装：`sudo apt-get install git`或`yum install git`

## 在Mac OS X上安装Git

## 在Windows上安装Git
①：msysgit是Windows版的Git，从https://git-for-windows.github.io下载按默认选项安装即可。
②：在开始菜单里找到“Git”->“Git Bash”，蹦出一个类似命令行窗口的东西，就说明Git安装成功  
③：安装完成后，还需要最后一步设置，在命令行输入：  
```bash
$ git config --global user.name "lafitehhq"
$ git config --global user.email "lafitehhq@126.com"
```
*注意：*
--global参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。

# 创建版本库
>**含义：**
>版本库又名仓库，简单理解成一个目录，这个目录里面的所有文件都可以被Git管理起来，每个文件的修改、删除，Git都能跟踪，以便任何时刻都可以追踪历史，或者在将来某个时刻可以“还原”。

## 创建版本库
①：进入一个合适的目录，创建一个空目录
```bash
$ mkdir learngit
$ cd learngit
$ pwd
/Users/lafitehhq/learngit
```
*注意：*  
为了避免遇到各种莫名其妙的问题，请确保目录名（包括父目录）不包含中文。  
②：把当前空目录变成Git可以管理的仓库：`git init`
```bash
$ git init
Initialized empty Git repository in /Users/michael/lafitehhq/.git/
```
*注意：*  
当前目录下多了一个.git的目录(使用`ls -ah`可以查看)，这个目录是Git来跟踪管理版本库的，不要修改这个目录里面的文件。

## 把文件添加到版本库
>所有的版本控制系统，其实只能跟踪文本文件的改动，比如TXT文件，网页，所有的程序代码等等，Git也不例外。而图片、视频这些二进制文件，虽然也能由版本控制系统管理，但没法跟踪文件的变化，只能把二进制文件每次改动串起来，也就是只知道图片从100KB改成了120KB，但到底改了啥，版本控制系统不知道，也没法知道。

*注意：*  
不要使用Windows自带的记事本编辑任何文本文件,建议你下载Notepad++代替记事本，不但功能强大，而且免费！记得把Notepad++的默认编码设置为UTF-8 without BOM即可：  
![windows_Notepad++](http://ojifsovoq.bkt.clouddn.com/image/jpg/windows_Notepad++.jpeg)

## 示例
>**需求：**
>编写一个readme.txt文件，放到learngit目录下（子目录也行）

①：把文件添加到仓库
```zsh
git add readme.txt
```
②：把文件提交到仓库：
```zsh
$ git commit -m "wrote a readme file"
[master (root-commit) cb926e7] wrote a readme file
 1 file changed, 2 insertions(+)
 create mode 100644 readme.txt
```
*注意：*  
-m后面输入的是本次提交的说明；  
commit可以一次提交很多文件，可以多次add不同的文件，再一次提交commit

# 时光机穿梭
##  查看工作区
### 命令
①：掌握工作区的状态：`git status`
②：若有文件被修改过，查看修改内容：`git diff`
### 示例
①：修改readme.txt文件
```bash
Git is a distributed version control system.
Git is free software.
```
②：运行git status命令看看结果
>readme.txt被修改过了，但还没有准备提交的修改。

```bash
$ git status
# On branch master
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#    modified:   readme.txt
#
no changes added to commit (use "git add" and/or "git commit -a")
```

③：查看具体修改了什么内容
>在第一行添加了一个“distributed”单词。

```bash
$ git diff readme.txt 
diff --git a/readme.txt b/readme.txt
index 46d49bf..9247db6 100644
--- a/readme.txt
+++ b/readme.txt
@@ -1,2 +1,2 @@
-Git is a version control system.
+Git is a distributed version control system.
 Git is free software.
```
④：提交修改和提交新文件是一样
第一步： `git add` 
```bash
$ git add readme.txt
``` 
第二步：查看当前仓库的状态：`git status`
>将要被提交的修改包括readme.txt

```bash
$ git status
# On branch master
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#       modified:   readme.txt
#
```
第三步：提交：`git commit`
```bash
git commit -m "add distributed"
```
第四步：看看调校后仓库的状态
>当前没有需要提交的修改，而且，工作目录是干净（working directory clean）的

```bash
$ git status
# On branch master
nothing to commit (working directory clean)
```
## 版本回退
### 命令
①：跳转前先查看提交历史，确定要回退到哪个版本：`git log`或`git log --pretty=oneline`    
②：在版本的历史跳转：`git reset --hard commit_id` 或`git reset --hard HEAD^n`（n是返回前n个版本） 
③：要重返未来，查看命令历史，确定要回到未来的哪个版本：`git reflog`  
### 示例
①：查看文件从最近到最远的提交日志的历史记录

```bash
$ git log
commit ea34578d5496d7dd233c827ed32a8cd576c5ee85
Author: Michael Liao <askxuefeng@gmail.com>
Date:   Tue Aug 20 14:53:12 2013 +0800

    add distributed

commit cb926e7ea50ad11b8f9e909c05226233bf755030
Author: Michael Liao <askxuefeng@gmail.com>
Date:   Mon Aug 19 17:51:55 2013 +0800

    wrote a readme file

```

*注意：*  
类似cb926e7ea50ad11b8f9e909c05226233bf755030是commit id（版本号）  
②：把当前版本回退到上一个版本
```bash
$ git reset --hard HEAD^
HEAD is now at cb926e7 add distributed
```
*注意：*  
`--hard`的意义:  
版本号没必要写全，前几位就可以了，Git会自动去找。当然也不能只写前一两位，因为Git可能会找到多个版本号，就无法确定是哪一个了
③：将当前版本恢复回之前最新的版本
Git提供了一个命令`git reflog`记录每一次命令：  
```bash
$ git reflog
ea34578 HEAD@{0}: reset: moving to HEAD^
ea34578 HEAD@{2}: commit: add distributed
cb926e7 HEAD@{3}: commit (initial): wrote a readme file
```
④：把当前版本回退到想要的版本
```bash
$ git reset --hard ea34578
HEAD is now at ea34578 add distributed
```

## 工作区和暂存区
### 工作区（Working Directory）
>电脑里能看到的目录

### 版本库（Repository）
>工作区有一个隐藏目录.git,是Git的版本库。  
>Git的版本库里存了很多东西  
>stage（或者叫index）：暂存区  
>master：Git为我们自动创建的第一个分支  
>HEAD：指向master的一个指针  

![Git_工作区&版本库&暂存区_1](http://ojifsovoq.bkt.clouddn.com/image/jpg/Git_%E5%B7%A5%E4%BD%9C%E5%8C%BA&%E7%89%88%E6%9C%AC%E5%BA%93&%E6%9A%82%E5%AD%98%E5%8C%BA.jpeg)
### Git工作原理
`git add`把文件添加进去，实际上就是把文件修改添加到暂存区  
`git commit`提交更改，实际上就是把暂存区的所有内容一次提交到当前分支  
创建Git版本库时，Git自动创建了唯一一个master分支，git commit就是往master分支上提交更改。
可以理解为：需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改



## 管理修改
## 撤销修改
## 删除文件
# 远程仓库
## 添加远程库
## 从远程库克隆
# 分支管理
## 创建与合并分支
## 解决冲突
## 分支管理策略
## Bug分支
## Feature分支
## 多人协作
# 标签管理
## 创建标签
## 操作标签
# 使用GitHub
# 自定义Git
## 忽略特殊文件
## 配置别名
## 搭建Git服务器
