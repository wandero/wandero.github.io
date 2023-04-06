---
id: 223
title: 'Chrome 字体图标显示乱码问题'
date: '2014-03-07T14:18:04+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/223'
duoshuo_thread_id:
    - '6275546021292409601'
mytory_md_visits_count:
    - '265'
dotGood:
    - '1'
categories:
    - 工具二三
tags:
    - Chrome
    - CSS
---

**UPDATE：**  
已有更好的处理方法见 [Chrome 浏览器字体设置](http://cloudlet.info/t/431)

<!-- more -->

- - - - - -

Chrome 通过修改 custom.css 强制页面字体后，淘宝等站点使用了字体图标的位置会显示乱码

解决方法：

修改  
`\User Data\Default\User StyleSheets\custom.css`中的强制字体代码,

如将

`* {font-family:"Comic sans Ms","Microsoft Yahei", "iconfont", "webdings", sans-serif !important;<br></br>}`

修改为

`*:not([class*="icon"]):not(i){font-family:"Comic sans Ms","Microsoft Yahei", "iconfont", "webdings", sans-serif !important;}`