---
id: 1228
title: 'DEVONthink Windows 替代方案'
date: '2022-12-16T12:13:41+08:00'
author: Zephur
layout: post
guid: 'https://cloudlet.info/?p=1228'
mytory_md_path:
    - 'https://raw.githubusercontent.com/wandero/blog/master/22/221216%20DEVONthink%20Windows%20%E6%9B%BF%E4%BB%A3%E6%96%B9%E6%A1%88.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
categories:
    - 工具二三
tags:
    - Logseq
    - DEVONthink
    - PKM
---

DEVONthink 是一款自称「专业文件知识信息管理库工具软件」、实则 Mac 专属的全流程知识库神器，集文档和信息材料的收集、储存、标注、组织、搜索、编辑等功能于一体，Windows 上几乎没有单一的平替甚至低配方案（Readwise 在某些方面算一款，但一方面主要针对的网络信息，一方面价格较高），那么，接下来，就是数量或者说价格取胜的时候了……下面按功能陈述

<!-- more -->

## 文档管理

**Zotero（组织） + Logseq（标注索引） + Anytext searcher（全文搜索）**

Zotero 配合 ZotFile（插件）坚果云可以实现文档材料的基本管理（以及云同步），提供简单的组织功能，如分类、标签、索引（聊胜于无），主要针对工作文档（非文献）

这里的亮点在于 Logseq 支持 Zotero 的标注，在 Zotero 中对 PDF 进行标注后，复制标注，在 Logseq 中选择性粘贴（Ctrl+Shift+V），即可附带 pdf 的文件链接和注记的位置链接，点击链接可以在没开启 Zotero 和相关文档的情况下直接开启 Zotero 打开文档跳转到注记位置（并且支持图片），通过标注引用操作，内化的知识管理系统（Logseq）可以和外在的知识（Zetero 等）库较为完美的衔接起来

Zotero 本身只能索引 PDF 的文字内容，且中文支持似乎够呛，为此可以使用 Anytext searcher 进行全盘全文搜索，（需要注意该软件闭源），另外 Anytext 是基于索引搜索的，生成的索引文件占用空间可能非常大。如果需要无索引即时搜索可以考虑 FileLocator Pro，但这个体验就不好说了，适合临时应急

某些时候还可以加上 Everything 文件搜索，顺便，Everything 高版本也能全文搜索，工具栏 搜索 高级搜索 文件内容中包含的单词或短语，或者直接使用语法 `c:cloudlet content:cloudlet.info` 不过效率嘛……

## 材料收集

**AHK 至 Logseq + Web Clipper 至 Webdav（坚果云）**

材料收集在 EverNote 时代根本就不是事，虽然 Evernote 养废了大量只收不看的松鼠症用户，但短文、长文、RSS、邮件的通杀实在是方便。在反复体验和比较后，个人目前选择短内容用 AHK 剪辑至 Logseq（Win+A 触发，Evernote 泪目），选择内容连带链接直接置于 Logseq 的 Jounals 中，在每日的 Logseq 整理中进一步细化，因为是 AHK，剪辑不限于网页，可以复制的地方都可以剪辑

长文要复杂一些，一方面，长文直接往 Logseq 扔很容易导致信息过载或落灰，另一方面，排版问题也比较大。权衡后选择了 Web Clipper 方案。 虽然 Web Clipper 集成了各种平台，但在现在这个地主家也没有余粮的年代（语雀点赞），建议还是使用 WebDAV 方案，直接剪辑生成 markdown 文件放到云存储（而非放到某个说不好能撑几年或者虽然活着但是不停的恶心人的具体产品上），md 文件不仅同时解决了备份和云同步问题，本身的设定也导致材料干净、易储存、易搜索、易转换，比如可以使用 AnyTxt 全文搜索、可以通过 Pandoc 批量转换为 PDF 扔 Zotero，如果对材料图片有需求（md 文件只是引用原文图片），可以自备图床，Web Clipper 支持将材料内图片上传

这里顺便说下简悦，初看上去，Simpread 在没有 DEVONthink 的 Win 平台甚至都有成为信息中枢的潜力，但是实际上，这个拥有迷宫般设置和功能的软件一般用户实在是难以驾驭，易用性基本为 0，可持续性也不高（几个月前的标注链接现在已经无法打开了），看官方教程都经常迷路，而且圆环套圆环，版本更迭造成的差异会导致教程自己都迷路，所以虽然产品的价格和服务极其良心，但使用体验实在太糟糕了，个人觉得，小补救是放弃图文教程改视频教程，但这个没法解决版本更迭带来的文档管理问题（某种程度上，这也是喜欢 AllInOne 的我转向 Web Clipper 剪辑 markdown 的一大原因） ，大补救是重构？……

## RSS

DEVONthink 的 RSS 功能本身远不如专业的 RSS 订阅服务，所以还是 Inoreader 之类就好，只是不用集成业务的话长内容还是需要跳转原文使用 Web Clipper（短内容直接 AHK 剪辑）

## 其他

DEVONthink 的词频分析、材料筛选、规则自动化之类功能似乎替代很少，不过一般用户需求也不大