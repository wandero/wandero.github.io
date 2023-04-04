---
id: 250
title: '低版本 Chrome 安装扩展方法'
date: '2014-08-06T21:22:37+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/250'
duoshuo_thread_id:
    - '6275546034022122242'
mytory_md_visits_count:
    - '61'
categories:
    - Notes
tags:
    - Chrome
---

#### 问题

Chrome 的扩展安装受到各种限制（目前似乎只能用高版本通过 webstore 安装），使用枫树之类低版本修改版的话，会出现无法安装扩展的问题。

<!-- more -->

#### 解决

安装一个 chrome……

使用 webstore 装好相应的扩展

通过ID 在用户配置文件夹中找到该扩展（不清楚位置可以搜索 ID ）

复制粘贴到任意位置，删除 \_metadata 文件夹

通过“加载正在开发的扩展程序”选择刚复制的文件夹的子目录（版本号那层，而非 ID 那层），确定，done

（注意加载后原粘贴出来的文件夹仍需保留，否则扩展会消失）