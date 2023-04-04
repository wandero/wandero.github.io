---
id: 1214
title: 'Win 用 BAT 快速重启程序'
date: '2022-12-14T17:45:08+08:00'
author: Zephur
layout: post
guid: 'https://cloudlet.info/?p=1214'
mytory_md_path:
    - 'https://raw.githubusercontent.com/wandero/blog/master/22/221214%20Win%20BAT%20%E5%BF%AB%E6%8D%B7%E9%87%8D%E5%90%AF%E7%A8%8B%E5%BA%8F.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
categories:
    - Notes
tags:
    - win10
excerpt_separator: <!-- more -->
---

在某些场景中，需要重启程序（关闭再打开），可以使用批处理解决，BAT 代码如下

```bat
:: 重启 Tickeys
taskkill /im ticKeys.exe /f
start c:\O\Tickeys1.1.1\TicKeys.exe
exit

```

将该文件创建快捷方式（如 tk.lnk)（还可以在快捷方式的属性 快捷方式 中将运行方式设为最小化）

复制到（已写入系统环境变量的）快捷方式文件夹

Win+R 呼出运行面板，键入 tk 回车即可重启 Tickeys

注：Tickeys 在切换播放设备后异常（仍然在原设备播放）