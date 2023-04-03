---
id: 199
title: 'Codecademy 等站点的光标错位问题'
date: '2013-09-30T11:55:04+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/199'
permalink: /2013/09/30/codecademy-%e7%ad%89%e7%ab%99%e7%82%b9%e7%9a%84%e5%85%89%e6%a0%87%e9%94%99%e4%bd%8d%e9%97%ae%e9%a2%98/
duoshuo_thread_id:
    - '6275546013704913665'
mytory_md_visits_count:
    - '47'
categories:
    - Notes
tags:
    - ahk
---

用强制（或修改过）页面字体的浏览器浏览 Codecademy 等站点时，会出现页面编辑器光标错位的情况，感觉是默认字符宽度的设定造成的（使用 Stylish for Chrome 时这种问题也很明显）

<!-- more -->

正面解决方法尚未发现，侧面的话，或者使用未强制字体的浏览器（糟糕的浏览体验），或者……使用 Sublime Text 和复制粘贴……

附上一段方便此类操作的ahk代码  
（在 ST 中按 F1 会全选当前代码将其复制到 Codecademy 代码窗口中并自动执行，在 Codecademy 中按 F2 会全选当前代码并复制到 ST中）

```
    $F1::
    if WinActive("ahk_class PX_WINDOW_CLASS")
    send ^a
    send ^c
    SetTitleMatchMode 2
    WinActivate, Codecademy
    send ^a
    send ^v
    send ^{Enter}
    Return

    $F2::
    if WinActive("ahk_class Chrome_WidgetWin_1")
    send ^a
    send ^c
    SetTitleMatchMode 2
    WinActivate, Sublime
    send ^a
    send ^v

```