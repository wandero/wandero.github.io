---
id: 378
title: 'Chrome 配置同步'
date: '2016-05-25T16:20:07+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/378'
permalink: /2016/05/25/chrome-%e9%85%8d%e7%bd%ae%e5%90%8c%e6%ad%a5/
duoshuo_thread_id:
    - '6288538246896960258'
mytory_md_visits_count:
    - '123'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/16/160525Chrome%20%E9%85%8D%E7%BD%AE%E5%90%8C%E6%AD%A5.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
mytory_md_path_old:
    - 'https://github.com/wandero/blog/raw/master/160525Chrome%20%E9%85%8D%E7%BD%AE%E5%90%8C%E6%AD%A5.md'
categories:
    - Notes
tags:
    - Chrome
    - sync
---

Chrome 本身通过 Google 账户进行的同步已经相当强大，仅挂 ss 的情况下也未发现任何异常，这样扩展、设置、历史记录、书签的同步就都已经解决（历史记录的同步很赞）。

此外，Tampermonkey 可以通过启用 TESLA，从而通过 Chrome Sync 同步，而剩下还有同步需求的就主要是 Stylish 了。

对于 Dropbox 用户，可以使用软链接等命令或 Dropbox Folder Sync 来同步 `\User Data\Default\databases\chrome-extension_xxx（扩展序列号）_0` 文件夹。

对于坚果云用户，因为坚果云既不支持软链接也不支持30字符以上长度的文件夹，只有同步 `\User Data\Default\databases` 文件夹，好在该文件夹体积和变化都不大。