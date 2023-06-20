---
layout: post
title: "使用 AHK 自动跳过 Supermemo 18 报错"
date: 2023-05-26 21:00:00 +0800
categories: 工具二三
tags:
    - AHK
    - SuperMemo

---

SuperMemo 作为一款间隔重复记忆软件，其神器属性自不待言，但是软件问题也是史诗级别的，层出不穷的报错窗口让人十分无奈，还好有 AutoHotKey，直接上代码

<!-- more -->

```
#Persistent
SetTimer, CheckErrorWindows, 100

CheckErrorWindows:
    IfWinExist, Error!
    {
        IfWinNotExist, Fatal Error!
        {
            WinActivate, Error!
            Send, !o
        }
    }
    Else IfWinExist, Fatal Error!
    {
        WinActivate, Fatal Error!
        Send, {Left}
        Send, {Enter}
    }
return
```

将改代码保存为 monitor.ahk，开机启动即可自动跳过 Supermemo 的各种报错弹窗，但按键快了的话还是可能误操作退出 SuperMemo，不知道 SM 19 什么时候能出以及出了有无改善……