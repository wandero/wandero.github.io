---
id: 384
title: '使用 Typora 作为 Evernote 主编辑器'
date: '2016-06-21T20:08:50+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/384'
permalink: /2016/06/21/%e4%bd%bf%e7%94%a8-typora-%e4%bd%9c%e4%b8%ba-evernote-%e4%b8%bb%e7%bc%96%e8%be%91%e5%99%a8/
duoshuo_thread_id:
    - '6298616486080545538'
mytory_md_visits_count:
    - '1586'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/16/160621%E4%BD%BF%E7%94%A8%20Typora%20%E4%BD%9C%E4%B8%BA%20Evernote%20%E4%B8%BB%E7%BC%96%E8%BE%91%E5%99%A8.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
dotGood:
    - '6'
mytory_md_path_old:
    - 'https://github.com/wandero/blog/raw/master/160621%E4%BD%BF%E7%94%A8%20Typora%20%E4%BD%9C%E4%B8%BA%20Evernote%20%E4%B8%BB%E7%BC%96%E8%BE%91%E5%99%A8.md'
categories:
    - Evernote
tags:
    - Evernote
    - Markdown
    - typora
---

## Typora 推荐

又一款 Markdown 编辑器……以及就是这款 Markdown 编辑器

似乎从 Markdown 诞生起，双窗口就是他的固定属性，偶尔有些单窗口的应用又只是针对源代码而非显示效果的，然后融合源代码和预览效果为一个窗口的 Typora 终于出现。除了单窗口编辑浏览这种逆天功能外，其他的诸如大纲、自定义样式、表格、图片、公式、代码高亮等等功能也都不缺。

## Evernote 的编辑器

Evernote 的编辑器本来已经足够灾难了，在浩劫般的 6.0 版本后，开发者更是丧心病狂的封杀了笔记内容里的各种样式元素，所以，我们现在只提 5.8（5.9 笔记标题会丢失样式且外观诡异）。在不知道还能撑多久的 5.8 中（4.6.7 表示当前登陆正常），我们可以使用各种方式排出养眼的界面继而通过拖拽或者剪辑弄进 Evernote 里，但是这种版面非常脆弱，一个回车都可能使整篇笔记的版面崩塌。而一些使用 ahk 脚本添加样式的方法不仅复杂还可能打乱材料的结构和段落。

## Typora-Evernote 转换

至此新的长文档编辑方案（旧的在[这](http://cloudlet.info/t/285)）（以及剪辑资料美化方案）出炉，Typora 不管是新撰写还是编辑材料都可以相对顺利的复制（拖拽）至 Evernote，并且可以继续从 Evernote 复制（拖拽）回 Typora 编辑，而 Typora 的样式是可以用户自定义的。

样式问题解决了，但是这样复制粘贴看上去很繁琐？万能的 Autohotkey 大神会拯救你的（[Typora-Evernote 自动复制粘贴 AHK](http://cloudlet.info/t/389)）

## 目前存在的问题

之所以说相对顺利，这种内容转换还存在一些问题……

- 在涉及到代码块、引用等格式时，粘贴至 Evernote 的内容可能出问题（某些格式的内容复制粘贴出问题的时候可以使用拖拽的方法在两者间切换）
- 在多种分辨率环境下，笔记内容的宽度和左右留白会不好协调
- 该转换只能应用于 Evernote 5.x（win）。6.0 之后可以考虑将使用 ahk 将 Typora 内容的源码格式保存在 Evernote 中，需要的时候热键粘贴回 Typora
    
    ​