---
id: 78
title: 'WordPress 自动升级问题'
date: '2013-01-30T14:46:21+08:00'
author: Zephur
layout: post
guid: 'http://foro.cloudlet.info/t/78'
duoshuo_thread_id:
    - '6275545957719343874'
mytory_md_visits_count:
    - '32'
categories:
    - 工具二三
tags:
    - WordPress
---

WordPress 自动升级时显示

```
Downloading update from http://wordpress.org/wordpress-x.x.zip

```

大多为升级超时（wget 升级包均速50k不到……）  
解决办法是修改

```
wp_remote_get($url, array('timeout' => )参数

```

或者……**选择人少的时候升级**……

另外，升级失败会在 /wp-content/ 目录中生成 xxx.tmp 临时文件