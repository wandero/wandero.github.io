---
id: 389
title: '[AHK] Typora-Evernote 自动复制粘贴脚本'
date: '2016-08-30T09:36:05+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/389'
duoshuo_thread_id:
    - '6324429388200805121'
mytory_md_visits_count:
    - '1058'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/16/160830%5BAHK%5D%20Typora-Evernote%20%E8%87%AA%E5%8A%A8%E5%A4%8D%E5%88%B6%E7%B2%98%E8%B4%B4%E8%84%9A%E6%9C%AC.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
mytory_md_path_old:
    - 'https://github.com/wandero/blog/raw/master/160830%5BAHK%5D%20Typora-Evernote%20%E8%87%AA%E5%8A%A8%E5%A4%8D%E5%88%B6%E7%B2%98%E8%B4%B4%E8%84%9A%E6%9C%AC.md'
dotGood:
    - '3'
categories:
    - Notes
tags:
    - ahk
    - Evernote
    - Markdown
    - typora
---

# 说明

很简陋的代码，只是把热键串了下，操作方便一些。中间想添加 Typora 无空白文档自动新建一个的功能发现 `#IfWinNotExist` 无法精确匹配，还是那句，抛砖引玉

<!-- more -->

# 代码

```
#IfWinActive, Typora
{
    !q::
    send ^a
    send ^c
#IfWinActive, Typora
{
    ;在 Typora 窗口 alt+q 会将当前内容全选复制至 Evernote 笔记内
    !q::
    send ^a
    send ^c
    WinActivate, 印象笔记
    Sleep, 200
    ; send ^m
    ; Sleep, 200
    send ^a
    send ^v
    Return
}

#IfWinActive ahk_class (ENSingleNoteView|ENMainFrame)
{
    ;在 Evernote 笔记窗口  alt+q 会将当前内容全选复制至 Untitled - Typora 窗口
    !q::
    send ^a
    send ^c
    #IfWinExist, Untitled - Typora
        {
        WinActivate, Untitled - Typora
        send ^a
        send ^v
        }
    return
}
```