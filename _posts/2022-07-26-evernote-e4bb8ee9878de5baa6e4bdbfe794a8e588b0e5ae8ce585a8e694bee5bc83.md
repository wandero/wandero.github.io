---
id: 1149
title: 'Evernote 从重度使用到完全放弃'
date: '2022-07-26T21:13:02+08:00'
author: Zephur
layout: post
guid: 'https://cloudlet.info/?p=1149'
permalink: /2022/07/26/evernote-%e4%bb%8e%e9%87%8d%e5%ba%a6%e4%bd%bf%e7%94%a8%e5%88%b0%e5%ae%8c%e5%85%a8%e6%94%be%e5%bc%83/
mytory_md_path:
    - 'https://raw.githubusercontent.com/wandero/blog/master/22/220726%20Evernote%20%E4%BB%8E%E9%87%8D%E5%BA%A6%E4%BD%BF%E7%94%A8%E5%88%B0%E5%AE%8C%E5%85%A8%E6%94%BE%E5%BC%83.md'
mytory_md_text:
    - "# Evernote 从重度使用到完全放弃\n\n## 为什么放弃\n\n特地看了下，注册 Evernote 是 2009 年，重度使用应该是 2014 年接触 GTD 和电脑玩物的《Evernote超效率数字笔记术》 之后，十年时光恍然而逝，笔记不知所云，软件也物是人非了。  尽管 Evernote 似乎仍然是市场占有率最高的笔记软件，但早已暮气沉沉，积重难返。而对我个人而言，2022年的今天仍然使用的是 2015年6月的5.8.13 版本，实在不知道是 Evernote 的巨大成功还是巨大失败。\n\n作为一款老本吃了七八年（甚至可能还能吃几年）的笔记软件，Evernote 不可谓不成功，但时移世易，笔记软件的理念越来越现代、需求也越来越复杂，这款封闭且毫无进取心的软件早已落后于时代。如果说 OneNote 算古典笔记软件、Evernote 算传统笔记软件的话，以 Roam Research 和 Obsidian 为代表的新生代已经是现代笔记软件了。特别是 Obsidian 和 Logseq 等开源软件，依托强大的基础架构和无限可能的扩展系统，基本上在易用性以外的全部场景都能花式吊打 Evernote……\n\n## （如何放弃） 功能替代\n\n### 快速剪辑 ：AutoHotKey 脚本\n\nLogseq 没有原生的剪辑功能，论坛上还有很多用户反对增加剪辑功能，易用性在这里反而成了原罪，虽然 Evernote 本身功能限制有一定的责任，但笔记组织和材料利用更多是用户而非软件的事情，剪辑功能的缺失并不能挽救沉没的笔记。不过好在有 AHK，通过脚本也能实现相对圆满的快速剪辑功能（网页材料剪辑选择内容和网址，其他材料剪辑选择内容，详见 [使用 AHk 实现 Logseq 快速剪辑]()()（未完成））\n\n### 长文剪辑 ：Simpread\n\n目前 Logseq 长文剪辑实现最佳的是简悦的同步助手方案，可以剪辑内容及标注（md 格式），不直接放入 page 文件夹但又能在 Journals 里显示 Linked Reference。虽然配置起来比较麻烦，但相对凑合使用其他软件的配套扩展中转方案（例如 web-clipper 和 Joplin 扩展），简悦方案要强大的多。当然，对格式完全无需求也可以使用 AHK 快速剪辑脚本\n\n### RSS  剪辑\n\nInoreader 的集成剪辑功能没有很好的替代（一键收藏实在方便），为此专门增加软件也不合适，暂时只能短内容使用 AHK，长文跳转原网页使用 Simpread 了\n\n### 邮件接收\n\n作为轻度邮件用户，使用专门的邮件客户端太麻烦，可以使用滴答清单来接收汇总邮箱的转发\n\n### 大纲笔记\n\n这个功能 Evernote 没有，但这里特地提下，之前正是因为 Evernote 处理不了大纲笔记，不得不使用 Workflowy 辅助 Evernote，现在对于最核心的大纲类内容 Logseq 可以一肩挑了，意外之喜\n\n## （如何放弃）笔记导出\n\nEvernote 重度用户历史材料少不了，不少用户主张保留在 Evernote 或者导出存档，而倾向 AllinOne 的用户比如我，当然是要转换放进 Logseq 了。基础方案是使用 Joplin 将 ENEX 批量导出为 MD 文件，再用 Visual Studio Code 等软件批量处理下格式。当然导入不是重点，配合 Logseq 的 Ramdom Note 和 简单的 ahk 脚本，可以在 Logseq 中方便的随机回顾历史材料并快速处理了（详见  [Evernote 笔记批量转入 Logseq 简易指南]()（未完成）、[Logseq 简易上手指南]()）\n\n "
mytory_md_mode:
    - url
categories:
    - Articles
    - Evernote
    - smgmt
tags:
    - Evernote
    - 笔记软件
---

## 为什么放弃

特地看了下，注册 Evernote 是 2009 年，重度使用应该是 2014 年接触 GTD 和电脑玩物的《Evernote超效率数字笔记术》 之后，十年时光恍然而逝，笔记不知所云，软件也物是人非了。 尽管 Evernote 似乎仍然是市场占有率最高的笔记软件，但早已暮气沉沉，积重难返。而对我个人而言，2022年的今天仍然使用的是 2015年6月的5.8.13 版本，实在不知道是 Evernote 的巨大成功还是巨大失败。

<!--more-->

作为一款老本吃了七八年（甚至可能还能吃几年）的笔记软件，Evernote 不可谓不成功，但时移世易，笔记软件的理念越来越现代、需求也越来越复杂，这款封闭且毫无进取心的软件早已落后于时代。如果说 OneNote 算古典笔记软件、Evernote 算传统笔记软件的话，以 Roam Research 和 Obsidian 为代表的新生代已经是现代笔记软件了。特别是 Obsidian 和 Logseq 等开源软件，依托强大的基础架构和无限可能的扩展系统，基本上在易用性以外的全部场景都能花式吊打 Evernote……

## （如何放弃） 功能替代

### 快速剪辑 ：AutoHotKey 脚本

Logseq 没有原生的剪辑功能，论坛上还有很多用户反对增加剪辑功能，易用性在这里反而成了原罪，虽然 Evernote 本身功能限制有一定的责任，但笔记组织和材料利用更多是用户而非软件的事情，剪辑功能的缺失并不能挽救沉没的笔记。不过好在有 AHK，通过脚本也能实现相对圆满的快速剪辑功能（网页材料剪辑选择内容和网址，其他材料剪辑选择内容，详见 \[使用 AHk 实现 Logseq 快速剪辑\]()()（未完成））

### 长文剪辑 ：Simpread

目前 Logseq 长文剪辑实现最佳的是简悦的同步助手方案，可以剪辑内容及标注（md 格式），不直接放入 page 文件夹但又能在 Journals 里显示 Linked Reference。虽然配置起来比较麻烦，但相对凑合使用其他软件的配套扩展中转方案（例如 web-clipper 和 Joplin 扩展），简悦方案要强大的多。当然，对格式完全无需求也可以使用 AHK 快速剪辑脚本

### RSS 剪辑

Inoreader 的集成剪辑功能没有很好的替代（一键收藏实在方便），为此专门增加软件也不合适，暂时只能短内容使用 AHK，长文跳转原网页使用 Simpread 了

### 邮件接收

作为轻度邮件用户，使用专门的邮件客户端太麻烦，可以使用滴答清单来接收汇总邮箱的转发

### 大纲笔记

这个功能 Evernote 没有，但这里特地提下，之前正是因为 Evernote 处理不了大纲笔记，不得不使用 Workflowy 辅助 Evernote，现在对于最核心的大纲类内容 Logseq 可以一肩挑了，意外之喜

## （如何放弃）笔记导出

Evernote 重度用户历史材料少不了，不少用户主张保留在 Evernote 或者导出存档，而倾向 AllinOne 的用户比如我，当然是要转换放进 Logseq 了。基础方案是使用 Joplin 将 ENEX 批量导出为 MD 文件，再用 Visual Studio Code 等软件批量处理下格式。当然导入不是重点，配合 Logseq 的 Ramdom Note 和 简单的 ahk 脚本，可以在 Logseq 中方便的随机回顾历史材料并快速处理了（详见 \[Evernote 笔记批量转入 Logseq 简易指南\]()（未完成）、\[Logseq 简易上手指南\]()）