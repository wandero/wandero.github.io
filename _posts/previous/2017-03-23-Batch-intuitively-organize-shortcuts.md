---
id: 438
title: 批量直观整理快捷方式
date: '2017-03-23T15:12:57+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/438'
mytory_md_visits_count:
    - '79'
mytory_md_path:
    - 'https://raw.githubusercontent.com/wandero/blog/master/17/170323%E6%89%B9%E9%87%8F%E7%9B%B4%E8%A7%82%E6%95%B4%E7%90%86%E5%BF%AB%E6%8D%B7%E6%96%B9%E5%BC%8F.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
mytory_md_path_old:
    - 'https://raw.githubusercontent.com/wandero/blog/master/17/170323%E6%89%B9%E9%87%8F%E7%9B%B4%E8%A7%82%E6%95%B4%E7%90%86%E5%BF%AB%E6%8D%B7%E6%96%B9%E5%BC%8F.md'
categories:
    - 工具二三
tags:
    - win10
---

不使用 Win + R 大法的同学可能很少有这种诡异的需求，所以先解释一下神器级的 Win + R

<!-- more -->

## Win + R （快速启动应用程序）

## 优点

快速开启指定应用程序（闭眼敲几下键盘即可）

保持桌面清爽（一个快捷方式都没有）

无需安装额外软件（系统原生支持）

## 实现

### 建立 links 文件夹

建议非系统盘，方便独立于系统复用

### 将 links 文件夹路径加入系统变量

（计算机-属性-高级系统设置-环境变量-系统变量-Path）变量值中填入 links 路径（例如 D:syslinks，注意之前加分号分隔）

### links 文件夹内放置重命名的快捷方式

例如将原本在桌面的快捷方式 cloudlet.link 剪切至 links，重命名为 c.lnk

（重命名规则，可以将单字母分配给高频应用，双字母组合分配给其他应用，足够一般使用，另外注意系统 path 变量中已有的文件夹内的文件名也会被触发）

### 使用自定义按键开启指定程序

Win + R 呼出系统运行窗口（几乎可以在任何窗口启动），键入 C，回车，cloudlet.info 程序启动

（其实这里不用局限于程序，任意能建立快捷方式的文件都可以操作，比如一些频繁使用的 Excel 文件，不使用 TotalCMD 的情况下的频繁打开的文件夹，等等）

## links 文件夹快捷整理

因为 links 文件夹可以独立于系统安装而重复使用，日积月累会产生大量失效快捷方式，一个个去右键甄别显然繁琐，这个时候 Windows（7）的原生功能出场了：

将 links 文件夹切换为「详细信息」视图

在名称、修改日期、类型、大小那一行右键，弹出菜单中选择「其他」

在「选择详细信息」中勾选「链接目标」，收工

## links 文件夹快捷整理

[LiNK Fixer](http://corz.org/windows//software/accessories/LiNKFixer.php) 这个小软件可以批量修改指定文件夹内的快捷方式路径