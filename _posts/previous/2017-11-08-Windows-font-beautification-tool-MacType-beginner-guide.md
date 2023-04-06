---
id: 821
title: 'Windows 字体美化神器 MacType 简易上手指南'
date: '2017-11-08T22:16:51+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/?p=821'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/17/171108%20Windows%20%E5%AD%97%E4%BD%93%E7%BE%8E%E5%8C%96%E7%A5%9E%E5%99%A8%20MacType%20%E7%AE%80%E6%98%93%E4%B8%8A%E6%89%8B%E6%8C%87%E5%8D%97.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
dotGood:
    - '15'
mytory_md_path_old:
    - 'https://github.com/wandero/blog/raw/master/17/171108%20Windows%20%E5%AD%97%E4%BD%93%E7%BE%8E%E5%8C%96%E7%A5%9E%E5%99%A8%20MacType%20%E7%AE%80%E6%98%93%E4%B8%8A%E6%89%8B%E6%8C%87%E5%8D%97.md'
categories:
    - 方法一二
tags:
    - Mactype
    - win10
---

> **环境** 桌面 Winows 7，浏览器 Centbrowser
> 
> **思路** 使用热替换模式安全无损地消灭宋体，美化桌面和绝大部分软件界面

<!-- more -->

## 基本操作

### 安装渲染字体包

下载 Max@themex.net 制作的 XHei Believe 字体包，原发布地址已失效，请自行搜索 IoF\_20140711\_103833 （IoF 字体集最终版）。将「01：IoF 字体集 – XHei\_Believe + webOS – XHei\_Believe」中的 simsun.ttc 以外的 6 个字体文件拷出安装（「双击字体 – 点击安装」 或将字体拷贝至系统字体文件夹）

### 安装设置 MacType

进入 [MacType 官网](http://www.mactype.net/) 下载 MacType 程序并安装（当前版本为 2017\_0628，安装之前确保完全卸载老版本 MacType 并重启）

加载方式选择「注册表方式加载」（不建议使用其他加载方式）

配置文件选择 「IoF – HotShift – HotShift→XHei… – Believe」

### 重启系统

重要，虽然大多时候注销即可，但建议重启以使其完全生效

### 设置软件字体

将（能够调整字体的）软件字体设置为 XHei Believe（等宽字体处修改为 XHei Believe Mono）。使用 Stylish 等界面扩展的可自行修改脚本字体设置。另，不需关闭 Windows 的 ClearType

## 进阶操作

### 选择其他替换字体

当前版本的 MacTpye 已经内置了所有 20140711 IoF 字体集的配置文件，在前面提到的字体集中也已经包含 IoF 系列的全部字体，安装目标字体包中的 3 个同名字体（不包括 simsun 以及 XXX 字体），在 MacType （程序 – MacType 用户向导 – 下一步）中切换至对应配置文件（注意是选择 IoF 根目录下 HotShift 文件夹内的配置文件，有「热替换为……」字样），设置后注销/重启使其配置生效

### 调整字体替换规则

配置文件默认设定了一系列的字体替换规则，如果不想某些字体被替换，可以在配置文件的 \[FontSubstitutes\] 中的【字体替代】或【扩展的字体替代】部分中删除该替换规则

### 排除不兼容软件

一些不兼容 MacType 的软件运行时可能出现乱码、报错甚至崩溃，碰到此类问题可以在不关闭软件进程的情况下在 MacType 的「进程管理」（「MacType 用户向导」左下角）中选择相应进程，右键选择 「排除此进程」或 「不对此进程替换字体」。

例如设置 MacType 后网易云音乐出现「云音乐进程崩溃，程序将终止运行」问题，对 cloudmusic.exe 设置「不对此进程替换字体」后即可解决。

也可以直接在配置文件（如 `MacType\ini\Believe.ini`）中的 `\[UnloadDll\]` 部分添加进程名（如 cloudmusic.exe）实现同样的效果。（建议单独复制一份 Believe.ini 使用，方便修改和复用，也不会因软件重装等情况被覆盖）

### 还原软件替换字体

解决方法同上，在「进程管理」中选择 WINWORD.EXE ，设置「不对此进程替换字体」即可

## 其他

说起来 MacType 也用了几年，但之前因为硬替换导致的 Word 字体变化和一些诡异的系统问题只是对其字体替换功能浅尝辄止，实在是暴殄天物……最近因为实在无法忍受 GnuCash 的默认字体界面而重新折腾了一番——目前 GnuCash 的文字渲染大赞

Windows 7 中使用 DirectWrite 的软件不多，绝大多数软件都能取得不错的渲染效果（连因为大量剪辑保留了原始样式而比较乱的 Evernote 都受到了小幅的加成）。 而对于不幸使用了 DirectWrite 的 Chrome 和 Electron 系应用，渲染效果则要大打折扣，新版 Typora 渲染效果较差，Pomodone 使用默认替换规则会出现图标显示为文字的问题，等等

XHei Believe 是由「方正兰亭细黑」中文部分和「Gotham book」英文部分合成而来，个人感觉比微软雅黑、XHei\_OSX、XHei\_Apple 要养眼不少，不习惯的可参考字体集中的海报 PDF 自行选择