---
id: 425
title: '通过 mklink 使用 Dropbox 同步任意位置文件'
date: '2017-02-24T15:42:45+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/425'
duoshuo_thread_id:
    - '6390577042055758593'
mytory_md_visits_count:
    - '82'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/17/170224%E9%80%9A%E8%BF%87%20mklink%20%E4%BD%BF%E7%94%A8%20Dropbox%20%E5%90%8C%E6%AD%A5%E4%BB%BB%E6%84%8F%E4%BD%8D%E7%BD%AE%E6%96%87%E4%BB%B6.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
mytory_md_path_old:
    - 'https://github.com/wandero/blog/raw/master/17/170224%E9%80%9A%E8%BF%87%20mklink%20%E4%BD%BF%E7%94%A8%20Dropbox%20%E5%90%8C%E6%AD%A5%E4%BB%BB%E6%84%8F%E4%BD%8D%E7%BD%AE%E6%96%87%E4%BB%B6.md'
dotGood:
    - '1'
categories:
    - 工具二三
tags:
    - Sync
---

（一般使用 Dropbox 同步任意文件夹说的比较多，但这类需求实际上坚果云可以直接通过原生功能完成，而要同步任意位置文件，坚果云就爱莫能助了）

在 Windows 7 中，通过`mklink [文件链接] [目标文件]`命令即可为指定文件建立指定位置的镜像（mklink 默认符号链接模式，不加其他参数）

而具体到 Dropbox 的使用，需要注意首先要将目标文件从原位置移动至 Dropbox 文件夹内，再反过来在原始位置建立符号链接，这样才能使 Dropbox 正常同步