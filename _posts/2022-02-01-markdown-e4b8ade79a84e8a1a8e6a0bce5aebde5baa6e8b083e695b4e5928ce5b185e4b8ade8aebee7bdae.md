---
id: 1096
title: 'Markdown 中的表格宽度调整和居中设置'
date: '2022-02-01T22:49:16+08:00'
author: Zephur
layout: post
guid: 'https://cloudlet.info/?p=1096'
permalink: /2022/02/01/markdown-%e4%b8%ad%e7%9a%84%e8%a1%a8%e6%a0%bc%e5%ae%bd%e5%ba%a6%e8%b0%83%e6%95%b4%e5%92%8c%e5%b1%85%e4%b8%ad%e8%ae%be%e7%bd%ae/
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/22/220127%20Markdown%20%E4%B8%AD%E7%9A%84%E8%A1%A8%E6%A0%BC%E5%AE%BD%E5%BA%A6%E8%B0%83%E6%95%B4%E5%92%8C%E5%B1%85%E4%B8%AD%E8%AE%BE%E7%BD%AE.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
categories:
    - Notes
tags:
    - Markdown
---

Markdown 通过各种方式转换为 html 后表格单元列宽度会无法控制（例如本 blog 使用的 Mytory for WordPress 方案

查了下资料，发现最实用的是在文本上添加 html 标签，如将 `列1标题` 修改为 `<div  style="width:60px;text-align: center">列1标题</div>`（60px可根据实际页面具体调整）

同样，Markdown 表格本身无法实现单元列标题居中而内容靠左，需要首先通过 Markdown 语法设定单元列靠左，在列标题中设置 `text-align: center`