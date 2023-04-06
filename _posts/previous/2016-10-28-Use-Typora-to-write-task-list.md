---
id: 408
title: '使用 Typora 编写任务清单'
date: '2016-10-28T10:53:54+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/408'
duoshuo_thread_id:
    - '6346343470361215745'
mytory_md_visits_count:
    - '71'
    - '71'
    - '71'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/16/161028%E4%BD%BF%E7%94%A8%20Typora%20%E7%BC%96%E5%86%99%E4%BB%BB%E5%8A%A1%E6%B8%85%E5%8D%95.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
mytory_md_path_old:
    - 'https://github.com/wandero/blog/raw/master/161028%E4%BD%BF%E7%94%A8%20Typora%20%E7%BC%96%E5%86%99%E4%BB%BB%E5%8A%A1%E6%B8%85%E5%8D%95.md'
categories:
    - 工具二三
tags:
    - Typora
    - Writing
---

Typora 是一个基于 Chromium 的神奇 MarkDown 编辑器，结合 Chromium 自身的 Developer Tools 功能，可以轻松的自定义文本样式，以 [做一份任务清单](http://cloudlet.info/t/406) 中提到的冷藏大象清单为例，在 Evernote 中我们可以实现这样一份清单：

<!-- more -->

![http://i.imgbed.com/i/46/2016/10/2544.png](http://i.imgbed.com/i/46/2016/10/2544.png)

而在 Typora 中可以变成这个样子：

![http://i.imgbed.com/i/46/2016/10/2545.png](http://i.imgbed.com/i/46/2016/10/2545.png)

注意，这里的淡化不是手工实现的（Typora 不支持直接设定颜色等样式），而是通过修改 task list 样式的 CSS 来实现的，也就是说，实际上已完成任务的文本样式可以呈现为 CSS 允许实现的任意样式。

而图中效果只需要在 Typora 的当前 theme 中添加一行 `.task-list-done {opacity: 0.3 !important;}` 即可实现。

而因为 Typora 的设定，如果勾选完成父任务，对应的子任务会自动表示为完成状态（如果使用opacity，会呈现加倍的淡化效果）

综上，就单一任务清单来说，使用 Typora 编写也是一个不错的选择，但这种方法的问题是无法与 Evernote 较好的衔接，不放入 Evernote 相关的随时随地回顾和搜索编辑都很难实现，放入 Evernote 样式会无法继续保持。折中处理是将源代码格式或者 md 文件直接放入 Evernote ，但效果都很不理想……（所以其实本文只是 Typora 自定义 CSS 功能的一种展示……）