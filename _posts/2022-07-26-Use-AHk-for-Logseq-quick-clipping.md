---
id: 1152
title: '使用 AHk 实现 Logseq 快速剪辑'
date: '2022-07-26T22:07:22+08:00'
author: Zephur
layout: post
guid: 'https://cloudlet.info/?p=1152'
categories:
    - 工具二三
tags:
    - Logseq
    - AHK
---

Logseq 没有快速剪辑功能，使用起来很不方便，好在有万能的 AHK，感谢 [及时春雨的脚本（Obsidian&amp;Logseq等软件联动 AHK加速脚本使用详解）](https://www.bilibili.com/video/BV1vY411T711?spm_id_from=333.337.search-card.all.click&vd_source=3c6810b837c319a08af0b805d3d2a19d)，不过这个脚本里面功能太多，只山寨了一段，主要用于 Logseq 的快速剪辑（Win+A 快速剪辑选中内容至 Logseq 当日 Journals 末尾，网页内容额外添加原文链接），另外支持了一下快捷随机页面和删除（F1 触发 Ramdom Note 扩展打开随机页面功能，注意受输入法状态和 Caps Lock 大写影响；F2 删除当前页面并打开下一随机页面，点击坐标需要结合屏幕调整）。

<!-- more -->

```
      SetTitleMatchMode, Regex ;正则表达式

      ;------初始化配置------;
      #NoEnv  ; Recommended for performance and compatibility with future AutoHotkey releases.
      SendMode Input  ; Recommended for new scripts due to its superior speed and reliability.
      SetWorkingDir %A_ScriptDir%  ; Ensures a consistent starting directory.
      #SingleInstance,Force
      FileEncoding, UTF-8-RAW

      JournalsFileFolder=c:\N\log\journals\

      ; Win+A 快速剪辑选中内容至 Logseq 当日 Journals 末尾，网页内容额外添加原文链接
      $#a::
      Loop
        Clipboard:=""
        Until (Clipboard="")
        Send ^c{Ctrl Up}
        ClipWait, 0.5

        IfWinActive, Cent
        {
            note = %clipboard%
            send {f6}
            sleep 100
            Send ^c{Ctrl Up}
            note = %note% [LINK](%clipboard%)
        }
        else
        {
            note = %clipboard%
        }

        if (ErrorLevel=0)
        {
            ;~ MsgBox Control-C copied the following contents to the clipboard:`n`n%clipboard%
            FormatTime, FileName, A_Now, yyyy_MM_dd
            FormatTime, TimeString, A_Now, HH:mm
            JournalsPathname = %JournalsFileFolder%%FileName%.md
            笔记内容0 := FileOpen(JournalsPathname, "r").Read()
            if  (笔记内容0 = "")
            {
                模板内容 := FileOpen(TemplateFile, "r").Read()
                FileOpen(JournalsPathname, "w").Write(模板内容) ;保存模板内容
            }
            ;~ MsgBox The specified date and time, when formatted, is %TimeString%.
            StringReplace, note, note, `r`n,   , All
            StringReplace, note, note, `n,   , All
            StringReplace, note, note, \, \\, All
            ;~ MsgBox, % note
            FileAppend, `n-  %note%, %JournalsFileFolder%%FileName%.md
            MsgBox, 0, , 保存成功, 0.5
        }
      return

      #IfWinActive ahk_exe Logseq.exe
      {

        ;F1 触发 Ramdom Note 扩展打开随机页面功能，注意受输入法状态和 Caps Lock 大写影响
        $f1::
        send {esc}
        send r
        send n
        return

        ;F2 删除当前页面并打开下一随机页面，点击坐标需要结合屏幕调整
        $f2::
        click 2404,90
        sleep 50
        click 2076,574
        sleep 50
        send {enter}
        sleep 50
        send r
        send n
        return
      }

```