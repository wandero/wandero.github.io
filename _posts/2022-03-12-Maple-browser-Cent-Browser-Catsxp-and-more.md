---
id: 1123
title: '枫树浏览器、Cent Browser、Catsxp……'
date: '2022-03-12T20:48:56+08:00'
author: Zephur
layout: post
guid: 'https://cloudlet.info/?p=1123'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/22/220312%20%E6%9E%AB%E6%A0%91%E6%B5%8F%E8%A7%88%E5%99%A8%E3%80%81Cent%20Browser%E3%80%81Catsxp%E2%80%A6%E2%80%A6.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
dotGood:
    - '1'
categories:
    - 工具二三
tags:
    - Chrome
    - 'Cent Browser'
    - Mactype

---

**220801 UPDATE**

**Cent Browser 更新！！！**又能再战三年？……

目前 Catsxp 的 Mactype 渲染聊胜于无， GDIChromium 的有等于无……，其他功能更是完全被 Cent 碾压，特别是设置同步，下文没必要看了……

<del>转眼又是六年（[什么样的壳浏览器才是好的壳浏览器](https://cloudlet.info/t/369)），枫树浏览器之后，又需要寻找百分浏览器的替代者了……</del>

- - - - - -

<!-- more -->

## Cent Browser

（先盘点下个人觉得比较重要的 Cent Browser 的独特功能）

- 字体渲染，支持关闭 Directwrite（从而支持 Mactype 渲染）
- 自定义样式，系统级支持自定义 custom.css
- 支持调用 IDM 并且支持热键临时禁用 IDM（使用内置下载）
- 自动显示隐藏书签栏
- 隐藏标签页关闭按钮
- 双击关闭标签页
- 支持书签栏悬停切换（打开书签栏一个文件夹后，鼠标移动到其他文件夹上能自动打开）
- 内置鼠标手势和超级拖拽，好用的「下一页（论坛）」手势和还算好用的添加书签手势
- （缺点）鼠标手势略简单，没有三段手势
- （缺点）一年多没更新了
- （缺点）新机制下似乎无法同步配置了

## Catsxp

虽然六年过去，市面上不乏大牌靠谱的 Edge（大声朗读完美）、Brave（据说安全隐私强）、Vivaldi ，但是定制性方面习惯了 Cent Browser 的用户很难适应一般浏览器，近期在 Cent 习惯性断更又习惯性的搜索之后 ，发现了猫眼浏览器 Catsxp （v2.3.4），尝试了下，感觉如下：

- （没法关闭 Directwrite）字体渲染部分只能使用 Mactype 助手勉强解决页面部分的字体渲染，但页面以外，如标签栏、书签栏、系统界面都无能为力
- 没有系统级的支持 custom.css
- 调用下载工具功能实测无效
- （目前版本 BUG） 下载按钮开启的下载内容面板在碰到相同文件询问保留舍弃时，选择保留会导致浏览器崩溃
- 不支持隐藏书签页状态下的书签栏悬停切换（显示书签页状态下正常）
- Catsxp 虽然也有简单的鼠标手势和超级拖拽（未实测），但没有「 下一页（论坛）」
- 外观还是有点丑（特别是各种图标风格，太喧宾夺主了）
- （优点）自动显示隐藏书签栏、隐藏标签页关闭按钮、双击关闭标签页都已实现
- （似乎）有独立的同步功能（具体同步内容未测试）
- （优点）更新快

## 最后

最后……还是继续坚持 Cent Browser，整体协调的外观还是太重要了……希望 Catsxp 能够尽快超越 Cent Browser，当然如果能够提供 GDI 支持（禁用 Directwrite） 就可以马上弃暗投明了……

顺便，只对字体渲染有执念而对定制性没有要求的话，可以考虑 [GDIChromium](https://github.com/GTANAdam/GDIChromium)（仅为 Chromium 增加了 GDI 支持，代价是新机制下无法同步配置了）