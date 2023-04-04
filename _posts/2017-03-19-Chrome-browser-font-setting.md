---
id: 431
title: 'Chrome 浏览器字体设置'
date: '2017-03-19T09:52:34+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/431'
duoshuo_thread_id:
    - '6399021757948232450'
mytory_md_visits_count:
    - '83'
mytory_md_path:
    - 'https://raw.githubusercontent.com/wandero/blog/master/17/170319Chrome%20%E6%B5%8F%E8%A7%88%E5%99%A8%E5%AD%97%E4%BD%93%E8%AE%BE%E7%BD%AE.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
mytory_md_path_old:
    - 'https://raw.githubusercontent.com/wandero/blog/master/17/170319Chrome%20%E6%B5%8F%E8%A7%88%E5%99%A8%E5%AD%97%E4%BD%93%E8%AE%BE%E7%BD%AE.md'
categories:
    - 工具二三
tags:
    - Chrome
---

（Chrome 原版已经无法使用 custom.css 来定制浏览器字体了，所以本文说的其实是 Centbrowser）

通常的 custom.css 只是为页面强制指定一组字体，例如

`*:not([class*="icon"]):not(i){font-family:"Comic sans Ms","Microsoft Yahei",sans-serif !important;}`

这样虽然能起到强制设定中英文字体的问题，但是也容易导致一些使用特殊字体的页面出现乱码和无法使用页面自定的英文字体等问题。

更好的办法是使用 CSS3 的 `@font-face` 规则针对指定 UNICODE 字符范围的字符使用指定字体映射，例如

`@font-face { font-family: '宋体';unicode-range: U+2E80-FFFF; src: local('微软雅黑')}` 即为将CJK 字符的宋体显示替换为微软雅黑显示

注意修改 Custom.css 后还需要将浏览器字体设定为微软雅黑……