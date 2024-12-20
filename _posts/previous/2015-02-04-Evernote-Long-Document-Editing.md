---
id: 285
title: 'Evernote 长文档编辑方案'
date: '2015-02-04T16:10:16+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/285'
duoshuo_thread_id:
    - '6275546041756418817'
v2press_who_bookmarked_me:
    - 'a:1:{i:0;i:333;}'
mytory_md_visits_count:
    - '231'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/15/150204Evernote%20%E9%95%BF%E6%96%87%E6%A1%A3%E7%BC%96%E8%BE%91%E6%96%B9%E6%A1%88.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
mytory_md_path_old:
    - 'https://github.com/wandero/blog/raw/master/15/150204Evernote%20%E9%95%BF%E6%96%87%E6%A1%A3%E7%BC%96%E8%BE%91%E6%96%B9%E6%A1%88.md'
categories:
    - 工具二三
tags:
    - Evernote
    - Markdown
    - Typora
---

**UPDATE：Typora 出现后，主要使用 Typora 作为 Evernote 的编辑器，详见 [使用 Typora 作为 Evernote 主编辑器](http://cloudlet.info/t/384)**

Evernote 寒碜的排版和不支持 markdown 一直被界面控鄙视，这类问题在处理短内容笔记时还不明显，在长文档编辑的时候就很拉后腿了，经过一段时间的尝试，个人选择 **Evernote （印象笔记）+ Maxiang（马克飞象）+ Sublime\_Evnernote** 作为有排版需求的长文档编辑方案，具体按软件介绍：

<!-- more -->

## Evernote

材料的捕获、组织、整理，这些都是 Evernote 的强项，之前已经说过很多了（[Evernote 与相关软件的区别和联系](http://cloudlet.info/t/277)），这里略过

## Maxiang

Maxiang 是一款基于 Chrome 浏览器的在线/离线应用

### 应用亮点

**华丽界面**

在 Mactype 、Chrome浏览器的 custom.css 修改、Chrome 浏览器的 Opera Font Rendering by thunder13 扩展以及自身自定义设置功能（theme、css）的多重支持下，Maxiang 能够实现 Windows 下最华丽（个人经验）的 Markdown 双窗口实时预览体验 （另外因为是一款基于浏览器的应用，不满意的地方再上 Stylish 修改也很简单）

**内容目录**

这个功能很赞，实现应该也不难（基于#符号提取文章结构），但我还是第一次在 Markdown 类的编辑器中看到。

### 存在问题

（似乎是因为功能实现的原因？）Maxiang 编辑过的笔记必须使用 Maxiang 才能继续编辑。对于一般用户来说，这点问题不大，无非主打使用 Maxiang 而已，反正 Evernote 中还可以搜索这类笔记；但对于 Evernote 重度用户，这个问题对于信息中枢级别的 Evernote 操作来说几乎是致命的，不能流畅的编辑直接影响了整个信息处理的流程和流畅程度，相当于在本来就好不容易统一的容器里人为制造了一次割裂。

所以虽然就实现的界面效果而言，Maxiang 一年八十的费用也还说的过去，但编辑绑定问题却导致选择了 Maxiang 就意味着基本放弃 Evernote 绝大部分功能（见[使用 Evernote 构建桌面 GTD 系统](http://cloudlet.info/t/284)），如何取舍就要看用户的需求倾向了。

（另外不清楚什么原因，使用的时候 Maxiang 的 文档管理-从 Evernote 同步笔记列表 功能没法显示 Evernote 中笔记列表，也不知道这个功能具体实现出来是什么样子）

## SublimeEvernote

SublimeEvernote 是一款 SublimeText 的扩展包

### 应用亮点

能够在 Evernote 和 SublimeText 之间 **双向同步（支持 markdown 格式的）文档**，不同于 Maxiang 的，笔记文档可以在 Evernote 和 SublimeEvernote 之间无障碍切换。

另外得益于 SublimeText 自身的强悍，文档编辑应该更流畅？（代码盲仰望ing）

### 存在问题

受限于 SublimeText ，SublimeEvernote 无法实现双窗口实时预览 ……

## 方案

都说到这了，实现方案自动成型：

- 使用 Evernote 组织整理素材
- 使用 Maxiang 成文
- 使用 SublimeEvernote 保存代码（markdown 格式）
- （使用 SublimeEvernote ）同步至 Evernote（类 Html 格式）

（之后的文档既可以在 Evernote 中以富文本格式进行编辑，也可以在 SublimeText 中读取 Evernote 笔记后以 markdown 格式编辑）