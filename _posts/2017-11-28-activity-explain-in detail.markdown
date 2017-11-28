---
layout:     post
title:      "Activity详解"
subtitle:   ""
date:       2017-11-28 12:00:00
author:     "lcy"
header-img: "img/post-bg-nextgen-web-pwa"
---

# Activity详解
在日常应用中，Android是与用户交互的接口，它提供了一个界面，让用户进行点击，滑动等操作；
### 一. activity生命周期
#### 1. activity的4种状态
* running：表明activity处于活动状态，用户可以点击屏幕，屏幕会做出响应，它是activity处于栈顶的一个状态；

* paused：表明activity失去焦点时的状态，它是被一个非全屏的activity占据或者被一个透明的activity覆盖；处于可见，但是失去了和用户交互的能力；（正常情况下它的成员变量这些都还存在，但是在内存紧张的情况下可能会被回收）

* stopped：activity被另一个activity完全覆盖的时候，被覆盖的activity就处于stopped的状态，不再对可见；（它的一些内存状态信息和成员变量等都有可能存在，在内存紧张的情况下，它可能会被回收）

* killed：activity已经被系统回收掉了，就会处于killed这个状态

#### 2. activity生命周期分析
![](https://imgsa.baidu.com/exp/w=480/sign=fc075ffcaeaf2eddd4f148e1bd110102/5fdf8db1cb134954832dc99e544e9258d1094a1c.jpg)

* activity启动->onCreate()->onStart()->onResume()

* 点击Home键回到主页面（activity不可见）->onPause()->onStop()

* 当我们再次回到原Activity时：->onRestart()->onStart()->onResume()

* 退出当前Activity时：->onPause()->onStop()->onDestroy()

#### 3. android的进程优先级
    前台/可见/服务/后台/空

### 二. activity任务栈
![
](http://img.blog.csdn.net/20141224210418616?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvZ3VvbGluX2Jsb2c=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
### 三. activity启动模式
#### 1. Standard：
activity默认启动模式，将当前启动的activity加入栈顶；

#### 2. SingleTop：
栈顶复用模式，当前启动activity在整个任务栈的顶端,则复用当前栈顶的activity实例，并回调onNewIntent()方法；

#### 3. SingleTask：
检测整个任务栈中是否存在当前启动activity的实例，如果存在,则直接将activity置于栈顶,并且将此activity以上的所有activity都从任务栈中移出，并且回调onNewIntent()方法；

#### 4. SingleInstance：
此activity在所有任务栈中只存在一个实例，并且这个示例独享一个任务栈；（用的比较少，类似通讯录）

### 四. scheme跳转协议
Android中的scheme是一种页面内跳转协议，是一种非常好的实现机制，通过定义自己的scheme协议，可以非常方便跳转app中各个页面；通过scheme协议，服务器可以定制化告诉App跳转到哪个页面，可以通过通知栏定制化跳转页面，可以通过H4页面跳转页面等。



