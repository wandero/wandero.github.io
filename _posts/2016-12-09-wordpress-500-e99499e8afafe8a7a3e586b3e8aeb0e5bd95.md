---
id: 411
title: 'WordPress 500 错误解决记录'
date: '2016-12-09T14:31:44+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/411'
permalink: /2016/12/09/wordpress-500-%e9%94%99%e8%af%af%e8%a7%a3%e5%86%b3%e8%ae%b0%e5%bd%95/
duoshuo_thread_id:
    - '6361985181087171329'
mytory_md_visits_count:
    - '42'
    - '42'
    - '42'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/16/161209WordPress%20500%20%E9%94%99%E8%AF%AF%E8%A7%A3%E5%86%B3%E8%AE%B0%E5%BD%95.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
mytory_md_path_old:
    - 'https://github.com/wandero/blog/raw/master/161209WordPress%20500%20%E9%94%99%E8%AF%AF%E8%A7%A3%E5%86%B3%E8%AE%B0%E5%BD%95.md'
categories:
    - Notes
tags:
    - WordPress
---

最近 WordPress 出现 500 错误，访问后台会跳转至 cloudlet.info/wp-admin/upgrade\*，页面显示站点无法正常工作。

尝试了网上的通过修改数据库清除伪静态规则和插件激活列表、清空 w3tc 缓存等方法均无效，最后用了 ftp 重命名插件文件夹（plugins）的方法搞定。