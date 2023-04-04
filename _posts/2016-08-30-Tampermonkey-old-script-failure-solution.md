---
id: 393
title: 'Tampermonkey 老脚本失效解决办法'
date: '2016-08-30T10:40:24+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/393'
permalink: /2016/08/30/tampermonkey-%e8%80%81%e8%84%9a%e6%9c%ac%e5%a4%b1%e6%95%88%e8%a7%a3%e5%86%b3%e5%8a%9e%e6%b3%95/
duoshuo_thread_id:
    - '6324445965327532801'
mytory_md_visits_count:
    - '117'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/16/160830Tampermonkey%20%E8%80%81%E8%84%9A%E6%9C%AC%E5%A4%B1%E6%95%88%E8%A7%A3%E5%86%B3%E5%8A%9E%E6%B3%95.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
mytory_md_path_old:
    - 'https://github.com/wandero/blog/raw/master/160830Tampermonkey%20%E8%80%81%E8%84%9A%E6%9C%AC%E5%A4%B1%E6%95%88%E8%A7%A3%E5%86%B3%E5%8A%9E%E6%B3%95.md'
dotGood:
    - '52'
categories:
    - Notes
tags:
    - chromext
---

因为种种超出代码盲理解的原因，Tampermonkey 的不少老脚本无法在新版本下工作（同时新脚本好像也无法在老版本下工作），解决办法很简单，同时安装两个 Tampermonkey……

新老 Tampermonkey 各跑各的适配脚本，使用了一段时间未发现异常

btw：将 Chrome 扩展文件重新打包成 crx 可以改变扩展的 ID（从而实现不同版本扩展并存）