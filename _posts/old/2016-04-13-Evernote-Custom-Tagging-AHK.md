---
id: 368
title: 'Evernote 半自动添加自定义标签（ahk）'
date: '2016-04-13T15:56:48+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/368'
duoshuo_thread_id:
    - '6275546055127859970'
mytory_md_visits_count:
    - '48'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/16/160413Evernote%20%E5%8D%8A%E8%87%AA%E5%8A%A8%E6%B7%BB%E5%8A%A0%E8%87%AA%E5%AE%9A%E4%B9%89%E6%A0%87%E7%AD%BE%EF%BC%88ahk%EF%BC%89.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
mytory_md_path_old:
    - 'https://github.com/wandero/blog/raw/master/160413Evernote%20%E5%8D%8A%E8%87%AA%E5%8A%A8%E6%B7%BB%E5%8A%A0%E8%87%AA%E5%AE%9A%E4%B9%89%E6%A0%87%E7%AD%BE%EF%BC%88ahk%EF%BC%89.md'
dotGood:
    - '1'
categories:
    - 工具二三
tags:
    - AHK
    - Evernote
---

在剪辑大量材料的时候，个人通常为了方便直接用一个原生标签，这样会给后期处理（原生标签转换成自定义便签）带来很多麻烦，今天突然意识到这个仍然可以用简单的 Autohotkey 脚本解决。

（自定义标签为个人提法，详见 [Evernote 的信息组织结构](http://cloudlet.info/t/279)）

<!-- more -->

## 效果

（将笔记列表切换为摘要视图非更新时间排序模式）复制需要添加的自定义标签内容，在一则笔记末尾按下 F1，自动切换至下则笔记添加自定义标签。之所以选择笔记内部位置和使用 Loop 1 是为了方便添加其他非自定义标签。如果仅仅是批量添加特定标签可以将 Loop 1 修改为 Loop n 自动循环。

非常简单的代码，实现了非常省事的功能，又一个腾出原生标签的理由……

## 代码

```
; 自动添加自定义标签
; 可将 F1 修改为其他热键，可将 Loop 次数更改为其他值
$F1::
Loop, 16
{
    send, {esc}
    sleep,500
    send,{down}
    sleep,500
    send {enter}
    Sleep, 500
    Send, {CTRLDOWN}{END}{CTRLUP}
    sleep,100
    send {enter}
    sleep,100
    send {enter}
    sleep,100
    send, %Clipboard%
}
return

;F2 中止脚本，防止误操作
$F2::reload 
```