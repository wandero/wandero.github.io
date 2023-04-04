---
id: 171
title: 'Stylish 简易上手指南'
date: '2013-06-06T18:20:49+08:00'
author: Zephur
layout: post
guid: 'http://foro.cloudlet.info/t/171'
duoshuo_thread_id:
    - '6275546006448767746'
mytory_md_visits_count:
    - '681'
dotGood:
    - '2'
categories:
    - 方法一二
tags:
    - Chrome
---

（老实说个人这种代码盲写起这种题目来实在是不胜惶恐，不过网上似乎没有这种基础性的东西，所以勉力简单的总结下）

## 简介

Stylish是一款浏览器扩展，在 Chrome 、 Firefox 、 Opera 上均有相应版本。作用是重置相关页面的CSS从而实现定制站点外观的功能。

[userstyles.org](http://userstyles.org/) 是 Stylish 的配套站点，Stylish 用户可以在这里分享自己制作的站点样式。

<!-- more -->

## 用法

下面以 Chrome 为例简单介绍一下用法

Stylish – 管理已安装的样式 – 写入新样式

应用对象：指定 \[相关网页\] 添加  
代码：\[相关代码\]

填入名称，勾选启用，保存样式即会在指定页面生效。

## 代码

相关代码（语法）实际上就是一份 CSS 样式表，不过一般都加上 !important 强制样式生效。

CSS 样式表则是各条 CSS 规则的集合，而具体的 CSS 规则由选择器和声明组成。例如

```
    #top { display: none !important }

```

这条 CSS 规则包括 #top （选择器）、display （属性）、none（值），而作用是隐藏页面中 ID 为 top 的元素。

在简单的 Stylish 样式中，我们用的比较多的选择器是 #id 和 .class ，用的比较多的声明是 { display: none !important }

## 初步

以上简单介绍了 Stylish 的原理和用法，但对初步接触 Stylish 和 CSS 的用户，还有一个比较重要的问题：如何获取我们希望隐藏或处理的元素信息呢？

接下来我们可以祭出各类网页审查工具了，继续以 Chrome 自带的审查元素工具为例：

在本页面页脚右键选择审查元素，即可打开 Developer Tools 工具，挪动下鼠标可以看到页面选择区域会更根据鼠标指向的元素而变化。

左键单击 `div class="container"` ，选中整个 .container，在 工具界面右侧我们可以看到相关选择器的属性如下

```
    .container {
    background: #fff /*@url("images/bg-footer.png") no-repeat right center*/;
    }

```

（点击#fff前的白色方块换个颜色看看效果？）

接下来我们可以在这行代码中（}之前）加入 display: none 看看效果

（注意：这种在 Developer Tools 中进行的修改只是临时性的，页面刷新即会消失；另一方面，在 Developer Tools 中进行的修改在未刷新页面前可能和 Stylish 中的样式发生冲突从而干扰测试结果）

ok，测试通过，我们现在知道在 cloudlet.info 这个站点，如果想隐藏页脚，元素选择器应该使用 .container ，声明使用 display: none，回到 Stylish 的代码界面，将

```
    .container {
    display: none !important;
    }

```

写入代码区，保存样式，针对 cloudlet.info 的简单样式修改完工。

## 进阶

1. \[#id\], \[.class\]可以用来合并使用相同声明的规则
2. .class1.class2可以用来匹配.class1 class2这种元素
3. DIV\[style=”%”\] （%代表元素属性）形式可以用来匹配无 id 无 class 但有特殊样式（不至于轨道炮）的元素
4. DIV\[id^=%\] DIV\[class^=%\]可以用来匹配以%开头的元素
5. DIV\[%1\]:nth-child(1)&gt;DIV\[%2\]:nth-child(2) （第一个%1声明的div元素内的第二个%2声明的div元素）可以用同级元素顺序及上下级元素从属来匹配元素
6. opacity 属性是个很赞的声明，设定合适的透明度有助于大幅提升浏览体验
7. div\[%1\] { opacity: 0 } div\[%1\]:hover { opacity: 1 }可以实现元素淡出鼠标悬停时才显示的效果
8. 页面中的iframe需要针对其原始url（而非当前页面）写选择器

基本上，熟悉以上用法就可以在很大程度上根据自己的意愿定制我们看到的大多数网页了，在这个过程中对 CSS 不清楚的地方可以参考**[ CSS 参考手册](http://www.w3school.com.cn/cssref/index.asp) [ CSS 选择器参考手册](http://www.w3school.com.cn/cssref/css_selectors.asp)**等资料。