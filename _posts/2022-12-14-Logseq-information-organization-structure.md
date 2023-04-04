---
id: 1213
title: 'Logseq 的信息组织结构'
date: '2022-12-14T17:46:24+08:00'
author: Zephur
layout: post
guid: 'https://cloudlet.info/?p=1213'
mytory_md_path:
    - 'https://raw.githubusercontent.com/wandero/blog/master/22/221214%20Logseq%20%E4%BF%A1%E6%81%AF%E7%BB%84%E7%BB%87%E7%BB%93%E6%9E%84.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
categories:
    - Articles
    - Notes
    - smgmt
tags:
    - Logseq
excerpt_separator: <!-- more -->
---

## 前言

信息组织结构，或者说内容组织形式，对于笔记软件的使用是极其重要的，如 [Evernote 的信息组织结构](https://cloudlet.info/t/279)（山寨了电脑玩物的 Evernote 超效率数字笔记术）、[使用 Evernote 构建桌面 GTD 系统](http://cloudlet.info/t/284)、[以 GTD 模式使用 Workflowy](https://cloudlet.info/t/992) （山寨了 David Allen 的 [Getting Things Done](https://cloudlet.info/t/282)），形式/模式变化会大幅度改变软件的使用体验和使用效率，那么，接下来就是 Logseq 的 <del>山寨</del> 组织时间了

<!-- more -->

就像 Logseq 山寨了 Roam 一样，Logseq 的使用技巧好像也大部分来自于 Roam……包括下面介绍的 Daily Notes 流，（国外不了解）国内阐释的最清晰的好像是知乎的[临时哈桑](https://www.zhihu.com/people/lin-shi-ha-sang)，[双向链接时代的快速无压记录](https://zhuanlan.zhihu.com/p/427336729)，原文很长，这里用自己的视角补充下

双链笔记几乎都配置了 Daily Notes 模块，有时会翻译为日记、日志等，这个概念很容易和日记（diary）混淆，实际上在 Daily Notes 流中，并不存在日记模式，而是将大部分笔记直接放入 Daily Notes（Logseq 中的 Journal），这样有几个好处：

## **快速**

笔记系统的主页就是每天的 Journal，打开就可以记

## **无压**

这里的无压不仅仅是录入的时候无压，（如果只是这样，Inbox 方案就能完全解决了），而且还指后期整理时候的无压（或者简单粗暴的说，没有传统意义上的位置整理了），这则笔记会一直放在最开始的位置，最多给他打打标签，使用双链笔记的块引用等功能可以方便的忽视他的实际位置把他嵌入任何需要的地方，同时还可以在任何地方方便的编辑

## **时间维度**

Daily Notes 方案（不需要额外操作）即可自动为笔记加上时间属性，加上 Logseq 强大的查询功能和标签功能，可以以多种角度清晰的看到笔记、任务、事件的联系（标签为人物时，即可切换到该人物视角；标签为事件时，即可切换到事件视角），详细的可以看看这个 [Logseq – How to Manage Projects with Examples + Intro to Tasks and Namespaces](https://www.youtube.com/watch?v=rfXADlTgYNg)（这里还提到了一种 Hierarchy 组织形式，直接建立 `to/read` 的标签或页面，这样这个页面会自动归属于 to 这个页面下，结构可以不断扩展`to/read/new`、`to/listen`，个人目前未使用）

这里提下页面和标签，在 Daily Notes 方案中可以统一视作标签（# 输入更方便），一般页面中不放内容，仅通过 Linked Rreferences 汇集 Daily Notes，且新内容会自然置顶，会清晰的呈现问题思考/发展过程。另外，页面默认是没有时间维度的，不额外处理会缺失这一重要信息

## 其他

有了 Daily Notes 方案，再配合 Logseq 原生的工作流系统（TODO、LATER、DOING、DONE、CANCELED），不使用 Query 系统都可以实现基本的任务管理和知识管理了。