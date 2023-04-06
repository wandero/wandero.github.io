---
id: 1159
title: 'Evernote 笔记批量转入 Logseq 简易指北'
date: '2022-07-31T20:39:12+08:00'
author: Zephur
layout: post
guid: 'https://cloudlet.info/?p=1159'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/22/220731%20Evernote%20%E7%AC%94%E8%AE%B0%E6%89%B9%E9%87%8F%E8%BD%AC%E5%85%A5%20Logseq%20%E7%AE%80%E6%98%93%E6%8C%87%E5%8C%97.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
dotGood:
    - '2'
categories:
    - 工具二三
tags:
    - Logseq
    - Evernote
---

（折腾完才发现 Yarle 可以直接将 ENEX 转换为支持 Logseq 的markdown，定制项还比较多，当然也相对复杂，推荐使用Yarle而非 本文的 Joplin 转换……）

大致上是先用 Joplin 将 ENEX 批量导出为 MD 文件，再用 Visual Studio Code 等软件批量处理下格式。之后配合 Logseq 的 Ramdom Note 和 简单的 AutoHotKey 脚本，可以在 Logseq 中方便的随机回顾历史材料并快速处理了。

<!-- more -->

## Evernote 导出前整理

Evernote 笔记中可能存在大量废弃或者不需要转入 Logseq 或者可以合并的材料。可合并可不合并的内容建议在 Evernote 中合并，例如大批量同类型短内容的笔记，Evernote 支持批量选择搜索结果并合并笔记，并且对笔记附件的管理更直接方便。  
Logseq 不支持批量选择，更不支持选择后合并，也无法在删除页面时删除页面引用的附件，涉及大数量笔记时索引耗时较久，但（安装 Random Note 插件后）支持显示随记笔记功能。

## Evernote 导出 enex 文件

（以下操作基于 Evernote 5.8.13 ，高版本如果限制了导出可尝试降低版本）  
笔记本 导出笔记 导出为 ENEX 文件格式 （左下角）选项勾选 标签 导出  
（这里也可以选择 导出为多个网页文件 之后不通过 Joplin 而是使用 Pandoc 直接转换为 markdown ）

## Joplin 转换为 md 文件

导入 ENEX Evernote 导出文件（markdown），注意不要选 HTML 文件 全部导出 MD Markdown + Frontmattle（中文翻成了文章前言，就是 Evernote 笔记的创建时间、更新时间、标签、原文链接等信息）

这里的导出不要保存到 Logseq 的库文件夹，甚至初步整理后也可以先单独建立 Logseq 临时库深度整理，完全整理好后再放入 Logseq 中的非 pages 文件夹。

（笔记多的话导入导出都需要不短时间）

## VS Code 批量替换属性标记

VS Code 批量替换比较方便（用其他软件也行），对导出的 Evernote 文件夹中的 markdown 文件进行批量替换，主要是处理 frontmatter

```
            ------
            title: 标题
            updated: 2021-12-16 12:42:39Z
            created: 2021-12-16 12:42:39Z
            source: 剪辑链接
            author: cloudlet
            tags:
            evernotetag1
            evernotetag2
            ---
```

将 `updated:`等字符串替换为 `updated::`（注意不要替换 `title:`，Evernote 部分笔记使用的自动标题，替换了会出问题）

tags: 的处理比较复杂，笔记的标签数量并不一致，熟悉正则可能可以将 tags: 段完美处理，不熟悉或者不需要的话可以只处理第一个标签比如 `#evernotetag1` （不过因为我在 Evernote 主要使用的文本标签，原生标签比较简单）

将文件中的 `../_resources/` 相对路径替换为 resources 的绝对路径（例如 `C://logseq/_resources/`）

Logseq 目前似乎没法处理其他文件夹的相对路径，更诡异的是如果是图片，需要保证路径中是 `C://logseq`才可以直接显示。而如果不是片文件（比如 doc、pdf），又需要 `C:/logseq` 才能正常（可以点击打开），还是同上，能正则用正则，不能就优先图片好了

`author: cloudlet` 替换为空

`---` 替换为空（注意 VSC 的查找和替换都支持换行符，所以这里的第二处 `---`应带换行符替换为 `-`，从而将笔记内容分条目，不分条目在搜索结果中会显示整则笔记）

## AnyTXT Searcher 批量删除废弃笔记

批量删除笔记在 Evernote 的整理阶段处理会方便一些，但导入 Logseq 后也可以通过AnyTXT Searcher 等工具实现，使用 AnyTXT 搜索关键字，对搜索结果批量选择删除即可。

## Logseq 删除空页面

删除页面后，All pages 打开 所有页面 面板，右上角按钮 选择删除空页面