---
id: 392
title: 'Tampermonkey 脚本同步'
date: '2016-08-30T10:30:18+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/392'
permalink: /2016/08/30/tampermonkey-%e8%84%9a%e6%9c%ac%e5%90%8c%e6%ad%a5/
duoshuo_thread_id:
    - '6324443359863636738'
mytory_md_visits_count:
    - '72'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/16/160830Tampermonkey%20%E8%84%9A%E6%9C%AC%E5%90%8C%E6%AD%A5.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
mytory_md_path_old:
    - 'https://github.com/wandero/blog/raw/master/160830Tampermonkey%20%E8%84%9A%E6%9C%AC%E5%90%8C%E6%AD%A5.md'
categories:
    - Notes
tags:
    - chromext
---

Tampermoneky 虽然内置了同步功能（配置模式-高级-启用 Tesla-Chrome Sync），但似乎不大好用，在 Greasyfork 上发布又比较麻烦。

折中方案推荐 Dropbox 文件共享生成（[Dropbox 共享文件外链](http://cloudlet.info/t/390)）更新 URL（复制至 Tamperonkey 脚本编辑器界面的更新 URL 表单内），这样既方便脚本修改（可以直接编辑 js 文件），又不用操心同步问题。

btw：似乎`// @version`增加才会触发更新