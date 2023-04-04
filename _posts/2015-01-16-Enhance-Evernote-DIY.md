---
id: 280
title: '自己动手对 Evernote 进行一些小增强'
date: '2015-01-16T12:43:20+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/280'
duoshuo_thread_id:
    - '6275546040867226370'
v2press_who_bookmarked_me:
    - 'a:1:{i:0;i:333;}'
mytory_md_visits_count:
    - '174'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/15/150116%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E5%AF%B9%20Evernote%20%E8%BF%9B%E8%A1%8C%E4%B8%80%E4%BA%9B%E5%B0%8F%E5%A2%9E%E5%BC%BA.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
mytory_md_path_old:
    - 'https://github.com/wandero/blog/raw/master/15/150116%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E5%AF%B9%20Evernote%20%E8%BF%9B%E8%A1%8C%E4%B8%80%E4%BA%9B%E5%B0%8F%E5%A2%9E%E5%BC%BA.md'
categories:
    - Evernote
tags:
    - Evernote
---

（本篇无多少干货，ahk 脚本也写得蹩脚，抛砖引玉）

## 操作方面

Evernote 虽然提供了大量的程序内热键，但却无法修改，对此不折腾会死星人和手残人士都有些无法接受，出动 AutoHotKey 大神势在必行。

<!-- more -->

### **排版**

Evernote 的排版这里就不吐槽了，个人常用情景是对剪辑内容纯文本简化格式，然后对小标题之类加粗，实在需要缩进什么的 Tab，这样基本满足阅览需求又不需要花费多少精力在版面上，毕竟对于 Evernote 内的笔记，这是一个频繁变动的世界，每次调整都可能意味者原有版面的支离破碎）

**Alt+1 简化格式** （代替默认的 设为纯文本后简化格式，需要注意的是手误按下破坏了原有的大好版面时不要抓狂，连续两次 Ctrl +z 就原地复活了 ）

**Alt+2 加粗整行**（替换默认的 选定整行 后 Ctrl+B，注意这个功能是基于光标位置实现的）

**Alt+3 淡化整行**（代替默认的 选中整行 后 点击字体颜色图标来改变字体配色)，该功能可以用来代替复选框或删除线（既然事项已完成，就应该淡化掉，从美观和效率角度都是最好的做法）。注意该功能是基于屏幕坐标的鼠标动作实现，仅用于 Evernote 主窗口，代码仅限于参考，实际使用需要结合 AutootKey 的 Window Spy 功能调整。另外，在不同分辨率的桌面环境中，遇到这种基于屏幕坐标实现的功能时，可以配置随系统启动的独立脚本（配合通用脚本）以适应具体环境）

```
#IfWinActive ahk_class ENMainFrame;Evernote主窗口
$!1:: ;格式化
Send ^+{Space}
Send ^{Space}
return
$!2:: ;加粗整行
click 3
send ^b
return
$!3::  ;淡化整行
click 3
Click 850,160
click 845,250
return
#IfWinActive

#IfWinActive ahk_class ENSingleNoteView;笔记独立窗口
$!1:: ;格式化
Send ^+{Space}
Send ^{Space}
return
$!2:: ;加粗整行
click 3
send ^b
return
#IfWinActive
```

### **整理**

整理是 Evernote 应用的重要组成部分，对剪辑或添加的零散信息，合并与调整笔记本位置是会频繁用到的功能，启用 ahk 后，可以实现 F1 打开移动笔记本窗口，然后键入数字序号来选定笔记本。（ [Evernote 的信息组织结构](http://cloudlet.info/t/279) 命名原则中提到的快捷操作）因为采取的 02-20 对应命名规则，输入 2-9 可以通过序号数位数字直接定位资料组笔记本，输入 02-06 定位行动组笔记本，如果和前一则笔记移动的笔记本相同，无需输入即可定位，之后回车，移动完成，自动切换至下则笔记，继续）

**F1** （在笔记内或笔记列表面板）**打开“移动到笔记本窗口”**(替换默认的 （ESC +） AppsKey/右键 +v）  
**Enter**（在移动到笔记本窗口，输入数字选定笔记本后）确认（替换默认的Alt+O)

```
#IfWinActive ahk_class ENMainFrame
$f1::
send {Esc}
Sleep, 10
send {AppsKey}
send V
return
#IfWinActive

#IfWinActive , 移动笔记到笔记本
$enter::
Send !+o
return
#IfWinActive
```

### **输入法开关**

**Ctrl + Space** 这种热键也能出现在已经独立运营的国内版本软件中，可见印象笔记的本地化程度……虽然在之前的脚本中已经用 Alt +1 实现了格式化功能，但在程序内无法切换输入法也是非常别扭的，不用 ahk 的话可以将输入法切换热键改为 Ctrl + Shift 之类凑合，但最优的解决方案仍然是…… ahk，先将输入法切换热键改为 Ctrl + Shift ，然后将全局 Ctrl + Space 映射为 Ctrl + Shift（或者随便什么冷僻的组合热键，这样可以保留一个宝贵的顺手的热键）

```
$^Space::
send ^{shift}
return
```

### **搜索**

习惯了浏览器选定文字下拉即可搜索之类便利功能的用户显然不会满意 Evernote 这类重要信息处理源居然没有该项功能，继续 ahk。

**Alt+F1** （新增功能）在浏览器中搜索选定文字/打开选定网址

（这里插一句，类似的日常脚本完全可以设置为常驻脚本，开机启动，珍惜生命，减少 apm）

```
$!f1::
send ^c
SetTitleMatchMode 2
WinActivate, 枫树极速浏览器;好吧，我还在坚守这款被开发者抛弃快两年的神器
send ^k
send {AppsKey}
send {enter}
send {enter}
send {enter}
return
```

## 模板方面

Evernote 的排版实在是寒碜，如果一定要实现顺眼的版面，有没有什么办法呢？答案是……粘贴/剪辑……

从 Word 粘贴/剪辑，从 Excel 粘贴/剪辑，从 MarkdownPad 粘贴/剪辑，从浏览器粘贴/剪辑，从 Evernote clearly 粘贴/剪辑（是的，你没有看错，从 cleary 粘贴和使用 clearly 剪辑出来的版面是完全不同的）， 从 Pocket web 端粘贴/剪辑……另外剪辑和粘贴的版面很多时候也是完全不同的……

当然，实际上因为这种版面无法维持（继续编辑经常会破坏版面），所以和 Evernote 笔记轻便灵活且能够不断修改完善的主旨是有所冲突的，是否需要如此折腾就见仁见智了。