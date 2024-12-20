---
id: 1089
title: 鼠标手势扩展和移除书签功能实现
date: '2021-12-19T21:25:10+08:00'
author: Zephur
layout: post
guid: 'https://cloudlet.info/?p=1089'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/21/211219%20%E9%BC%A0%E6%A0%87%E6%89%8B%E5%8A%BF%E6%89%A9%E5%B1%95%E5%92%8C%E7%A7%BB%E9%99%A4%E4%B9%A6%E7%AD%BE%E5%8A%9F%E8%83%BD%E5%AE%9E%E7%8E%B0.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
categories:
    - 工具二三
tags:
    - chromext
---

MouseStroke 之后一直没有找到完全满足要求的 Chrome 鼠标手势扩展，SmartUp 虽然能够移除书签，但添加书签却只能添加到其他书签文件夹内，而其他书签又不支持点击其他书签文件夹后鼠标悬停展开。更严重的是总有些页面出这样那样的问题，虽然自定义设置强大，但用起来还是够呛。

<!-- more -->

也试过 crxMouse 其他主流鼠标扩展，总有些不顺手，无奈用回 Centbrowser 内置的鼠标手势，优点是浏览器原生支持，基本能在所有页面工作；下一页功能兼容性优异。缺点是只支持两段手势，功能有限，再加上最难受的不支持移除书签。

然后继续尝试 MouseGestureL.ahk、Stroke、StrokesPlus.net 之类全局手势，感觉还是无法解决该问题。最终发现陷入了思维误区，这个功能不是一定要用鼠标手势来实现，于是祭起 AutoHotKey 大法：

```ahk
    #IfWinActive, ahk_class Chrome_WidgetWin_1
    {
        ; Ctrl+D 移除本页面书签
        {
            $^d::
            send ^d
            send {tab}{tab}{tab}{tab}
            send {enter}
            return
        }
    }
```