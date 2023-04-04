---
id: 398
title: 'Photoshop 添加批量多行水印'
date: '2016-09-12T11:42:18+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/398'
duoshuo_thread_id:
    - '6329286021292753665'
mytory_md_visits_count:
    - '53'
    - '53'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/16/160912Photoshop%20%E6%B7%BB%E5%8A%A0%E6%89%B9%E9%87%8F%E5%A4%9A%E8%A1%8C%E6%B0%B4%E5%8D%B0.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
mytory_md_path_old:
    - 'https://github.com/wandero/blog/raw/master/160912Photoshop%20%E6%B7%BB%E5%8A%A0%E6%89%B9%E9%87%8F%E5%A4%9A%E8%A1%8C%E6%B0%B4%E5%8D%B0.md'
categories:
    - 工具二三
tags:
    - office
---

> （Photoshop 入门水平记录

要给一些图片加那种多行、斜排的水印，没找到什么方便的方法（网上比较多的是Word 手动复制粘贴的方法，而且水印是在最底层的，有图片会覆盖），最后发现还是 Photoshop 强悍。具体步骤:

- 准备好原始图层 图层1
- 复制图层 得到图层2
- 自由变换 Ctrl+T 将图层2进行变换（旋转、位移、缩放）
- **再次变换 Ctrl+Shift+Alt+T** 会重复上次的变换得到图层3
    
    准备好水印文字，自由变换中只进行位移，然后多次“再次变换”就有了水印列，合并复制粘贴，设好图层透明度，搞定。