---
layout:     post
title:      "Git常用简单指令"
subtitle:   "Git的常用指令"
date:       2018-03-02 12:00:00
author:     "lcy"
header-img: "img/home-bg-o.jpg"
---

# Git
分布式版本控制系统，可以有效、高速的处理从很小到非常大的项目版本管理。
### 一. 新建Git项目
#### 1. 新建.gitignore
>.gitignore：用于对仓库中一些不必要加入版本管理的文件进行过滤

* Android中

```
# Idea
*.iml
/.idea/
/.gradle/
local.properties
/build/
os.jks
.DS_Store
gradle.properties
/gradle
gradlew
gradlew.bat
...
```

* Java中

```
*.class

# package
*.war
*.ear

# kdiff3
*.orig

# maven
target/

# idea
.idea/
/idea/
*.ipr
*.iml
*.iws

# temp
*.log
*.cache
*.diff
*.patch
*.tmp

# system
.DS_Store
Thumbs.db
```


#### 2. 新建README.md
>README.md：用于对项目的介绍，以及项目部署或者使用的教程相关，markdown文件。

#### 3. 创建远程仓库
这里使用码云作为Git的远程仓库（免费，而且可以创建私有项目）
[码云 ](https://gitee.com/)

![](img/in-post/git_project_created.png)

创建完成后如图
![](img/in-post/git-project-init.png)

#### 4. 创建本地项目
以一个简单的Java 项目作为例子，新建一个Maven webapp项目，并给定java source目录，resources目录，以及测试目录：

![](img/in-post/git-project-local-1.png)

##### 新建.gitignore和README.md文件

```
touch .gitignore
touch README.md
```
![](img/in-post/git-project-local-2.png)

   在.gitignore文件中输入上文忽略文件
   在README.md写入初始化项目介绍
#### 5. 本地仓库初始化
##### 在项目控制台输入git init 在项目根目录初始化本地仓库

```
git init
```
##### 初始化成功后输入git status 查看初始化结果

```
git status
```
结果如下图
![](img/in-post/git-project-local-3.png)

##### 输入 git add . 添加所有变更文件,然后查看状态

```
git add .
git status
```
![](img/in-post/git-project-local-4.png)
项目文件颜色变为绿色
![](img/in-post/git-project-local-5.png)

##### 输入git commit -am "这是提交消息"`(提交消息是单引号包裹,数字键1左边那个按键)`

```
git commit -am `my project first commit`
```
提交后如下图
![](img/in-post/git-project-local-6.png)

##### 添加远程仓库
远程仓库地址在我们码云新建立的项目地址
![](img/in-post/git-project-local-6.png)

```
git remote add origin git@gitee.com:HaShiQiKeJi/GitDemo.git
```

git remote -v 查看我们添加的远程仓库

```
git remote -v
```
![](img/in-post/git-project-local-7.png)

##### 向远程仓库推送本地代码

```
git push -u origin master
```
如果不出意外,会提示你远程仓库文件需要git pull ... 后再提交

![](img/in-post/git-project-local-8.png)


再次输入命令

```
git push -u origin master
```
提示我们本地版本仓库的版本低于远程仓库的版本

这时候我们进行强制推送

```
git push -u -f origin master
```

![](img/in-post/git-project-local-9.png)


###### 一般来说我们平时在新建好远程仓库后，在建立本地项目时，可以直接从远程仓库通过git新建项目，具体怎么选择，就看具体的使用场景。

